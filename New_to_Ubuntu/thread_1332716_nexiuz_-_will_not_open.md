---
title: "nexiuz - will not open"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by know-no-code on 2009-11-20
Hi i am rather new to Linux and Ubuntu so bare with me.

I downloaded the game Nexuiz a few days ago and it will not open (as in i click the Nexuiz program in the games tab) and nothing happens. This happened with other games as well.

I tried running it from the terminal and this is what i got. What do you think? 

Nexuiz Linux 08:21:26 Jun  6 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (4066 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" "libmodplug.so" - failed.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
couldn't exec config.cfg
execing config_update.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
*** glibc detected *** nexuiz: corrupted double-linked list: 0x0c7b6ab8 ***

Anything would be appreciated

---

### Post by Trevster on 2009-11-20
Hello,

Run the following command and post the output. Do you have drivers for your graphics card installed?

glxinfo | grep rendering

---

### Post by know-no-code on 2009-11-21
well here is what it spat out

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Apparently i am missing something

---

### Post by know-no-code on 2009-12-01
Got it working, it does not run all that smooth but i think it is just my cpu.

---

