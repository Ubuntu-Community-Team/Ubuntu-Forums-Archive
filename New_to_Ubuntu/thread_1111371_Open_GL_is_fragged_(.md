---
title: "Open GL is fragged :("
date: 2009-03-30
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-03-30
So I am starting to think one of the recent automatic updates Ubuntu downloaded killed something graphics wise... I started another thread [here]() about compiz not working anymore. 

Now when I try to load any application that uses Open GL I can the following errors: ```
jeff@jeff-ubuntu:~$ neverball
neverball: Could not create GL context
jeff@jeff-ubuntu:~$ nexuiz
Nexuiz Linux 08:39:45 Jun  6 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (4066 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
execing config_update.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1680x1050x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 1680x1050: Could not create GL context
Desired video mode fail, trying fallbacks...
Initializing Video Mode: fullscreen 1680x1050x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 1680x1050: Could not create GL context
Initializing Video Mode: fullscreen 1680x1050x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 1680x1050: Could not create GL context
Initializing Video Mode: fullscreen 1680x1050x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 1680x1050: Could not create GL context
Initializing Video Mode: fullscreen 640x1050x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 640x1050: Could not create GL context
Initializing Video Mode: fullscreen 640x480x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 640x480: Could not create GL context
Initializing Video Mode: fullscreen 640x480x16x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Failed to set video mode to 640x480: Could not create GL context
Quake Error: Video modes failed

```

Those are the outputs from two games, but all the others than use Open GL give something similar. Anyone else having similar issues or have any idea how I can correct them?

~Jeff

---

### Post by CatKiller on 2009-03-30
Your link is broken, btw.

You haven't said in either thread what graphics card you're using, or the driver that you're using. ```
glxinfo | grep direct
``` will probably show you what the problem is.

---

### Post by beastrace91 on 2009-03-30
Ehh, my GFX card is in my sig, as for my drivers I am using the 180.27 atm.

I am currently downloading the 9.04 beta and going to format and do a clean install with it. I've had alot of broken packages/gfx issues over the last few months and want a fresh start.

~Jeff

---

