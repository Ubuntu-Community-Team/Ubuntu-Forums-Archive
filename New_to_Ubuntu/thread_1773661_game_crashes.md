---
title: "game crashes"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by kaloasd on 2011-06-02
My problem is that when i start open arena or tremulous I get a zoomed top left corner of the desktop and the sound but nothing else changes. I managed to escape out of open arena, the screen zoomed out but nothing responds. I end up restarting.

Please help !!!

---

### Post by ubudog on 2011-06-02
Hi there.  What type of graphics card are you using?  Also, what Ubuntu version do you have?

---

### Post by kaloasd on 2011-06-03
OS: Ubuntu 11.04
Video: Intel 82946GZ/GL integrated

---

### Post by ubudog on 2011-06-03
Have you installed any drivers for the card yet (System>Administration>Additional Drivers)?

---

### Post by kaloasd on 2011-06-07
I've tried that, there are no additional drivers, but maybe I forgot to say that the games sometimes work and during gameplay i have no crashes.

---

### Post by ubudog on 2011-06-07
Hmm... strange...

Could you try running it from the terminal and posting the output?  (Applications>Accessories>Terminal)

```
openarena
```

---

### Post by kaloasd on 2011-06-08
I did it with tremulous because it has the same bug. Do I need to do it with open arena?
<code>
tremulous 1.1.0 linux-x86 Aug  5 2010
----- FS Startup -----
/home/kalo/.tremulous/base
/usr/share/games/tremulous/base/z-debian-tremulous-ui-fixes.pk3 (1 files)
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreatiom-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2081 files in pk3 files
execing default.cfg
execing autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_INIT(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
</code>

---

### Post by ubudog on 2011-06-08
Could you try it with OpenArena and post the output?

---

### Post by ubudog on 2011-06-08
Ok, I did some searching.  I believe the issue is caused by not having the correct drivers installed... you can download them for your graphics card type from here:
[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+controllers&ProductProduct=Intel%C2%AE+82946GZ+Graphics+Controller](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+controllers&ProductProduct=Intel%C2%AE+82946GZ+Graphics+Controller)

Make sure you select Linux.  Let me know how it goes.   :)

---

### Post by kaloasd on 2011-06-08
Thanks, I also managed to get it out of full screenmode and it works good enough.

---

### Post by ubudog on 2011-06-08
Cool no problem.  The driver worked?

---

