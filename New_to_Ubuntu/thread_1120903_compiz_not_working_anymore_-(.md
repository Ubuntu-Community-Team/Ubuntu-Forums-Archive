---
title: "compiz not working anymore :-("
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Vulgor Schnecke on 2009-04-09
hi there,

so, i have this strange problem atm when i set up my comp with ubuntu everything was working perfectly....today i updated some libraries as the update manager told me. when i rebooted i was only able to log in to ubuntu in a command line like mode, not log in screen. when i typed in "firefox" it said "no screen specified" ior soemthing like that. so i ran ubuntu in recovery mode and then i got the usual login screen and the usual GUI,. so i was happy. but ever since, compiz has stopped working. i ran a script called compiz-check, and this is what i got:

""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M56P [Radeon Mobility X1600]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

ok, i have absolutley no idea even where to begin to start solving this problem^^. it used to be working perfectly fine.......
:-(
oh yeah, as for my graphics card, i have a laptop with ATI Mobility Radeon X1400 and im using proprietary ATI drivers.
so, i would gs reatly appreciate any help i can get to tackle this problem. thx!

---

### Post by ajgreeny on 2009-04-09
Try reinstalling your ATI drivers as it may be that there was a kernel update.  Compiz-check will not do anything in a cli, if that's how you used it, only in a gui terminal, eg gnome-terminal.  It needs x to be running to check it.  But I see you are now running the radeon driver which is the open source driver, not the proprietary one you had before.

---

