---
title: "Why doesn't games work?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Marrkle on 2009-07-07
So I got my 8.04 Hardy installed( thanks to all that helped) and I downloaded 2 3D FPses, 

Alien Arena
OpenArena

But when I click them they switch to full screen and immediately close. 

Any advice?

---

### Post by ~sHyLoCk~ on 2009-07-07
Run them from the terminal and see what error message you get that could provide some clue.

---

### Post by Marrkle on 2009-07-09
OpenArena run error:

marrkle@Marrkle:~$ openarena
ioQ3 1.33+oa linux-i386 Oct 28 2007
----- FS_Startup -----
Current search path:
/home/marrkle/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (76 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (191 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (11 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1496 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (9 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (620 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (171 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (73 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (926 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
3573 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by aeiah on 2009-07-09
the clue is here:
> 
You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.
************************************************** *********
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


you're using a graphics driver that doesn't provide opengl accelleration. what graphics card do you have? im guessing nvidia or ati. you need to download and install the restricted hardware drivers for your graphics card. you can do it through the menu > system > administration area

---

### Post by Marrkle on 2009-07-10
> **aeiah said:**
> the clue is here:


you're using a graphics driver that doesn't provide opengl accelleration. what graphics card do you have? im guessing nvidia or ati. you need to download and install the restricted hardware drivers for your graphics card. you can do it through the menu > system > administration area

I don't see any restricted hardware drivers...

---

### Post by Troll_the_Great on 2009-07-10
> **Marrkle said:**
> I don't see any restricted hardware drivers...

Go to System - Administration - Hardware Drivers and enable your drivers from there. If you have an ATI or nVidia card you can install EnvyNG and this program will automatically install your drivers.
Open a terminal (Applications - Accessories - Terminal) and type:
```
sudo apt-get install envyng-gtk
```
After you install it, you can find it under Applications - System Tools - EnvyNG.
Post back if you have any problems.
Cheers!

---

### Post by Marrkle on 2009-07-10
> **Troll_the_Great said:**
> Go to System - Administration - Hardware Drivers and enable your drivers from there. If you have an ATI or nVidia card you can install EnvyNG and this program will automatically install your drivers.
Open a terminal (Applications - Accessories - Terminal) and type:
```
sudo apt-get install envyng-gtk
```After you install it, you can find it under Applications - System Tools - EnvyNG.
Post back if you have any problems.
Cheers!
  It says I have no propriety drivers are in use on this system

---

### Post by Troll_the_Great on 2009-07-10
> **Marrkle said:**
> It says I have no propriety drivers are in use on this system

Who says you do not have any propriety drivers? The Hardware Drivers section? Did you install EnvyNG? What kind of video card do you have? Open a terminal, type 
```
lspci | grep VGA
``` and post the output.

---

### Post by Marrkle on 2009-07-10
> **Troll_the_Great said:**
> Who says you do not have any propriety drivers? The Hardware Drivers section? Did you install EnvyNG? What kind of video card do you have? Open a terminal, type 
```
lspci | grep VGA
``` and post the output.

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

---

### Post by Troll_the_Great on 2009-07-10
> **Marrkle said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

And EnvyNG doesn't work? Did you installed it?

---

### Post by Majorix on 2009-07-10
Your video card is really old. I doubt it is enough to run the games you are trying to run.

---

