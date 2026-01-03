# Poseidon Customs

A comprehensive vehicle customization script for FiveM using ox_lib. Perfect for police departments, mechanics, and general vehicle customization.

## 📋 Overview

Poseidon Customs is a feature-rich vehicle modification script that allows players to customize their vehicles with performance upgrades, cosmetic parts, colors, and more. The script features customizable zones, job restrictions, free mods for specific jobs, and an intuitive menu system.

## ✨ Features

- **Performance Upgrades**: Engine, brakes, transmission, suspension, and turbo modifications
- **Cosmetic Parts**: Extensive customization options including bumpers, spoilers, hoods, wheels, and more
- **Paint System**: Classic, Matte, Metal, Worn, and Chameleon paint options with pearlescent support
- **Neon Lights**: Customizable neon lights with multiple color options
- **Window Tinting**: Various window tint levels
- **Plate Customization**: Multiple license plate styles
- **Xenon Lights**: Color-customizable headlights
- **Extras System**: Toggle vehicle extras when available
- **Repair System**: Vehicle repair functionality with dynamic pricing
- **Job Restrictions**: Configure zones with job-based access control
- **Free Mods/Repairs**: Grant free modifications and repairs to specific jobs (e.g., police, mechanics)
- **Admin Menu**: Admin command to access customization menu from anywhere
- **Drag Camera**: Smooth camera system for viewing vehicle modifications
- **Zone System**: Polyzone-based customization areas with optional map blips

## 📦 Dependencies

- **QB-Core** or **QBox** - Framework integration
- **ox_lib** - Menu and UI system
- **oxmysql** - Database integration

## 🚀 Installation

1. Ensure you have all dependencies installed and running
2. Place the `poseidon-customs` folder in your `resources` directory
3. Add `ensure poseidon-customs` to your `server.cfg`
4. Configure the script in `config.lua` (see Configuration section)
5. Restart your server

## ⚙️ Configuration

### Zones

Edit `config.lua` to configure customization zones. Each zone can have:
- **points**: Array of vec3 coordinates defining the zone boundaries
- **job**: Restrict access to specific jobs (optional)
- **freeRepair**: Jobs that get free repairs (optional)
- **freeMods**: Jobs that get free modifications (optional)
- **blipLabel**: Custom label for map blip (optional)
- **blipColor**: Blip color ID (optional)
- **hideBlip**: Hide the blip on the map (optional)

**Important**: Ensure all Z values in zone points match to avoid zone detection issues.

```lua
Config.Zones = {
    {
        freeRepair = { 'police', 'sheriff' },
        freeMods = { 'police', 'sheriff' },
        job = { 'police', 'sheriff' },
        points = {
            vec3(401.53, -971.76, 23.33),
            vec3(401.46, -999.84, 23.33),
            vec3(417.19, -999.52, 23.33),
            vec3(416.88, -971.60, 23.34),
        }
    },
}
```

### Prices

Configure pricing in `config.lua`:
- **cosmetic**: Price for cosmetic modifications
- **colors**: Price for color changes
- **Performance mods**: Individual arrays for each upgrade level

```lua
Config.Prices = {
    ['cosmetic'] = 500,
    ['colors'] = 1000,
    [11] = { 0, 10, 20, 30, 40 },     -- Engine
    [12] = { 0, 25, 50, 75 },         -- Brakes
    [13] = { 0, 50, 10, 15, 20 },     -- Transmission
    [15] = { 0, 30, 60, 90, 120, 150 }, -- Suspension
    [18] = 100                        -- Turbo
}
```

### Blips

To enable map blips, edit `client/zones.lua` and uncomment the blip creation section (lines 73-83).

### Currency

Change the currency symbol in `config.lua`:
```lua
Config.Currency = '$'
```

## 🎮 Usage

1. Drive your vehicle into a configured customization zone
2. Press **[E]** to open the customization menu
3. Navigate through the categories:
   - **Performance**: Engine, brakes, transmission, suspension, turbo
   - **Cosmetics - Parts**: Bumpers, spoilers, wheels, interior, etc.
   - **Cosmetics - Colors**: Paint, neon, window tint, xenon lights
   - **Extras**: Toggle vehicle extras (if available)
4. Select modifications and confirm changes
5. Vehicle properties are automatically saved to the database

### Admin Menu

Admins with the `customs.admin` ACE permission can use:
```
/admincustoms
```
This opens the customization menu from anywhere (vehicle required).

## 🔧 Available Modifications

### Performance
- Engine upgrades (4 levels)
- Brake upgrades (3 levels)
- Transmission upgrades (4 levels)
- Suspension upgrades (5 levels)
- Turbo upgrade
- Armor upgrade (configurable)

### Parts
- Spoiler, Front/Rear Bumpers, Side Skirts
- Exhaust, Grille, Hood
- Left/Right Fenders, Roof
- Wheels (Sport, Muscle, Lowrider, SUV, Offroad, Tuner, Hiend, Street, Track, etc.)
- Horns (57+ options)
- Interior modifications (Dashboard, Dial, Seats, Steering Wheel, etc.)
- License plate holders and vanity plates

### Colors & Visual
- **Paint Types**: Classic, Matte, Metal, Worn, Chameleon
- **Pearlescent**: Applied over base paint colors
- **Neon**: Left, Right, Front, Back positions with 12 color options
- **Window Tint**: 6 levels from None to Pure Black
- **Xenon Lights**: 13 color options
- **Tyre Smoke**: 10 color options
- **Plate Styles**: Multiple license plate designs

## 📝 Notes

- Vehicle modifications are saved to the `player_vehicles` table in your database
- The script requires players to be inside a vehicle to use the customization menu
- Payment is processed automatically (cash first, then bank)
- Free repairs/modifications apply based on job configuration
- Zones use polyzones for accurate detection
- Drag camera provides smooth vehicle viewing during customization

## 🛠️ Support

Developed by **Poseidon Developments**

- Discord: [Join our Discord](https://discord.gg/3w8bdfZusD)

## 📄 License

This script is provided as-is. Please refer to your purchase/license agreement for usage terms.

## 🔄 Version

Current Version: **1.0.0**

---

**Note**: Make sure your server build supports the GEN9 vehicle color system (carcols_gen9.meta and carmodcols_gen9.meta) for full color functionality.
