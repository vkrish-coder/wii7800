[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
[![Actions Status](https://github.com/raz0red/wii7800/workflows/Build/badge.svg)](https://github.com/raz0red/wii7800/actions)

# Wii7800

Ported by raz0red

Wii7800 is a Nintendo Wii port of the ProSystem emulator developed by Greg Stanton. 
Additional changes developed by Ludovic Jacomme aka Zx-81 (PSP port), Leonis,
and gdement. Portions of the Pokey code were adapted from the MAME 
implementation.

[https://gstanton.github.io/ProSystem1_3/]

| ![](https://wiibrew.org/w/images/thumb/1/16/7800-pole.gif/189px-7800-pole.gif) | ![](https://wiibrew.org/w/images/thumb/a/a5/7800-commando.gif/189px-7800-commando.gif) | ![](https://wiibrew.org/w/images/thumb/d/dd/7800-ninja.gif/189px-7800-ninja.gif) |
|---|---|---|

## Current status

Wii7800 is an ongoing work in progress. For the latest project information,
please visit the [Wii7800 page](http://www.wiibrew.org/wiki/Wii7800) on WiiBrew:

[http://www.wiibrew.org/wiki/Wii7800]

## Known issues

    - High Score cartridge is only compatible with NTSC games.

## Installation

To install Wii7800, simply extract the zip file directly to your SD card 
(retain the hierarchical structure exactly).

Cartridge images must be placed in the roms directory (/wii7800/roms).
(Zip files are supported)

Wii7800 does support loading of the Atari 7800 BIOS, although it isn't 
necessary. If you wish to use the BIOS, simply place the NTSC and PAL BIOS
files in the (/wii7800) directory. The NTSC file must be named, "7800.rom",
while the PAL file must be named, "7800pal.rom". 

## Lightgun Accuracy, etc.

The crosshair for the Wii7800 emulator is not perfect. For example you may be
pointing at something and your shot may register to the right or left. This is
due to the way the 7800 handles hit detection for lightgun games. It only 
checks for a hit every 7 CPU cycles. There are 330 cycles for the visible 
portion of each frame. Thus, there are only ~47 hit points for each scanline.
So, the crosshair at best gets you in approximately the right area, and if you
miss you need to adjust based on where the shot shows up on the screen 
(exactly how you do it when there is no crosshair). 

## Cartridge/ROM Compatibility 

To find out if a particular cartridge/ROM is compatible with Wii7800, please
refer to the following page. 

[http://www.wiibrew.org/wiki/Wii7800/Cartridge_Compatbility]

Note: There are many dumps of ROMs that are incompatible with Wii7800. 
However, there is typically a dump of the cartridge that does work. 
This page contains a list of compatible ROMs by "hash code".

## Controls

    Wii7800 menu:
    -------------

        Wiimote:

            Up/Down  : Scroll
            A        : Select 
            B        : Back
            Home     : Exit to Homebrew Channel
            Power    : Power off

         Classic controller:

            Up/Down  : Scroll
            A        : Select 
            B        : Back
            Home     : Exit to Homebrew Channel
            
         Nunchuk controller:

            Up/Down  : Scroll
            C        : Select 
            Z        : Back
                  
         GameCube controller:

            Up/Down  : Scroll
            A        : Select 
            B        : Back
            Z        : Exit to Homebrew Channel
                        
    In-game (Joystick):
    ---------------------------

        Wiimote:

            D-pad          : Move
            2              : Fire 1
            1              : Fire 2
            +              : [Reset]
            -              : [Select]
            A              : Left difficulty (if enabled)
            B              : Right difficulty (if enabled)
            Home           : Display Wii7800 menu (see above)

         Classic controller:

            D-pad/Analog   : Move
            Right analog   : Dual analog (if enabled)
            A              : Fire 1
            B              : Fire 2
            +              : [Reset]
            -              : [Select]
            ZL/ZR Trigger  : [Pause]
            L Trigger      : Left difficulty (if enabled)
            R Trigger      : Right difficulty (if enabled)
            Home           : Display Wii7800 menu (see above)
            
         Nunchuk controller:

            Analog         : Move
            C              : Fire 1
            Z              : Fire 2
                  
         GameCube controller:

            D-pad/Analog   : Move
            C Analog       : Dual analog (if enabled)
            A              : Fire 1
            B              : Fire 2
            Start          : [Reset]
            L Trigger      : [Select]
            R Trigger      : [Pause]
            Y              : Left difficulty (if enabled)
            X              : Right difficulty (if enabled)
            Z              : Display Wii7800 menu (see above)
            
    In-game (Lightgun):
    ---------------------------

        Wiimote:

            Wiimote IR     : Move
            A/B            : Fire 1
            +              : [Reset]
            -              : [Select]
            1              : Left difficulty (if enabled)
            2              : Right difficulty (if enabled)
            Home           : Display Wii7800 menu (see above)
           
## Wii7800 crashes, code dumps, etc.

If you are having issues with Wii7800, please let me know about it via one of 
the following locations:

* http://www.wiibrew.org/wiki/Talk:Wii7800
* http://www.twitchasylum.com/forum/viewtopic.php?t=519

## Special thanks

* NeoRame          : Icon
* munky6           : Lead tester
* Curt Vendel      : Granting permission to use the High Score ROM
* GroovyBee        : Technical assistance
* mimo             : Testing
* Tantric/eke-eke  : Audio code example
* Tantric          : Huge improvements to the SDL
* Team Twiizers    : For enabling homebrew

## Change log

### 11/16/19 (0.4)
    - Reworked audio integration (resolves audio clipping and popping)
    - Refactored project layout. Now includes third party libraries, which
        should reduce effort to build against latest devkitPro releases
    - Updated to latest versions of devkitPPC (r34) and libogc (1.8.23)
    - Merged PR#7 by arocchi
        Fixes to make wii7800 work with latest DevKit
    - Merged PR#3 by clobber
        Fix bit shift overflow when reading cartridge size from header
    - Merged PR#2 by clobber
        Update internal ROM database
    - Merged PR#1 by clobber
        Correctly load supergame cart types

### 03/29/10 (0.3)
    - GX based scaler (smoother scrolling in Plutos, Xevious, Motor Psycho)
    - Ability to adjust screen size to any size/dimensions via the
        "Screen Size" option under "Display". If this is entered after 
        loading a cartridge, the last frame will be displayed to assist in 
        sizing.
    - Fixed graphical glitches in Ballblazer
    - Implemented RANDOM (read) and SKCTLS (write) for Pokey sound emulation
        - Ballblazer now plays all sounds
    - Minor refactor of Pokey code
    - Some minor adjustments to the Light Gun related code
    - Updated palette (from Underball)
    - Updated menu code, GX rendering of dip switches and debug information
    - Ability to set HBLANK period, Dual-analog support in ProSystem database

### 06/29/09 (0.2)
    - Lightgun support 
    - High score cartridge support
    - Increased accuracy of Maria cycle timing, games now run at close to 
        their intended speed (One on One, Tower Toppler, Summer Games, 
        KLAX, Karateka, etc.)
    - Increased compatibility for PAL games (Ballblazer, Commando, and Food 
        Fight now work)    
    - Audio now sounds as it should regardless of frequency (PAL games and 
        custom frame rates)
    - Timers now properly take into consideration cycles generated via Maria 
        and during WSYNC
    - Changes to ProSystem database format
        - Maria cycles are now enabled by default (option 0x1 now disables
            Maria, the opposite of before)
        - Ability to adjust the lightgun crosshair offset per game
    - All games now have Maria cycles and WSYNC enabled in the ProSystem 
        database (with the exception of MIA)    
    - Console switch defaults updated to work with the majority of games
    - Additions to debug output (Maria vs. CPU cycles, timer info, etc.)
    - Other games improved by various changes
        - Kung Fu Master no longer has the lines in the upper left corner of
            display and the Fuji logo appears as it should (if using BIOS)
        - Midnight Mutants has less graphical glitches
        - Summer Games has less graphical glitches
        - Plutos has slightly less graphical glitches
    - Fixed save/restore state issue for games that use RIOT timers.        
        
### 05/26/09 (0.1)
    - Snapshot support, including auto-load/auto-save
    - Optional loading of 7800 BIOS
    - Support for ProSystem emulator database
    - Detects and configures controls for one and two button 7800 games
    - Controls support for Wiimote/Nunchuk/Classic/Gamecube controllers
    - Analog controls support
    - Dual analog support for Gamecube/Classic controllers (Robotron)
    