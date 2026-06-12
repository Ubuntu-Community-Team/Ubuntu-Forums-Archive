---
title: "Bigfish games permission error"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Desktop_n00b on 2009-07-25
When I try to use wine to install any game from bigfish games it says I do not have permission to install.
So I searched google, and I have read forum after forum after forum and everything I get tells me to go to this

[http://bugs.winehq.org/show_bug.cgi?id=15755](http://bugs.winehq.org/show_bug.cgi?id=15755)

then it tells me to read this

[http://wiki.winehq.org/Patching](http://wiki.winehq.org/Patching)

but I can't make sense out of any of that. I am sorry for making another one of these posts but I need a super dumbed down explanation for extream ubuntu/wine n00bs of what I am supposed to do.

I've had ubuntu about a week and I decided to build a PC for my fiancé, but the only games she plays are these bigfish ones. If I download the games off torrent they work, but she freaks out on me and says that its illegal to download stuff off torrents. From my experiments I have found that the only thing that seems to be having the problem in wine is the software that limits your time to 60 mins until you pay for the game. So I have spent hours trying to figure out this code stuff. I am so frustrated that I have a splitting headache. Can anyone help me?

---

### Post by BslBryan on 2009-07-25
Hey, Desktop_n00b. :-)

First, you have to uninstall wine via the terminal by typing  
```
sudo apt-get --purge remove wine
```

Then, open up your terminal and type (or copy/paste) ```
gksudo gedit /etc/apt/sources.list
```

Then, scroll to the bottom, and paste this line. ```
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
``` 
Then save the file, and close gedit.  

Then, in your terminal, type ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Then, type ```
sudo apt-get update
```

Then, ```
sudo apt-get install wine
```

Now, open up your favorite text editor and paste in these contents.
```
 dlls/advapi32/security.c |    6 +++---
 1 files changed, 3 insertions(+), 3 deletions(-)

diff --git a/dlls/advapi32/security.c b/dlls/advapi32/security.c
index 8229377..4f154a7 100644
--- a/dlls/advapi32/security.c
+++ b/dlls/advapi32/security.c
@@ -616,10 +616,10 @@ BOOL WINAPI
 CheckTokenMembership( HANDLE TokenHandle, PSID SidToCheck,
                       PBOOL IsMember )
 {
-  FIXME("(%p %p %p) stub!\n", TokenHandle, SidToCheck, IsMember);
+  FIXME("(%p %s %p) stub!\n", TokenHandle, debugstr_sid(SidToCheck), IsMember);
 
-  *IsMember = TRUE;
-  return(TRUE);
+  *IsMember = FALSE;
+  return TRUE;
 }
 
 /******************************************************************************
-- 
1.5.4.3


``` 

Save this as patch.diff and follow the complete instructions on [http://wiki.winehq.org/Patching](http://wiki.winehq.org/Patching).  

Note: You may have to change the instructions a little bit to fit your needs (change filenames, move the patch you created into some other folder, etc.)

Hope I've helped!

---

### Post by llamabr on 2009-07-25
Wine is very rarely the correct answer.  Have you searched for native games?  Most of those on that site can be played online, completely, and they'll work.

As you can see, it's a bit complicated to set up wine, and it usually won't work very well.  You can also try these, and others:

```
apt-cache search game
atomix - puzzle game for building molecules out of isolated atoms
edubuntu-addon-young - Edubuntu add-on packages for young children
gcompris - Educational games for small children
gcompris-data - Data files for GCompris
gcompris-sound-ar - Arabic (Tunisia) sound files for GCompris
gcompris-sound-bg - Bulgarian sound files for GCompris
gcompris-sound-br - Breton sound files for GCompris
gcompris-sound-cs - Czech sound files for GCompris
gcompris-sound-da - Danish sound files for GCompris
gcompris-sound-de - German sound files for GCompris
gcompris-sound-el - Greek sound files for GCompris
gcompris-sound-en - English sound files for GCompris
gcompris-sound-es - Spanish sound files for GCompris
gcompris-sound-eu - Basque sound files for GCompris
gcompris-sound-fi - Finnish sound files for GCompris
gcompris-sound-fr - French sound files for GCompris
gcompris-sound-hi - Indian Hindi sound files for GCompris
gcompris-sound-hu - Hungarian sound files for GCompris
gcompris-sound-id - Indonesian sound files for GCompris
gcompris-sound-it - Italian sound files for GCompris
gcompris-sound-mr - Indian Marathi sound files for GCompris
gcompris-sound-nb - Norwegian (Bokmal) sound files for GCompris
gcompris-sound-nl - Dutch sound files for GCompris
gcompris-sound-pt - Portuguese sound files for GCompris
gcompris-sound-ptbr - Portuguese sound files for GCompris
gcompris-sound-ru - Russian sound files for GCompris
gcompris-sound-so - Somali sound files for GCompris
gcompris-sound-sr - Serbian sound files for GCompris
gcompris-sound-sv - Swedish sound files for GCompris
gcompris-sound-tr - Turkish sound files for GCompris
gcompris-sound-ur - Urdu sound files for GCompris
ggzcore-bin - GGZ Gaming Zone: various command-line helper programs
italc-client - Intelligent Teaching and Learning with Computers
italc-master - Intelligent Teaching and Learning with Computers
libeigen-dev - lightweight C++ template library for linear algebra
libggz-gtk-dev - GGZ Gaming Zone: core client embedding library for GTK+ - development files
libggz-gtk1 - GGZ Gaming Zone: core client embedding library for GTK+
libggzcore-dev - GGZ Gaming Zone: core client frontend library - development files
libggzcore9 - GGZ Gaming Zone: core client frontend library
libggzdmod++-dev - GGZ Gaming Zone: game backend class library - development files
libggzdmod++1 - GGZ Gaming Zone: game backend class library
libggzdmod-dev - GGZ Gaming Zone: game backend library - development files
libggzdmod6 - GGZ Gaming Zone: game backend library
libggzmod-dev - GGZ Gaming Zone: game frontend library - development files
libggzmod4 - GGZ Gaming Zone: game frontend library
libitalc - Intelligent Teaching and Learning with Computers
libopenbabel-dev - Convert and manipulate chemical data files (development version)
libopenbabel3 - Convert and manipulate chemical data files
libxxf86dga-dev - X11 Direct Graphics Access extension library (development headers)
libxxf86dga1 - X11 Direct Graphics Access extension library
libxxf86dga1-dbg - X11 Direct Graphics Access extension library (debug package)
tuxmath - math game for kids with Tux
tuxtype - Educational Typing Tutor Game Starring Tux
tuxtype-data - Data files for the Educational Typing Tutor Game Starring Tux
xscreensaver-gl - GL(Mesa) screen hacks for xscreensaver
3dchess - 3D chess for X11
a7xpg - chase action game
a7xpg-data - chase action game - game data
abe - Side-scrolling game named "Abe's Amazing Adventure"
abe-data - Side-scrolling game named "Abe's Amazing Adventure"
abuse - SDL port of the Abuse action game
abuse-frabs - levels and graphics for Abuse
abuse-lib - original levels for Abuse
ace-of-penguins - Solitaire-games with penguin-look
adanaxisgpl - Action game in four spatial dimensions
adanaxisgpl-data - Action game in four spatial dimensions
adonthell - A 2D graphical roleplaying game
adonthell-data - Data files needed by Adonthell
airstrike - 2d dogfight game in the tradition of 'Biplanes' and 'BIP'
airstrike-common - 2d dogfight game in the tradition of 'Biplanes' and 'BIP'
alex4 - Alex the Allegator 4 - a retro platform game
alex4-data - Alex the Allegator 4 - game data
alienblaster-data - Game data for Alien Blaster
allegro-demo - cool game, demonstrating power of the Allegro library
allegro-demo-data - graphics and audio data for allegro-demo
amphetamine - jump'n run game with unique visual effects
amphetamine-data - data files for the game "Amphetamine"
anagramarama - fast paced anagram puzzle game using SDL
anagramarama-data - fast paced anagram puzzle game using SDL (data files)
angband-doc - Documentation for the roguelike game Angband.
angrydd - Angry Drunken Dwarves - falling blocks puzzle game
antigravitaattori - Multiplayer flying saucer racing game
arkhart - former world for Arkrpg
arkrpg - roleplaying kernel
armagetronad - 3D Tron-like high speed game
armagetronad-common - Common files for the Armagetron Advanced packages
armagetronad-dedicated - dedicated game server for Armagetron Advanced
asc - turn-based strategy game
asc-data - data files for the Advanced Strategic Command game
asc-music - music pack for ASC
asciijump - Small and funny ASCII-art game about ski jumping
atanks - tank-battling game
atanks-data - data files for Atomic tanks
atom4 - An original two-player color puzzle game
atris - tetris-like game with a twist for Unix
attal - turn-based strategy game
attal-themes-cyberpunk - cyberpunk theme for attal
attal-themes-medieval - medieval theme for attal
balazar - adventure/action game Balazar -- Arkanae II, reforged scepters
balazarbrothers - 3D puzzle game
barrage - Rather violent action game
battleball - soccer game played with tanks or helicopters
beneath-a-steel-sky - a science fiction adventure game
berusky - Logic game based on Sokoban
berusky-data - Data files for Berusky
billard-gl - 3D billiards game
billard-gl-data - 3D billards game - data files
biloba - turn based strategy board game for up to 4 players
biloba-data - turn based strategy board game for up to 4 players
biniax2 - logic game with arcade and tactics modes
biniax2-data - logic game with arcade and tactics modes - game data
bloboats - a boat racing game
blobwars - A platform shooting game
blobwars-data - A platform shooting game
blockattack - a puzzle game inspired by Tetris
bnetd - Gaming server that emulates Battle.net(R)
bombardier - The GNU Bombing utility
bomberclone - free Bomberman clone
bomberclone-data - Data files for bomberclone game
bombermaze - A bomberman clone for GNOME, for 2-4 players
boswars - futuristic real-time strategy game
boswars-data - Images, data, and music files for Bos Wars
bouncy - eat the yummy veggies in the garden - game for small kids
briquolo-data - Fast paced 3d Breakout data files
bsdgames - a collection of classic textual unix games
btanks - fast 2D tank arcade game with multiplayer and split-screen modes
btanks-data - game data for Battle Tanks
bubbros - multiplayer clone of the famous Bubble Bobble game
bugsquish - Bugs are trying to suck blood out of your arm!
bumprace - 1 or 2 players race through a multi-level maze
burgerspace - Avoid evil foodstuffs and make burgers
bygfoot - soccer (football) manager game featuring the most important European leagues
bzflag - a 3D first person tank battle game
bzflag-server - bzfs - BZFlag game server
castle-combat - game where the player builds one castle and destroys others
ceferino - action game similar to Super Pang
ceferino-data - action game similar to Super Pang
cgoban - complete Go board
childsplay - Suite of educational games for young children
childsplay-alphabet-sounds-ca - Catalan sounds for childsplay's alphabet game
childsplay-alphabet-sounds-de - German sounds for childsplay's alphabet game
childsplay-alphabet-sounds-es - Spanish sounds for childsplay's alphabet game
childsplay-alphabet-sounds-fr - French sounds for childsplay's alphabet game
childsplay-alphabet-sounds-it - Italian sounds for childsplay's alphabet game
childsplay-alphabet-sounds-nl - Dutch sounds for childsplay's alphabet game
childsplay-alphabet-sounds-pt - Portuguese sounds for childsplay's alphabet game
childsplay-alphabet-sounds-ru - Russian sounds for childsplay's alphabet game
childsplay-alphabet-sounds-sv - Swedish sounds for childsplay's alphabet game
childsplay-lfc-names-ca - Catalan files for the Letter Flash Cards game
childsplay-lfc-names-fr - French files for the Letter Flash Cards game
childsplay-lfc-names-nl - Dutch files for the Letter Flash Cards game
childsplay-plugins - Additional games for childsplay
childsplay-plugins-lfc - letterFlashscard game for childsplay
chromium - fast paced, arcade-style, scrolling space shooter
circuslinux - The clowns are trying to pop balloons to score points!
circuslinux-data - data files for circuslinux
ciso - Tool to convert Sony PSP iso to ciso
cl-reversi - Reversi game for Common Lisp
cl-sdl - Common Lisp bindings to the SDL graphics library
clanlib-doc - Reference documentation and tutorials for ClanLib
codeblocks-contrib - Contrib plugins for Code::Blocks IDE
codebreaker - A Master Mind clone using GTK
conquest - a real-time, multi-player space warfare game (curses client)
conquest-data - a real-time, multi-player space warfare game (data)
conquest-gl - a real-time, multi-player space warfare game (OpenGL client)
conquest-libs - a real-time, multi-player space warfare game (libs)
conquest-server - a real-time, multi-player space warfare game (server)
console-freecell - console version of freecell game
corewars - The classic corewars game with gtk-look.
cpushare - client and server for the CPUShare distributed computing platform
crack-attack - multiplayer OpenGL puzzle game like "Tetris Attack"
crawl - Dungeon Crawl, a text-based roguelike game
crimson - A hex-based tactical game
crossfire-client - Sound server for the game Crossfire
crossfire-client-gtk - GTK+ Client of the game Crossfire
crossfire-client-gtk2 - GTK+ 2 Client of the game Crossfire
crossfire-client-sounds - sound files for playing crossfire
crossfire-client-x11 - XLib Client of the game Crossfire
crossfire-common - Common files for Crossfire
crossfire-edit - Map editor for the Crossfire Gameset
crossfire-server - Server for Crossfire Games
crystalspace - Multiplatform 3D Game Development Kit
crystalspace-data - Multiplatform 3D Game SDK datas and menus for Demos
crystalspace-dev - Multiplatform 3D Game Development Kit dev files
crystalspace-doc - Multiplatform 3D Game Development Kit Documentation
csmash - CannonSmash, a table tennis simulation game
csmash-data - data files for the CannonSmash game
csmash-demosong - Demo song for CannonSmash
ctorrent - BitTorrent Client written in C++
cultivation - game about the interactions within a gardening community
cuyo - Tetris-like game with very impressive effects
cuyo-data - data files for the game cuyo
cyphesis-cpp - WorldForge game server
cyphesis-cpp-clients - WorldForge game server - clients to control the server
cyphesis-cpp-mason - WorldForge game server - game data for Mason
dangen - shoot 'em up game where accurate shooting matters
dealer - bridge hand generator
defendguin - defender clone with penguins
defendguin-data - Data files for defendguin
desmume - Nintendo DS emulator
dodgindiamond2 - Little shoot-'em-up arcade game for one or two players
donkey-bolonkey - Game where you rescue donkeys
dopewars - Make a fortune dealing drugs on the streets of New York
dopewars-data - Make a fortune dealing drugs on the streets of New York
dosbox - A x86 emulator with Tandy/Herc/CGA/EGA/VGA/SVGA graphics, sound and DOS
dossizola - An Isola board game with nice graphics
dossizola-data - Data files for Do'SSi Zo'la game
dreamchess - a 3D chess game
dreamchess-data - a 3D chess game
droidbattles - A game of programming battle droids
education-logic-games - DebianEdu logic games
efp - Escape from Pong NES game
egoboo - 3D dungeon crawling adventure in the spirit of NetHack
egoboo-data - Egoboo data files
einstein - Puzzle game inspired on Einstein's puzzle
empire - the war game of the century
enemylines3 - semi-abstract first person 3d-shooter game
enemylines7 - first person 3d-shooter game
enigma - A game where you control a marble with the mouse
enigma-data - Data file for the game enigma
enigma-doc - Documentation for the game enigma
enigma-level-previews - Pregenerated level previews for Enigma
epiphany - clone of Boulder Dash game
epiphany-data - required maps for epiphany game
etw - arcade-style soccer game
etw-data - graphics and audio data for etw
extremetuxracer - 3D racing game featuring Tux, the Linux penguin
extremetuxracer-data - data files for the game PlanetPenguin Racer
extremetuxracer-dbg - 3D racing game featuring Tux, the Linux penguin (debugging symbols)
fb-music-high - High quality, large music files for Frozen-Bubble
fb-music-low - Lower quality, small music files for Frozen-Bubble
fceu - FCE Ultra - a nintendo (8-bit) emulator
fceu-server - Server for the FCE Ultra NES emulator
fenix - development environment for making 2D games
fenix-dev - development environment for making 2D games
fenix-plugin-mpeg - mpeg plugin for the Fenix Game Development System
fenix-plugins - plugins for the Fenix Game Development System
fenix-plugins-system - plugins for the Fenix Game Development System
filler - simple game where two players try to capture half the board
fillets-ng - puzzle game about witty fish saving the world sokoban-style
fillets-ng-data - docs, graphics, music and international sounds for fillets-ng
fillets-ng-data-cs - add-on sounds for czech language spoken dialogs for fillets-ng
fkiss - Implementation of KISekae Set System (KISS) for the X Window System
flight-of-the-amazon-queen - a fantasy adventure game
flobopuyo - Clone of the PuyoPuyo game
fltk1.1-games - Fast Light Toolkit - example games: checkers, sudoku
flying - pool/snooker/carrom/hockey/curling simulator for X11
foobillard - a 3D billiards game using OpenGL
freealchemist - simpler figure block game
freecell-solver-bin - Library for solving Freecell games
freeciv-client-gtk - Civilization turn based strategy game (GTK+ client)
freeciv-client-sdl - Civilization turn based strategy game (SDL client)
freeciv-client-xaw3d - Civilization turn based strategy game (Xaw3D client)
freeciv-data - Civilization turn based strategy game (game data)
freeciv-server - Civilization turn based strategy game (server files)
freeciv-sound-standard - Civilization turn based strategy game (standard sound pack)
freecol - an open version of Colonization
freedoom - free game files for the 3D game DOOM
freedroid-data - Data files for freedroid - a strategic shoot-em up
freedroidrpg - An isometric RPG influenced by Paradroid
freedroidrpg-data - Data files for freedroidrpg
freesci - a portable interpreter for SCI games like Space Quest 3
freesci-doc - Documentation for FreeSCI
freesweep - a text-based minesweeper
freetennis - Free Tennis - simulation game
freetennis-common - Free Tennis - simulation game
freevial - trivia platform for community events
fretsonfire - game of musical skill and fast fingers
fretsonfire-game - game of musical skill and fast fingers - Game files
fretsonfire-songs-sectoid - game of musical skill and fast fingers - Songs Package
frotz - interpreter of Z-code story-files
frozen-bubble - Pop out the bubbles!
frozen-bubble-data - Data files for Frozen-Bubble
fruit - chess engine, to calculate chess moves
fteqcc - FTE QuakeC compiler
funnyboat - a side scrolling arcade shooter game on a steamboat
gabedit - graphical user interface to Ab Initio packages
gamazons - Amazons boardgame for Gnome
gambit - Game theory analysis software and tools
gambit-doc - documentation for gambit
games-thumbnails - thumbnails of games in Debian
gamine - an interactive game for young children
gamine-data - data files for gamine game
gausssum - parse and display Gaussian, GAMESS, and etc's output
gav - GPL Arcade Volleyball
gbatnav - networked BattleShip game
gbrainy - brain teaser game and trainer to have fun and to keep your brain trained
gbsplay - A Gameboy sound player
gearhead - roguelike mecha role playing game
gearhead-data - data files for gearhead
geki2 - Xenon-like vertical shoot'em-up
geki3 - R-Type-like horizontal shoot'em-up
gemdropx - Gem Drop X is an interesting one-player puzzle game for X11
ggz - GGZ Gaming Zone: the complete GGZ environment for gamers
ggz-docs - GGZ Gaming Zone: documentation
ggz-game-servers - GGZ Gaming Zone: game servers collection
ggz-gnome-client - GGZ Gaming Zone: core client for the GNOME desktop
ggz-grubby - GGZ Gaming Zone: chat bot with the ability to play games
ggz-gtk-client - GGZ Gaming Zone: advanced core client for GTK+ environments
ggz-gtk-games - GGZ Gaming Zone: game clients collection for GTK+
ggz-gtk-games-data - GGZ Gaming Zone: multimedia data for game clients for GTK+
ggz-kde-client - GGZ Gaming Zone: advanced core client for KDE
ggz-kde-games - GGZ Gaming Zone: game clients collection for KDE
ggz-kde-games-data - GGZ Gaming Zone: game clients collection for KDE
ggz-sdl-games - GGZ Gaming Zone: game clients collection for SDL
ggz-sdl-games-data - GGZ Gaming Zone: game clients collection for SDL
ggz-txt-client - GGZ Gaming Zone: client for the command line
ggzd - GGZ Gaming Zone: main server
ghex - GNOME Hex editor for files
ghextris - A Tetris-like game on a hexagonal grid
gimp-dds - DDS (DirectDraw Surface) plugin for the gimp
glbsp - nodes builder for Doom-style games; has support for OpenGL
glob2 - innovative state-of-the-art Real Time Strategy (RTS) game
glob2-data - dataset for Globulation2 (glob2)
glotski - Slide blocks to reach a goal
glpuzzle - Photo puzzle game for children
gltron - 3D lightcycle game
gmult - figure out which letters are which numbers
gngb - a Color Gameboy emulator
gnome-breakout - Clone of the classic game Breakout, written for GNOME
gnome-games-extra-data - games for the GNOME desktop (extra artwork)
gnome-hearts - The classic hearts card game for the GNOME desktop
gnome-mastermind - Mastermind (TM) clone for GNOME Desktop
gnubg - graphical or console backgammon program with analysis
gnubg-data - data files for GNU Backgammon
gnubik - 3D Rubik's cube game
gnuchess - Plays a game of chess, either against the user or against itself
gnugo - play the game of Go
gnujump - a platform game where you have to jump up to survive
gnujump-data - a platform game where you have to jump up to survive - data files
gnurobbo - logic game ported from ATARI XE/XL
gnurobots - Program a robot to explore a world
gnushogi - A program to play shogi, the Japanese version of chess
gnustep-games - The GNUstep Development Environment -- games
golly - Game of Life simulator using hashlife algorithm
gomoku.app - Extended TicTacToe game for GNUstep
goplay - games (and more) package browser using DebTags
gpe - The G Palmtop Environment (GPE) metapackage
gpe-go - two player board game for GPE
gpe-lights - Lights Out game clone for GPE
gpe-othello - othello board game for GPE
gpe-tetris - tetris game for small screens and embedded devices
gplanarity - simple puzzle game involving untangling planar graphs
grande - vertical shoot'em-up in the spirit of Xevious
gravitation - game about mania, melancholia, and the creative process
gravitywars - clone of Gravity Force
greed - curses-based clone of the DOS freeware game Greed
grhino - Othello/Reversi boardgame
gridlock.app - A collection of grid-based board games for GNUstep
groundhog - A simple logic game
grub-invaders - multiboot compliant kernel game
gsoko - sokoban game for GPE
gtans - Tangram (puzzle) game using GTK+
gtetrinet - multiplayer tetris-like game
gtkatlantic - Game like Monopoly
gtkballs - A simple logic game
gtkboard - many board games in one program
gtkgo - Skinnable version of the game "Go"
gtkpool - simple pool billiard game written with GTK+
gunroar - 360-degree gunboat shooter
gunroar-data - 360-degree gunboat shooter - game data
gweled - A "Diamond Mine" puzzle game
hannah - pacman-like game, child oriented
hannah-data - pacman-like game, child oriented - data files
hearse - exchange Nethack bones files with other players
hedgewars - Worms style game
heroes-common - Collect powerups and avoid your opponents' trails
heroes-data - Required data files for heroes
heroes-ggi - Collect powerups and avoid your opponents' trails
heroes-sdl - Collect powerups and avoid your opponents' trails
heroes-sound-effects - Optional sound files for heroes
heroes-sound-tracks - Optional sound files for heroes
hex-a-hop - puzzle game based on hexagonal tiles
hexxagon - Hexagonal Ataxx clone
hitori - eponymous puzzle game
holotz-castle - platform game with high doses of mystery
holotz-castle-data - platform game with high doses of mystery - data files
holotz-castle-editor - platform game with high doses of mystery - level editor
holotz-castle-milanb - platform game with high doses of mystery - extra levels
hrd - the puzzle game of HuaRongDao
ii-esu - shooter game
imaze-lesstif - multiplayer, 3D, labyrinth, run & shoot game (lesstif/motif client)
imaze-sounds - multiplayer, 3D, labyrinth, run & shoot game (sound files)
imaze-xaw - multiplayer, 3D, labyrinth, run & shoot game (xaw client)
imaze-xlabed - multiplayer, 3D, labyrinth, run & shoot game (lab generator)
imaze-xview - multiplayer, 3D, labyrinth, run & shoot game (xview client)
imazesrv - multiplayer, 3D, labyrinth, run & shoot game (server)
infon-devel - Develop bots for the infon game
infon-server - Program bugs to compete for food and survival - Server
infon-viewer - Program bugs to compete for food and survival - GUI
inform-mode - Emacs mode for editing Inform files
inventor-demo - Open Inventor demonstration programs and example code
jed-extra - collection of useful Jed modes and utilities
jester - board game similar to Othello
joy2key - Translate joystick movements into equivalent keystrokes
jscalibrator - GTK Joystick Calibrator
jumpnbump - cute multiplayer platform game with bunnies
jumpnbump-levels - cute multiplayer platform game with bunnies (extra levels)
jzip - Text mode interpreter for Z-Code adventures
kamefu - KDE All Machine Emulator Frontend for Unix - binary files
kamefu-data - Data files for Kamefu
kanatest - beginner's drill game to learn Japanese kana characters
kautoclick - an autoclicker for KDE
kball - game of skill and reflexes for all the family
kball-data - game of skill and reflexes for all the family - data files
kcheckers - Checkers boardgame
kde - the K Desktop Environment official modules
ketm - old school 2D-scrolling shooter
ketm-data - graphics and audio data for ketm
kitsune - Program to solve mathematical problems
kobodeluxe - a game of space battle
kobodeluxe-data - a game of space battle -- shared data
komi - A single player arcade game with Komi the Space Frog!
koules - abstract space action game
kq - adventure game in the spirit of Final Fantasy
kq-data - graphics and audio data for kq
kraptor - Classic shoot 'em up scroller game
kraptor-data - Classic shoot 'em up scroller game - data files
late - A simple game of capturing balls
late-data - data files for late game
lbreakout2 - A ball-and-paddle game with nice graphics
lbreakout2-data - A ball-and-paddle game with nice graphics (DATA FILES)
liballegro-doc - documentation for the Allegro library
liballegro4.2 - portable library for cross-platform game and multimedia development
liballegro4.2-dev - development files for the Allegro library
liballegro4.2-plugin-arts - aRts audio plugin for the Allegro library
liballegro4.2-plugin-esd - esd audio plugin for the Allegro library
liballegro4.2-plugin-jack - JACK audio plugin for the Allegro library
liballegro4.2-plugin-svgalib - SVGAlib video plugin for the Allegro library
libarkrpg-dev - development headers for Arkrpg
libarkrpg0c2a - shared libraries for Arkrpg
libatlas-cpp-0.6-1 - The protocol library of the World Forge project - runtime libs
libatlas-cpp-0.6-1-dbg - The protocol library of the World Forge project - debugging libs
libatlas-cpp-0.6-dev - The protocol library of the World Forge project - header files
libatlas-cpp-doc - The protocol library of the World Forge project - documentation
libbulletml-dev - C++ library to handle BulletML easily - development files
libbulletml0d1 - C++ library to handle BulletML easily - runtime library
libcegui-mk2-1 - Crazy Eddie's GUI (libraries)
libcegui-mk2-1-dbg - Crazy Eddie's GUI (debugging libraries)
libcegui-mk2-dev - Crazy Eddie's GUI (development files)
libcegui-mk2-doc - Crazy Eddie's GUI (documentation)
libclanapp-0.8-1 - ClanLib game SDK runtime
libclanlib-dev - ClanLib game SDK development files
libclansdl-0.8-1 - SDL module for ClanLib game SDK
libeigen2-dev - lightweight C++ template library for linear algebra
liberis-1.3-14 - The WorldForge client entity library
liberis-1.3-14-dbg - The WorldForge client entity library - debugging library
liberis-1.3-dev - The WorldForge client entity library - development files
liberis-doc - The WorldForge client entity library - API documentation
libexosip2-4 - eXtended OSIP library
libflatzebra-0.1-2 - Generic Game Engine library
libflatzebra-dev - Generic Game Engine library development files
libfreecell-solver-dev - Library for solving Freecell games (Development files)
libfreecell-solver0 - Library for solving Freecell games
libgames-cards-perl - Perl module for writing and playing card games
libggtl2 - generic game-tree search library
libggtl2-dev - generic game-tree search library
libgiigic1 - ggi library on top of libgii
libgiigic1-dev - development package for libgiigic
libglbsp-dev - node builder library for OpenGL-based Doom-style games (headers)
libglbsp3 - node builder library for OpenGL-based Doom-style games
libgrapple-1.0-1 - a network layer designed for games
libgrapple-dev - a network layer designed for games (development files)
libgtkhex0 - GNOME Hex editor for files (shared library)
libgtkhex0-dev - GNOME Hex editor for files (development headers)
libguichan-0.8.1-1 - small, efficient C++ GUI library
libguichan-0.8.1-1-dbg - small, efficient C++ GUI library (debugging symbols)
libguichan-allegro-0.8.1-1 - small, efficient C++ GUI library (allegro integration)
libguichan-dev - small, efficient C++ GUI library (development headers)
libguichan-opengl-0.8.1-1 - small, efficient C++ GUI library (OpenGL integration)
libguichan-sdl-0.8.1-1 - small, efficient C++ GUI library (SDL integration)
libkamefu-dev - Development headers for Kamefu
libkamefu0 - Libraries for Kamefu
libkxl0 - multimedia library for game development
libkxl0-dev - development files for libkxl0
libmercator-0.2-4c2a - WorldForge terrain library
libmercator-0.2-dev - WorldForge terrain library - development files
libnel-dbg - Massive multi-user 3D game environments library (debug)
libnel-dev - Massive multi-user 3D game environments library
libnel0 - Massive multi-user 3D game environments library
libopenal-dev - Software implementation of the OpenAL API (development files)
libopenal1 - Software implementation of the OpenAL API (libraries)
libopenal1-dbg - Software implementation of the OpenAL API (debugging symbols)
libopenscenegraph-dev - 3D scenegraph development files
libopenscenegraph7 - 3D scenegraph
libphysfs-1.0-0 - filesystem abstraction library for game programmers
libpixels-java - manipulation and filtering of images in Java
libpoker-eval - poker hand evaluator library
libpoker-eval-dev - poker hand evaluator library development files
libsdl-console - console that can be added to any SDL application
libsdl-console-dev - development files for libsdl-console
libsidplay1 - SID (MOS 6581) emulation library
libsidplay2 - SID (MOS 6581) emulation library
libsidplay2-dev - SID (MOS 6581) emulation library
libwfut-0.2-1 - WorldForge Update Tool (libraries)
libwfut-0.2-1-dbg - WorldForge Update Tool (debugging libs)
libwfut-0.2-dev - WorldForge Update Tool (development files)
lightyears - single player real-time strategy game with steampunk sci-fi
lincity - build & maintain a city/country
lincity-ng - City simulator game with polished graphics
lincity-ng-data - Media files for the city simulator game LinCity-NG
linux-igd - Linux UPnP Internet Gateway Device
liquidwar - A truely original multiplayer wargame
liquidwar-data - Data files for Liquid War
liquidwar-server - Liquid War server
lletters - GTK letters-learning game for small children
lletters-media - GTK letters-learning game for small children - data files
lmarbles - A game where you build figures out of colored marbles
lmemory - A children's game based on the "memory" card game
logstalgia - web server access log visualizer
londonlaw - london law game
lordsawar - A clone of the popular SSG game Warlords II
lordsawar-data - A clone of the popular SSG game Warlords II
lsnipes - A text-base maze-orientated game
lsr - The Linux Screen Reader for GNOME
ltris - very polished Tetris clone with CPU opponents
luola - multiplayer cave-flying game
luola-data - data files for luola
luola-levels - level files for luola
luola-nostalgy - nostalgy level files for luola
luxman - Pac-Man clone (svgalib based)
madbomber - A Kaboom! clone
madbomber-data - Datafiles for madbomber
magicmaze - rescue the maiden while avoiding the monsters
magicor - puzzle game in the spirit of solomon's key
magicor-data - data files for the magicor puzzle game
mah-jong - The original Mah-Jong game
mancala - Implementation of the simple board game called Mancala
manpages-de - German manpages
manpages-pl - Polish man pages
manpages-pt - Portuguese Versions of the Manual Pages
manpages-tr - Turkish version of the manual pages
matanza - Space ascii war game
mathwar - A flash card game designed to teach simple maths
matrem - An experiment in Artificial life
mazeofgalious - The Maze of Galious
mazeofgalious-data - The Maze of Galious
mednafen - multi-platform emulator, including NES, GB/A, Lynx, PC Engine
meritous - action-adventure dungeon crawl game
meritous-data - action-adventure dungeon crawl game (datafiles)
mgt - a game record display/editor for the oriental game of go
mines.app - Minesweeper for GNUstep
mirrormagic - Shoot around obstacles to collect energy using your beam.
moagg - 2D gravity game
moagg-data - data files for the moagg game
moaggedit - map editor for the Moagg game
monkey-bubble - game in which you must explode all bubbles
monopd - Monopoly game network server
monster-masher - GPL'ed mash'em-up action game for GNOME
monsterz - arcade puzzle game
monsterz-data - graphics and audio data for monsterz
moon-buggy - Drive a car across the moon
moon-buggy-esd - Drive a car across the moon (version with sound)
moon-lander - An SDL game based on the classic moon lander
moon-lander-data - Data files (sound, images) for moon-lander
mousetrap - A simple game of ball chasing
mu-cade - the physics centipede invasion, smashup waggly shmup
mu-cade-data - the physics centipede invasion - game data
mumble - Low latency VoIP client
nethack-common - Common files for Nethack dungeon crawl game
nethack-console - Text-based overhead view D&D-style adventure game
nethack-el - Emacs major-mode for playing NetHack
nethack-lisp - Text-based overhead view D&D-style adventure game
nethack-qt - Text-based/Qt overhead view D&D-style adventure game
nethack-spoilers - Spoiler files for the Nethack adventure game
nethack-x11 - Text-based/X11 overhead view D&D-style adventure game
netmaze - 3-D Multiplayer Combat Game
netpanzer - online multiplayer tactical warfare game
netpanzer-data - data files for the netPanzer game
netpanzer-dbg - debugging symbols for netpanzer
nettoe - Networked version of Tic Tac Toe (3x3 Grid) for the console
neverball - 3D floor-tilting game
neverball-common - data files for Neverball and Neverputt
neverputt - 3D miniature golf game
nexuiz - A fast-paced 3D first-person shooter
nexuiz-data - Nexuiz game data files
nexuiz-dbg - Debug information for the game Nexuiz
nexuiz-music - Nexuiz music files
nexuiz-server - Standalone server for Nexuiz
nexuiz-server-dbg - Debug symols for the Nexuiz game server
nikwi - platform game where your goal is to collect candies
nikwi-data - platform game where your goal is to collect candies - game data
ninvaders - A space invaders-like game using ncurses
njam - pacman-like game with multiplayer support
ogamesim - Console Ogame Simulator
ogamesim-www - WWW GUI for ogamesim
omega-rpg - A text-based roguelike game
oneisenough - 2D platform game about the epic struggle of balls
onscripter - Visual novel games engine compatible to NScripter
open-invaders - Space Invaders clone
open-invaders-data - Space Invaders clone (data package)
openarena - fast-paced 3D first-person shooter
openarena-data - OpenArena game data
openarena-server - game server for the game OpenArena
openbabel - Convert and manipulate chemical data files
opencity - a 3D city simulator game
opendb - Web-based lending database written in PHP
openglad - Top-down guantlet-style RPG
openmsx - the MSX emulator that aims for perfection
openrpg - client/server application to play RPG over the Internet
openscenegraph - 3D scenegraph binary files
openscenegraph-doc - 3D scenegraph documentation
orbital-eunuchs-sniper - An anti-terrorist, pro-Eunuchs, satellite sniping game
overgod - bi-directional scrolling arcade game
overgod-data - graphics and audio data for overgod
overkill - bloody 2D action deathmatch-like game in ascii-art
pachi - Platform game featuring Pachi el marciano
pachi-data - Platform game featuring Pachi el marciano (data files)
pacman4console - a console based pacman game
pangzero - action game that involves popping balloons with a harpoon
parsec47-data - retromodern hispeed shmup - game data
passage - game about the passage through life
pathogen - Puzzle game about matching 3D model structures
pathological - puzzle game involving paths and marbles
pathological-music - puzzle game involving paths and marbles [music]
pcsx-bin - Sony PlayStation emulator -- binary
pcsx-df - Sony PlayStation emulator -- binary
pcsx-i18n - Sony PlayStation emulator -- extra languages
penguin-command - a missile command clone
pengupop - Online multiplayer clone of Bust a Move
pennmush-i18n - i18n support files for the PennMUSH virtual world server
pennmush-mysql - text-based multi-user virtual world server with MySQL support
pente - Five in a row game for X and the console
pgn-extract - Portable Game Notation (PGN) extractor
pingus - Free Lemmings(TM) clone
pingus-data - Data files for pingus, a free Lemmings(TM) clone
pioneers - the Settlers of Catan board game
pioneers-console - the Settlers of Catan board game - console parts
pioneers-console-data - the Settlers of Catan board game - data files
pioneers-data - the Settlers of Catan board game - data files
pipenightdreams - connect pipes to get the water flowing from inlet to outlet
pipenightdreams-data - connect pipes to get the water flowing from inlet to outlet (data files)
pipewalker - Puzzle game - connect all computers to the net
pixbros - 2D game inspired in Bubble Bobble, Snow Bros and Tumble Pop
pixfrogger - help the frog cross the street
planetpenguin-racer - another 3D racing game featuring Tux, the Linux penguin
planetpenguin-racer-data - data files for the game PlanetPenguin Racer
planetpenguin-racer-dbg - another 3D racing game featuring Tux, the Linux penguin (debugging symbols)
planetpenguin-racer-extras - Additional courses for PlanetPenguin Racer
playmidi - MIDI player
plee-the-bear - A 2D platform game
plee-the-bear-data - Data for Plee the Bear
poker-web - Web interface to a poker-network server
pokerth - Texas hold'em game
pokerth-data - Texas hold'em game - common data files
pokerth-server - Texas hold'em game - server
pong2 - Remake of old arcade classic in OpenGL
pouetchess - 3D chess game
pouetchess-data - Data files for the game pouetChess
prboom - clone of the legendary first person shooter Doom
projectl - sword action shooting
psemu-input-omnijoy - Controller/keyboard plugin for PSX emulators
psemu-input-padjoy - Controller plugin for PSX emulators
psemu-sound-alsa - ALSA sound plugin for PSX emulators
psemu-sound-oss - OSS sound plugin for PSX emulators
psemu-video-x11 - software graphics plugin for PSX emulators
pvpgn - Gaming server that emulates Battle.net(R)
pybridge - An online contract bridge game. Gtk client
pybridge-common - Common files for pybridge
pybridge-server - Server files for pybridge
pydance - dancing simulation game similar to the kind in arcades
pydance-music - Songs and step patterns for pydance
pyntor - flexible and componentized presentation program
pyracerz - multiplayer top view 2D racing game
pyscrabble - a multiplayer scrabble implementation written in Python - client part
pyscrabble-common - a multiplayer scrabble implementation - common files
pyscrabble-server - a scrabble implementation written in Python - server part
pyslide - Tiny but powerful program to make animated presentations
pysol - X11 solitaire game written in Python
pysol-cardsets - Additional card graphics for Pysol
pysycache - Educational game to teach children to use the mouse
python-2play - peer-to-peer network game engine
python-fibranet - cooperative threading and event driven framework
python-ocempgui - graphical user interface toolkit providing widgets for PyGame
python-openal - port for Python of the OpenAL library
python-openbabel - Convert and manipulate chemical data files (Python binding)
python-poker-network - multiplayer poker server and client library
python-poker2d - GTK poker client to play on a poker-network server
python-pygame - SDL bindings for games development in Python
python-pyglet - a cross-platform windowing and multimedia library
python-pypoker-eval - python interface to poker hand evaluator library development files
python-rabbyt - sprite library for Python with game development in mind
python-renpy - framework for developing visual-novel type games - Python module
python-soya - high level 3D engine for Python
python-soya-doc - high level 3D engine for Python
python-tofu - high-level network game engine for Python
qgo - Go client and full featured SGF editor
qonk - Small build-and-conquer strategy game with very simple rules
qstat - Command-line tool for querying quake (and other) servers
qtads - Qt text-only interpreter for TADS
quarry - Board games Go, Amazons, and Reversi (a.k.a. Othello)
rafkill - vertical shoot'em-up similar to Raptor: Call of the Shadows
rafkill-data - graphics and audio data for rafkill
realtimebattle - Programming game
realtimebattle-common - Programming game
renpy - framework for developing visual-novel type games
renpy-demo - framework for developing visual-novel type games - demo
renpy-doc - framework for developing visual-novel type games - doc
renpy-thequestion - the question, a simple and complete Ren'Py game
ri-li - a toy train simulation game
ri-li-data - data files for Ri-li, a toy train simulation game
robocode - Java programming game based on battle tanks
robocode-doc - Java programming game based on battle tanks (documentation)
rockdodger - Dodge and blow up rocks with your spaceship
rolldice - A virtual dice roller
rrootage - arcade-style space shooting game
rrootage-data - space shooting game - data files
scanmem - Locate and modify a variable in a running process
scid - chess database
scorched3d - 3D artillery game similar to Scorched Earth
scorched3d-data - data files for Scorched3D game
scorched3d-dbg - 3D artillery game similar to Scorched Earth, debug data
scottfree - Interpreter for Adventure International games
scribble - Popular crossword game, similar to Scrabble(R)
scummvm - free implementation of LucasArts' SCUMM interpreter
sear - 3D client for the Worldforge game servers
sear-media - 3D client for the Worldforge game servers - data files
searchandrescue - fly aircraft to search (for) and rescue people in distress
sgf2dg - Creates TeX files from Go game records
sgt-puzzles - Simon Tatham's Portable Puzzle Collection - 1-player puzzle games
shisen.app - Shisen-sho puzzle game for GNUstep
sillypoker - A poker game
singularity - game where one becomes the singularity
singularity-music - Music for Endgame: Singularity game
slashem - A variant of Nethack
slashem-gtk - A variant of Nethack (Gtk window port)
slashem-sdl - A variant of Nethack (SDL window port)
slashem-x11 - A variant of Nethack (X11 window port)
slingshot - simple 2D shooting strategy game set in space, with gravity
slune - 3D racing and car-crashing game
smc - a Jump and Run game like Super Mario World written in C++
smc-data - levels for smc
smc-music - music files for smc
snake4 - Snake game
snowballz - fun RTS game featuring snowball fights with penguins
solarwolf - Collect the boxes and don't become mad
sopwith - port of the 1980's side-scrolling WWI dogfighting game
spacearyarya - third person shooter in pseudo-3D
spider - A two deck solitaire game for the X Window System
starvoyager - 2D space arcade game, themed around 'Star Trek' - binary
starvoyager-data - 2D space arcade game, themed around 'Star Trek' - data files
stax - collection of puzzle games similar to Tetris Attack
stormbaancoureur - simulated obstacle course for automobiles
stormbaancoureur-data - game data for Stormbaan Coureur
stroq - A Polarium/Chokkan Hitofude clone
sugar-connect-activity - connect the dots game on the XO laptop
sugar-memorize-activity - memory game activity on the XO laptop
supertransball2 - Thrust type of game
supertransball2-data - Data files for a thrust type of game
supertux - Classic 2D jump 'n run sidescroller with Tux
supertux-data - Levels for classic 2D jump 'n run sidescroller with Tux
supertux-data-stable - Levels for classic 2D jump 'n run sidescroller with Tux
supertux-stable - Classic 2D jump 'n run sidescroller with Tux
supertuxkart - kart racing game
supertuxkart-data - data for the supertuxkart kart racing game
tads2-mode - Emacs mode for editing TADS code
tatan - pointing STG shooter game
tecnoballz - breaking block game ported from the Amiga platform
tecnoballz-data - graphic, sound and music files for the game tecnoballz
teeworlds - An online multi-player platform 2D shooter
teeworlds-data - Data for Teeworlds; an online multi-player platform 2D shooter
teeworlds-server - Server for Teeworlds; an online multi-player platform 2D shooter
teg - Turn based strategy game
tenace - Bridge hand viewer and editor
tenmado - hard-core shoot 'em up game in blue-or-red world
tennix - 2D tennis game
tetrinet-client - textmode client for tetrinet, a multiplayer tetris-like game
tetrinet-server - server for tetrinet, a multiplayer tetris-like game
tetrinetx - Game server for Tetrinet
tex-chess - Chess fonts for TeX/LaTeX
tex-skak - Chess fonts for TeX/LaTeX
texlive-games - TeX Live: Games typesetting (chess, etc)
thrust - a port of the classic Commodore 64 game
tictactoe - tic-tac-toe game written in Ruby
tilda - terminal emulator with first person shooter console likeness
tint - TINT Is Not Tetris(tm) ...at least the name isn't
titanion - strike down super high-velocity swooping insects
titanion-data - strike down super high-velocity swooping insects - game data
tkgate - Event driven digital circuit simulator with Tcl/Tk
tomatoes - I Have No Tomatoes - tomato smashing game
tomatoes-data - I Have No Tomatoes - tomato smashing game
toppler - clone of the "Nebulus" game on old 8 and 16 bit machines
torcs - 3D racing cars simulator game using OpenGL
torcs-data - base data files for TORCS game
torcs-data-cars - data files for TORCS game - Cars set
torcs-data-tracks - data files for torcs game - Tracks set
torus-trooper - speeding ship sailing through barrage
torus-trooper-data - speeding ship sailing through barrage - game data
tourney-manager - perl interface to run chess engine tournaments
trackballs - An OpenGL-based game of marbles through a labyrinth
trackballs-dbg - Debugging symbols for Trackballs
transcend - retro-style, abstract, 2D shooter
trigger - free 3D rally racing car game
trigger-data - free 3D rally racing car game - data files
trophy - A 2D car racing action game
trophy-data - A 2D car racing action game (data files)
trophy-dbg - A 2D car racing action game (debugging symbols)
ttf-f500 - Wipeout 3 Font
tumiki-fighters-data - sticky 2D shooter - game data
tuxpuck - "Shufflepuck Cafe" Clone
tworld - Chip's Challenge Game Engine Emulation
typespeed - Zap words flying across the screen by typing them correctly
uligo - tsumego (go problems) practice tool
ultrastar-ng - karaoke game that allows user supplied songs
ultrastar-ng-gstreamer - karaoke game that allows user supplied songs
ultrastar-ng-xine - karaoke game that allows user supplied songs
unmass - Extract game archive files
val-and-rick - shooter game
val-and-rick-data - shooter game - game data
vbaexpress - Front-End for VisualBoyAdvance
vdr-plugin-freecell - Plugin for VDR that implements the card game "Freecell"
vdr-plugin-games - VDR plugin providing OSD games like tetris, snake and more
vdr-plugin-solitaire - Plugin to vdr that implements the card game "Solitaire"
vdr-plugin-spider - Plugin to vdr that implements the card game "Spider Arachnid"
vectoroids - vector-based rock-shooting
vegastrike - 3D space combat game
vegastrike-music - Music files for vegastrike
vertex - a GTK+OpenGL 3D modeller
vgacardgames - Four SVGAlib card games
viewmol - A graphical front end for computational chemistry programs.
viruskiller - Game about viruses invading your computer
visualboyadvance - a full featured Game Boy Advance emulator
visualboyadvance-gtk - a GTK+ front-end to VisualBoyAdvance emulator
vodovod - puzzle game, you must lead the water to the storage tank
wakkabox - An amusing block shuffling puzzle game
warzone2100 - 3D real time strategy game
warzone2100-data - data files for warzone2100
warzone2100-dbg - debug files for warzone2100
warzone2100-music - music for warzone2100
wfut - WorldForge Update Tool (executable)
whichwayisup - 2D platform game with a slight rotational twist
whitedune - graphical VRML97 viewer, editor, 3D modeller and animation tool
widelands - fantasy real-time strategy game
widelands-data - fantasy real-time strategy game (data files)
widelands-dbg - fantasy real-time strategy game (debug cruft)
wing - Galaga-like arcade game
wing-data - graphics and audio data for wing
wm-icons - Themed icon set that is Window Manager agnostic.
wmtictactoe - Dockable Tic Tac Toe game
worlded - world editor for Arkrpg
wormux - funny fight game on 2D maps
wormux-data - data files for the game wormux
wound-up - Arcade/Puzzle game involving cogs and elves
xarchon - An X11 version of the game Archon
xarchon-theme-default - The default theme for XArchon
xasteroids - X-based asteroids-style arcade game
xball - Simulate bouncing balls in a window
xbat - classic shoot 'em up game for X11
xbattle - Concurrent multi-player battle strategy game
xbl - 3-D tetris like game
xblast - game inspired by Dynablaster (dummy upgrade package)
xblast-tnt - multiplayer blast-the-others game inspired by Dynablaster
xblast-tnt-images - image files for xblast-tnt
xblast-tnt-levels - level files for xblast-tnt
xblast-tnt-mini - game inspired by Dynablaster (dummy upgrade package)
xblast-tnt-models - player models for xblast-tnt
xblast-tnt-musics - music files for xblast-tnt
xblast-tnt-sounds - sound files for xblast-tnt
xboing - blockout game for X
xbomb - a 'minesweeper' game with squares, hexagons or triangles
xbubble - A nice Puzzle Bubble clone
xbubble-data - Data files for XBubble, a nice Puzzle Bubble clone
xchain - A strategy game for 2-4 players
xconq - A graphical multi-player strategy game and game design system
xdemineur - Yet another minesweeper for X
xdigger - An arcade diamonds digging game for X11
xemeraldia - not just another tetris clone
xevil - A violent side-scrolling game for X
xfrisk - Server and X11 client for playing risk with humans or AIs
xgalaga - X version of the famous Galaga game
xjewel - match colors on falling columns of blocks
xjig - An X11 jigsaw puzzle
xjump - A jumping game for X
xletters - Type falling words before they land
xlife - John Conway's Game of Life, for X11
xmahjongg - tile-based solitaire game
xmille - The classic game of Mille Bournes
xmoto - 2D motocross platform game
xmoto-data - 2D motocross platform game - data files
xoids - Asteroids game with powerups and color graphics
xonix - Carve up the screen whilst dodging monsters
xpat2 - Generic patience game for X11
xpilot-extra - Maps, utilities and configs for XPilot
xpilot-ng - Multi-player tactical game for X (NG version)
xpilot-ng-client-sdl - Client for XPilot NG
xpilot-ng-client-x11 - Client for XPilot NG
xpilot-ng-common - Common files for XPilot NG
xpilot-ng-server - Server for hosting XPilot NG games
xpilot-ng-utils - Utilities for XPilot NG
xpuyopuyo - A puzzle game similar to tetris, played with colored blobs
xqf - X-based Quake Server Browser
xracer - Futuristic racing game
xracer-tools - Futuristic racing game - developer tools
xscavenger - A lode-runner-like platform game for X
xscorch - Clone of Scorched Earth
xshisen - Shisen-sho puzzle game for X11
xshogi - An X Window System Japanese Chess (Shogi) Board
xskat - 3-player card game "Skat"
xsok - generic Sokoban game for X11
xsol - X Solitaire
xsoldier - shoot 'em up game with the "not shooting" bonus
xtokkaetama - X Puzzle Game.
xtris - client-server multiplayer X tetris
xtron - Tron game for X11
xtux-client - arcade game featuring Free Software mascots
xtux-common - shared files for the arcade game X-Tux
xtux-levels - shared files for the arcade game X-Tux
xtux-server - server for the arcade game X-Tux
xvier - a "Four in a row" game
xwelltris - 3D Tetris like popular game similar to Welltris
xzip - Interpreter of Infocom-format story-files
yabause - Yet Another Buggy And Uncomplete Saturn Emulator
yabause-gtk - Yet Another Buggy And Uncomplete Saturn Emulator - Gtk port
yabause-qt - Yet Another Buggy And Uncomplete Saturn Emulator - Qt port
yakuake - a Quake-style terminal emulator based on KDE Konsole technology
yeahconsole - drop-down X terminal emulator wrapper
yics - Yahoo! Chess client for use with FICS interfaces
z80asm - assembler for the Zilog Z80 microprocessor
z80dasm - disassembler for the Zilog Z80 microprocessor
zatacka - Arcade multiplayer game like nibbles
zblast-data - sound files for zblast game
zblast-svgalib - svgalib version of zblast, shoot 'em up space game
zblast-x11 - X11 version of zblast, shoot 'em up space game
zec - Z-Shell Empire client
zivot - the game of life, simple console version
abuse-sfx - sound effects for Abuse
alien-arena - Standalone 3D first person online deathmatch shooter
alien-arena-browser - stand alone server browser for Alien Arena
alien-arena-data - Game data files for Alien Arena
alien-arena-server - Dedicated server for Alien Arena
angband - A single-player, text-based, dungeon simulation game.
apple2 - Apple ][ Emulator
blockade - A sliding block game
bsdgames-nonfree - rogue, the classic dungeon exploration game
crafty-books-medium - Medium-size opening books for crafty chess engine.
crafty-books-medtosmall - Medium-to-small size opening books for crafty chess engine.
crafty-books-small - Small-size opening books for crafty chess engine.
dgen - Sega Genesis/MegaDrive emulator
doom-wad-shareware - Shareware game files for the 3D game DOOM
exult - engine for Ultima VII (BG, FOV, SI, SS)
exult-studio - tools for editing and viewing exult games
funguloids - space-flying-mushroom-picking-simulator game
game-data-packager - Installer for game data files
glest - a free 3D real-time customizable strategy game
glest-data - a free 3d real-time customizable strategy game
gnuboy-sdl - SDL binaries for gnuboy - Game Boy Emulator
gnuboy-svga - SVGALIB binaries for gnuboy - Game Boy Emulator
gnuboy-x - X binaries for gnuboy - Game Boy Emulator
gwp - a VGA Planets strategy game client for GNOME
inform - story file compiler for the Inform interactive fiction language (v6)
inform-docs - documentation for the Inform interactive fiction language (v6)
kxmame - A KDE frontend for xmame emulator
lgc-pg - LGeneral Converter for Panzer General
lgeneral - A "Panzer General" - like game
libdscaler - Video deinterlacer plugins from the DScaler project
libjogl-java - Java bindings for OpenGL API (java library)
libjogl-java-doc - Documentation for the Java bindings for OpenGL
libjogl-jni - Java bindings for OpenGL API (java jni library)
maelstrom - An arcade-style game resembling Asteroids.
mssstest - Normalisation of disease scores for patients with Multiple Sclerosis
mythgame - Emulator & PC Game frontend module for MythTV
oolite - space-sim game Oolite ported to GNUStep/OpenGL linux
oolite-data - Data files for the space-sim game Oolite
openttd - reimplementation of Transport Tycoon Deluxe with enhancements
powder - Graphical dungeon crawling game
pq - Progress Quest is a "fire and forget" computer role-playing game
robotour - control mobile robots in this programmer's game
rocksndiamonds - Arcade style game
rott - Rise of the Triad -- The HUNT Begins
sauerbraten - 3D first-person game engine
sauerbraten-data - Game content for the Sauerbraten game
sauerbraten-dbg - Debug symbols for the Sauerbraten game engine
sauerbraten-server - Standalone server for the Sauerbraten game
sauerbraten-wake6 - Small but dodgy deathmatch/instagib map for the Sauerbraten game
sdlmame - An emulator for many arcade games
snes9x-x - X binaries for snes9x - Super NES Emulator
spellcast - The classic hand-waving multi-player X game of spellcasting:
spellcast-doc - Documentation for the multi-player X game of spellcasting.
stella - Atari 2600 Emulator for SDL & X windows
tads2 - Text mode interpreter for TADS version 2 game files
tads2-dev - TADS version 2 development tools
tads3 - Text mode interpreter for TADS game files
tads3-dev - TADS version 3 development tools
tads3-doc - TADS version 3 documentation
teamspeak-client - VoIP chat for online gaming
teamspeak-server - VoIP chat for online gaming (server)
tome - A single-player, text-based, dungeon simulation game.
tremulous - Aliens vs Humans, team based FPS game with elements of an RTS
tremulous-data - Tremulous datas
tremulous-doc - Tremulous documentation
tremulous-server - Tremulous server
tuxtype-data-nonfree - Educational Typing Tutor Game Starring Tux
uqm - The Ur-Quan Masters - An inter-galatic adventure game
uqm-content - The Ur-Quan Masters - Game data files
uqm-russian - Russian addon for 'The Ur-Quan Masters' game
warsow-data - Game data for Warsow
xapple2 - Apple ][ Emulator
xmame-common - Multiple Arcade Machine Emulator
xmame-sdl - SDL binaries for the Multiple Arcade Machine Emulator
xmame-svga - SVGALIB binaries for the Multiple Arcade Machine Emulator
xmame-x - X binaries for the Multiple Arcade Machine Emulator
xmess-sdl - SDL binaries for the Multi Emulator Super System
xmess-x - X binaries for the Multi Emulator Super System
zangband - A single-player, text-based, roguelike game
zangband-data - A single-player, text-based, roguelike game (datafiles)
bovo - gomoku board game for KDE 4
gnome-cards-data - data files for the GNOME card games
gnome-games - games for the GNOME desktop
gnome-games-data - data files for the GNOME games
kanagram - jumble word puzzle for KDE 4
katomic - atomix puzzle game for KDE 4
kbattleship - battleship board game for KDE 4
kblackbox - Black Box puzzle game for KDE 4
kblocks - a falling blocks game for KDE
kbounce - Jezzball arcade game for KDE 4
kbreakout - Breakout arcade game for KDE 4
kdegames - games from the official KDE 4 release
kdegames-card-data - card decks for KDE 4 games
kdegames-dbg - debugging symbols for the KDE 4 games module
kdegames-mahjongg-data - tilesets and backgrounds for Mahjongg games
kdiamond - three-in-a-row game for KDE 4
kfourinline - Connect Four game for KDE
kgeography - geography learning aid for KDE 4
kgoldrunner - Lode Runner arcade game for KDE 4
khangman - Hangman word puzzle for KDE 4
kiriki - Yahtzee dice game for KDE 4
kjumpingcube - simple tactical game for KDE 4
klines - color lines game for KDE 4
kmahjongg - Mahjongg solitaire game for KDE 4
kmines - minesweeper game for KDE 4
knetwalk - wire puzzle game for KDE 4
kolf - miniature golf game for KDE 4
kollision - simple ball dodging game for KDE 4
konquest - simple turn-based strategy game for KDE 4
kpat - solitaire card games for KDE 4
kreversi - reversi board game for KDE 4
ksame - SameGame puzzle game for KDE 4
kshisen - Shisen-Sho solitaire game for KDE 4
ksirk - Risk strategy game for KDE 4
kspaceduel - SpaceWar! arcade game for KDE 4
ksquares - Dots and Boxes game for KDE 4
ksudoku - Sudoku puzzle game and solver for KDE 4
ktuberling - stamp drawing toy for KDE 4
kubrick - game based on Rubik's Cube for KDE
libkdegames-dev - development files for the KDE 4 games module
libkdegames4 - libraries and common files for KDE 4 games
lskat - Lieutnant Skat card game for KDE
blender - Very fast and versatile 3D modeller/renderer
blinken - KDE 4 version of the Simon electronic memory game
gnome-games-servers - GGZ gaming zone servers for the GNOME games
sabre - fighter plane simulator for svgalib
sabre-common - data for the SABRE fighter plane simulator
wesnoth - fantasy turn-based strategy game
wesnoth-all - fantasy turn-based strategy game - complete suite
wesnoth-dbg - fantasy turn-based strategy game (debugging symbols)
wesnoth-server - multiplayer network server for Wesnoth
wesnoth-tools - tools for campaign developers for Wesnoth
xmms2-plugin-gme - XMMS2 - gme plugin
xsabre - fighter plane simulator for X11
zsnes - Emulator of the Super Nintendo Entertainment System

```

---

### Post by BslBryan on 2009-07-25
> **llamabr said:**
> Wine is very rarely the correct answer.  Have you searched for native games?  Most of those on that site can be played online, completely, and they'll work.

As you can see, it's a bit complicated to set up wine, and it usually won't work very well.

llamabr, you are 100% right, but I know both he and his wife-to-be personally, and my instructions are the only solution for her standards. :-P

---

### Post by Desktop_n00b on 2009-07-25
> **BslBryan said:**
> llamabr, you are 100% right, but I know both he and his wife-to-be personally, and my instructions are the only solution for her standards. :-P


Well actually she did say if I could find some "Time Management" and "Hidden Object" games she would be fine. Got a list of only those?

---

### Post by BslBryan on 2009-07-25
> **Desktop_n00b said:**
> Well actually she did say if I could find some "Time Management" and "Hidden Object" games she would be fine. Got a list of only those?

Great, you're a member for an hour and already you make a liar out of me. :P

---

### Post by Desktop_n00b on 2009-07-25
> **BslBryan said:**
> Great, you're a member for an hour and already you make a liar out of me. :P

Nah, even I was surprised by that lol

now I like that list. Now I will have a crap load of games to try for myself, but I need a separate list now of just those 2 type games I mentioned a sec ago for her. I tried looking in the 1st list but all that txt strains my eyes and I didn't see any, but the list is huge so there might be some

---

### Post by deesto on 2009-08-03
> **llamabr said:**
> Wine is very rarely the correct answer.Oh how I wish that were true, but there are some people who absolutely, positively must use application *X* or play game *Y*, and they won't even bother to try and use Linux without it.  Substitutions aren't helpful in these situations, where wine often is.
> Have you searched for native games?  Most of those on that site can be played online, completely, and they'll work.

As you can see, it's a bit complicated to set up wine, and it usually won't work very well...
True that it can be difficult to set up, but if and when it does work, it's quite a relief.

---

### Post by gristleizer on 2009-12-06
I'm a newb and am trying to get a Big Fish Game (the Tudors) to run via Wine (1.0.1) on Ubuntu 9.10 and following these instructions gets me nowhere. Is there a difference in getting this to work in Ubuntu 9.10?

---

