# Project Phantom

<img width="1535" height="862" alt="image" src="https://github.com/user-attachments/assets/672178ab-dae0-4812-8042-dcfe77bb9bc8" />


A futuristic first-person stealth shooter in plain HTML5, CSS3 and vanilla JavaScript (ES modules). 3D via Three.js r128 loaded from the cdnjs CDN. No build step, no backend.

## Run

```bash
python3 -m http.server 8080   # from the repository root
# open http://localhost:8080/
```

**Internet required:** Three.js (cdnjs) and the Rajdhani / Share Tech Mono fonts (Google Fonts, optional) are loaded from CDNs. Without Three.js the game shows an error screen. It deploys as a static site (GitHub Pages / Netlify / Vercel). Add `?nolock` to the URL to play without Pointer Lock (debug).

## Controls

| Key | Action | Key | Action |
|---|---|---|---|
| W A S D | Move | Mouse / LMB / RMB | Look / fire / aim |
| Shift | Sprint | Ctrl or C | Crouch (quieter, harder to see) |
| Space | Jump | R | Reload |
| E | Interact (hold to hack), silent takedown from behind | Q | EMP pulse (disables drones, cameras, turrets) |
| 1-4 / Wheel | Weapons | Tab | Objectives |
| Esc | Pause | | |

## Features

- 3 missions (Blacksite Breach, Neon District, Orbital Silence), each with its own procedurally built level, theme, enemies, objectives, optional bonuses and extraction.
- Enemies: Patrol Guard, Heavy Trooper (armour, cover cycling), Scout Drone (movement sensor, EMP-able), Elite Hunter (flanking, long searches), Sentry Turret, Security Camera.
- Stealth AI: PATROL > SUSPICIOUS > INVESTIGATE > ALERT > SEARCH > PATROL. Raycast line of sight, vision cones (visible on the floor), distance + wall-attenuated hearing, suspicion meters, last-known position, body discovery, alarms, A* pathfinding through doors.
- 5 weapons (Spectre-9, Vortex AR, Reaper SMG, Longshot, Arc Caster) with distinct stats, recoil, spread, sounds, ADS and viewmodels; headshot multipliers; hitscan with real obstruction checks.
- Progression: XP, credits, rank per mission, weapon purchases/unlocks, 3-level upgrades, statistics, settings, all in LocalStorage with validation.
- Fully procedural audio (Web Audio) and procedural textures/models.
- Graphics quality (low/medium/high shadows), instanced meshes, pooled particles, WebGL context-loss handling.

## Known limitations

- Desktop only (keyboard + mouse); no touch or gamepad.
- Enemies are simple procedural humanoids; no animation beyond walk/aim/fall.
- Shadows only on High. Quality changes to shadows apply on the next mission load.
- Tested in headless Chromium (software GL); real-GPU performance was not benchmarked.
- Balance (damage, detection, economy) is untuned beyond a few playthrough checks.

## Comparison build

`comparison/gemini/index.html` is an independent build of the same "Project Phantom" brief, supplied for side-by-side comparison (reported to be made by Gemini; not written by this project, included unmodified). Open `/comparison/gemini/index.html`, or `/compare.html` for a side-by-side page with launch links and a feature table.

| | This build | Comparison build |
|---|---|---|
| Structure | `index.html`, `style.css`, `game.js` + 9 ES modules | single HTML file |
| Size | about 4,000 lines of JS and CSS in 13 files | 5,275 lines, 168 KB |
| Three.js | r128 from cdnjs | r128 from cdnjs, with an offline shim fallback |

Both load and start in headless Chromium without console errors (checked once, menu to mission start only; the comparison build was not played further). No gameplay or quality ranking is claimed here.
