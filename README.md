# Warp: Fractured Reality

<p>
  <img alt="Unity" src="https://img.shields.io/badge/Unity-6000.2.10f1-black?logo=unity">
  <img alt="Language" src="https://img.shields.io/badge/C%23-scripts-239120?logo=csharp&logoColor=white">
  <img alt="Players" src="https://img.shields.io/badge/Players-2%20local%20split--screen-purple">
  <img alt="Platform" src="https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white">
</p>

### Bend time. Break space. Escape together.

**Warp: Fractured Reality** is a 2-player split-screen co-op sci-fi runner. Two scientists are trapped inside a
collapsing warp tunnel after a teleportation experiment goes wrong. Separated into distorted Time and Space
dimensions, both players must survive the hazards and help each other clear obstacles to escape. Teamwork is the only
way out.

> This is a re-themed, modified version of the game-jam project
> [The Masked Regime](https://github.com/zubiajunaid954-bot/The-Masked-Regime). It shares the same codebase and
> core mechanics.

## Gameplay

- **Local 2-player split screen:** each player has their own camera, hearts and lane to run.
- **Survive the hazards:** barriers cost a life and pebbles rewind you a few seconds back.
- **Collect masks / warp pickups:** picking one up temporarily disables the hurdles for about **6 seconds**, which is
  how the players "stabilize reality" and clear the way.
- **Cooperation over speed:** the run is only won when **both players reach the end point**. If either player loses
  all their lives, both lose.

## Controls

| Action | Player 1 | Player 2 |
| --- | --- | --- |
| Move | Arrow keys | `W` `A` `S` `D` |
| Jump | `Right Ctrl` | `Space` |
| Sprint | `Right Shift` | `Left Shift` |
| Crouch | `Numpad 0` | `C` |

## Game flow

```
Main Menu -> LEVEL (split-screen run)
                 ├─ any player runs out of lives -> LostGame -> restart LEVEL
                 └─ both players reach the end   -> EscapeScene -> GameOver -> Main Menu / Quit
```

## Open the project in Unity

1. Install **Unity 6000.2.10f1** (Unity Hub -> Installs).
2. Clone this repository and add the folder in Unity Hub.
3. This repository contains the game's own code, scenes and settings. Third-party art, characters, audio and the Unity
   Starter Assets package are **not** redistributed here (see [Credits](#credits-and-third-party-assets)). Import them
   into `Assets/` first, then open `Assets/Scenes/MainMenu.unity`. Until then scenes will show missing references.
4. Build order: `MainMenu` -> `LEVEL` -> `LostGame` -> `EscapeScene` -> `GameOver`.

## Project structure

```
Warp-Fractured-Reality/
├── Assets/
│   ├── Scripts/                 GameManager, PlayerLives, PlayerRewind, ObstacleDamage, Pebble, LoadGameOver, LostGameUI
│   ├── DualInputManager.cs      Two-player keyboard input
│   ├── HurdlesHandler.cs        Switches the hurdles' physics layer
│   ├── PowerHandler.cs          Pickups and the timed hurdle bypass
│   ├── EndPoint.cs              Finish trigger for each player
│   ├── GameOverUI.cs            Menu / quit buttons
│   ├── Scenes/                  MainMenu, EscapeScene, GameOver
│   └── StarterAssets/.../Scenes LEVEL (the run) and LostGame
├── Packages/                    Unity package manifest
└── ProjectSettings/
```

### Main systems

| System | Script | What it does |
| --- | --- | --- |
| Two-player input | `DualInputManager` | Feeds keyboard input to two separate Starter Assets controllers |
| Lives | `PlayerLives` | Heart UI per player; zero lives ends the run for both |
| Hazards | `ObstacleDamage`, `Pebble` | Life loss, sound and a screen flash; pebbles also rewind the player |
| Rewind | `PlayerRewind` | Records recent positions and jumps back to the oldest one (`rewindTime`, 5 seconds in the level) |
| Pickups | `PowerHandler`, `HurdlesHandler` | Moves the hurdles to a pass-through layer for 6 seconds, then restores them |
| Win condition | `EndPoint`, `GameManager` | Both `Player1` and `Player2` must reach the end point |

## Built with

- **Unity 6** (6000.2.10f1), C#, **Starter Assets: Third Person Controller**, Input System, TextMesh Pro

## Status

A prototype. The white-mask pickup is a placeholder and some scripts still contain debug logging.

## Credits and third-party assets

The game uses assets made by other people. None of them are included in this repository, and each one stays under its
publisher's own license:

- Unity Starter Assets (Third Person Controller), TextMesh Pro
- Environment, effects and material packs (Abandoned World, Hovl Studio, Vefects, Stylized Stone, VolumetricLines,
  YughuesFreeMetalMaterials, Brackeys assets and others)
- Character models and animations
- Sound effects and music

If you are the publisher of one of these and would like the credit changed, please open an issue.

---

Repository maintained by [@zubiajunaid954-bot](https://github.com/zubiajunaid954-bot).
