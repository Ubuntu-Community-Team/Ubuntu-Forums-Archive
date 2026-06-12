---
title: "zsnes where is it?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-01-21
I recently installed zsnes and I go to applications, games, and click on thye zsnes emulator and nothing happens, whats up?

---

### Post by bruce89 on 2009-01-21
It's broken, you'll need to install the version from intrepid-proposed (or intrepid-updates).

---

### Post by ja660k on 2009-01-21
strange, 
open terminal and type
```

zsnes &

```
and see if that opens it?

---

### Post by LunaticHiatus on 2009-01-21
I get this when I type zsnes &


 ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d50558]
/lib/tls/i686/cmov/libc.so.6[0xb7d4e680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 229425     /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 229425     /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 229425     /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09ccf000-09d19000 rw-p 09ccf000 00:00 0          [heap]
b6c11000-b7740000 rw-p b6c11000 00:00 0 
b7740000-b778e000 r-xp 00000000 08:01 690025     /usr/lib/libpulse.so.0.4.1
b778e000-b778f000 r--p 0004d000 08:01 690025     /usr/lib/libpulse.so.0.4.1
b778f000-b7790000 rw-p 0004e000 08:01 690025     /usr/lib/libpulse.so.0.4.1
b7790000-b779c000 r-xp 00000000 08:01 690026     /usr/lib/libpulse-simple.so.0.0.1
b779c000-b779d000 r--p 0000b000 08:01 690026     /usr/lib/libpulse-simple.so.0.0.1
b779d000-b779e000 rw-p 0000c000 08:01 690026     /usr/lib/libpulse-simple.so.0.0.1
b77ae000-b77c3000 r-xp 00000000 08:01 689492     /usr/lib/libICE.so.6.3.0
b77c3000-b77c4000 rw-p 00014000 08:01 689492     /usr/lib/libICE.so.6.3.0
b77c4000-b77c6000 rw-p b77c4000 00:00 0 
b77c6000-b7813000 r-xp 00000000 08:01 689567     /usr/lib/libXt.so.6.0.0
b7813000-b7817000 rw-p 0004c000 08:01 689567     /usr/lib/libXt.so.6.0.0
b7817000-b782d000 r-xp 00000000 08:01 690057     /usr/lib/libaudio.so.2.4
b782d000-b782e000 r--p 00015000 08:01 690057     /usr/lib/libaudio.so.2.4
b782e000-b782f000 rw-p 00016000 08:01 690057     /usr/lib/libaudio.so.2.4
b7836000-b7837000 rw-p b7836000 00:00 0 
b7837000-b783a000 r-xp 00000000 08:01 1458216    /lib/libcap.so.1.10
b783a000-b783b000 rw-p 00002000 08:01 1458216    /lib/libcap.so.1.10
b783b000-b783d000 r-xp 00000000 08:01 737954     /usr/lib/ao/plugins-2/libpulse.so
b783d000-b783f000 rw-p 00001000 08:01 737954     /usr/lib/ao/plugins-2/libpulse.so
b783f000-b7861000 r-xp 00000000 08:01 689608     /usr/lib/libaudiofile.so.0.0.2
b7861000-b7864000 rw-p 00021000 08:01 689608     /usr/lib/libaudiofile.so.0.0.2
b7864000-b786d000 r-xp 00000000 08:01 278575     /usr/lib/libesd.so.0.2.39
b786d000-b786e000 r--p 00008000 08:01 278575     /usr/lib/libesd.so.0.2.39
b786e000-b786f000 rw-p 00009000 08:01 278575     /usr/lib/libesd.so.0.2.39
b786f000-b7897000 r-xp 00000000 08:01 1458286    /lib/libpcre.so.3.12.1
b7897000-b7898000 r--p 00027000 08:01 1458286    /lib/libpcre.so.3.12.1
b7898000-b7899000 rw-p 00028000 08:01 1458286    /lib/libpcre.so.3.12.1
b7899000-b794e000 r-xp 00000000 08:01 688690     /usr/lib/libglib-2.0.so.0.1800.2
b794e000-b794f000 r--p 000b4000 08:01 688690     /usr/lib/libglib-2.0.so.0.1800.2
b794f000-b7950000 rw-p 000b5000 08:01 688690     /usr/lib/libglib-2.0.so.0.1800.2
b7950000-b7954000 r-xp 00000000 08:01 688696     /usr/lib/libgthread-2.0.so.0.1800.2
b7954000-b7955000 r--p 00003000 08:01 688696     /usr/lib/libgthread-2.0.so.0.1800.2
b7955000-b7956000 rw-p 00004000 08:01 688696     /usr/lib/libgthread-2.0.so.0.1800.2
b7956000-b795b000 r-xp 00000000 08:01 690055     /usr/lib/libartsc.so.0.0.0
b795b000-b795c000 r--p 00004000 08:01 690055     /usr/lib/libartsc.so.0.0.0
b795c000-b795d000 rw-p 00005000 08:01 690055     /usr/lib/libartsc.so.0.0.0
b795d000-b795f000 r-xp 00000000 08:01 737953     /usr/lib/ao/plugins-2/liboss.so
b795f000-b7961000 rw-p 00001000 08:01 737953     /usr/lib/ao/plugins-2/liboss.so
b7961000-b7968000 r-xp 00000000 08:01 689517     /usr/lib/libSM.so.6.0.0
b7968000-b7969000 r--p 00006000 08:01 689517     /usr/lib/libSM.so.6.0.0
b7969000-b796a000 rw-p 00007000 08:01 689517     /usr/lib/libSM.so.6.0.0
b796a000-b796b000 r-xp 00000000 08:01 737952     /usr/lib/ao/plugins-2/libnas.so
b796b000-b796d000 rw-p 00000000 08:01 737952     /usr/lib/ao/plugins-2/libnas.so
b796d000-b7977000 r-xp 00000000 08:01 1492095    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7977000-b7978000 r--p 00009000 08:01 1492095    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7978000-b7979000 rw-p 0000a000 08:01 1492095    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7979000-b7982000 r-xp 00000000 08:01 1492099    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7982000-b7983000 r--p 00008000 08:01 1492099    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7983000-b7984000 rw-p 00009000 08:01 1492099    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7984000-b7999000 r-xp 00000000 08:01 1492089    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7999000-b799a000 r--p 00014000 08:01 1492089    /lib/tls/i686/cmov/libnsl-2.8.90.so
b799a000-b799b000 rw-p 00015000 08:01 1492089    /lib/tls/i686/cmov/libnsl-2.8.90.so
b799b000-b799d000 rw-p b799b000 00:00 0 
b799d000-b79a4000 r-xp 00000000 08:01 1492091    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b79a4000-b79a5000 r--p 00006000 08:01 1492091    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b79a5000-b79a6000 rw-p 00007000 08:01 1492091    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b79a6000-b79a8000 rw-p b79a6000 00:00 0 
b79a8000-b79ac000 r-xp 00000000 08:01 689538     /usr/lib/libXdmcp.so.6.0.0
b79ac000-b79ad000 rw-p 00003000 08:01 689538     /usr/lib/libXdmcp.so.6.0.0
b79ad000-b79af000 r-xp 00000000 08:01 689527     /usr/lib/libXau.so.6.0.0
b79af000-b79b0000 rw-p 00001000 08:01 689527     /usr/lib/libXau.so.6.0.0
b79b0000-b79b1000 rw-p b79b0000 00:00 0 
b79b1000-b79c8000 r-xp 00000000 08:01 279252     /usr/lib/libxcb.so.1.0.0
b79c8000-b79c9000 r--p 00016000 08:01 279252     /usr/lib/libxcb.so.1.0.0
b79c9000-b79ca000 rw-p 00017000 08:01 279252     /usr/lib/libxcb.so.1.0.0
b79ca000-b79cb000 r-xp 00000000 08:01 279250     /usr/lib/libxcb-xlib.so.0.0.0
b79cb000-b79cc000 r--p 00000000 08:01 279250     /usr/lib/libxcb-xlib.so.0.0.0
b79cc000-b79cd000 rw-p 00001000 08:01 279250     /usr/lib/libxcb-xlib.so.0.0.0
b79cd000-b79d4000 r-xp 00000000 08:01 1492108    /lib/tls/i686/cmov/librt-2.8.90.so
b79d4000-b79d5000 r--p 00007000 08:01 1492108    /lib/tls/i686/cmov/librt-2.8.90.so
b79d5000-b79d6000 rw-p 00008000 08:01 1492108    /lib/tls/i686/cmov/librt-2.8.90.so
b79d6000-b79dd000 r-xp 00000000 08:01 278557     /usr/lib/libdrm.so.2.3.1
b79dd000-b79de000 r--p 00006000 08:01 278557     /usr/lib/libdrm.so.2.3.1
b79de000-b79df000 rw-p 00007000 08:01 278557     /usr/lib/libdrm.so.2.3.1
b79df000-b79e3000 r-xp 00000000 08:01 689543     /usr/lib/libXfixes.so.3.1.0
b79e3000-b79e4000 rw-p 00003000 08:01 689543     /usr/lib/libXfixes.so.3.1.0
b79e4000-b79e5000 rw-p b79e4000 00:00 0 
b79e5000-b79e7000 r-xp 00000000 08:01 689536     /usr/lib/libXdamage.so.1.1.0
b79e7000-b79e8000 rw-p 00001000 08:01 689536     /usr/lib/libXdamage.so.1.1.0
b79e8000-b79ec000 r-xp 00000000 08:01 689577     /usr/lib/libXxf86vm.so.1.0.0
b79ec000-b79ed000 r--p 00003000 08:01 689577     /usr/lib/libXxf86vm.so.1.0.0
b79ed000-b79ee000 rw-p 00004000 08:01 689577     /usr/lib/libXxf86vm.so.1.0.0
b79ee000-b79fb000 r-xp 00000000 08:01 689541     /usr/lib/libXext.so.6.4.0
b79fb000-b79fd000 rw-p 0000c000 08:01 689541     /usr/lib/libXext.so.6.4.0
b79fd000-b7ae8000 r-xp 00000000 08:01 689463     /usr/lib/libX11.so.6.2.0
b7ae8000-b7ae9000 r--p 000ea000 08:01 689463     /usr/lib/libX11.so.6.2.0
b7ae9000-b7aeb000 rw-p 000eb000 08:01 689463     /usr/lib/libX11.so.6.2.0
b7aeb000-b7aec000 rw-p b7aeb000 00:00 0 
b7aec000-b7aff000 r-xp 00000000 08:01 689953     /usr/lib/libdirect-1.0.so.0.1.0
b7aff000-b7b00000 r--p 00012000 08:01 689953     /usr/lib/libdirect-1.0.so.0.1.0
b7b00000-b7b01000 rw-p 00013000 08:01 689953     /usr/lib/libdirect-1.0.so.0.1.0
b7b01000-b7b08000 r-xp 00000000 08:01 689955     /usr/lib/libfusion-1.0.so.0.1.0
b7b08000-b7b09000 r--p 00006000 08:01 689955     /usr/lib/libfusion-1.0.so.0.1.0
b7b09000-b7b0a000 rw-p 00007000 08:01 689955     /usr/lib/libfusion-1.0.so.0.1.0
b7b0a000-b7b0b000 rw-p b7b0a000 00:00 0 
b7b0b000-b7b6f000 r-xp 00000000 08:01 689954     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b6f000-b7b70000 r--p 00063000 08:01 689954     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b70000-b7b71000 rw-p 00064000 08:01 689954     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b71000-b7b73000 r-xp 00000000 08:01 1492084    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b73000-b7b74000 r--p 00001000 08:01 1492084    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b74000-b7b75000 rw-p 00002000 08:01 1492084    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b75000-b7c38000 r-xp 00000000 08:01 689598     /usr/lib/libasound.so.2.0.0
b7c38000-b7c3a000 r--p 00

---

### Post by LunaticHiatus on 2009-01-21
how do I go abouts installing the intrepid-proposed version?

---

### Post by dawynn on 2009-01-21
This strikes at the heart of a very basic lesson when working with Linux:

I just used the menus to try to run application xyz, and it didn't start.  What happened?

The best first diagnostic tool you can use is the command line.  Bring up a terminal and try to run the same application.  Many tools will not present any errors if you just try to run them from the menus.  If there are any issues, they will just silently die -- no splash screen, no warning screens.

However, when run through a console, the same application will often give at least some kind of an error.  It may be that it cannot find a library, or that it had some kind of segfault.  At least you'll have something more concrete to report to the forums or bug database.

Cheers!

---

### Post by dawynn on 2009-01-21
Looks like our last messages crossed paths.  I'm away from my Linux machine, but I'll try to help.

In Synaptic, there's an option in the pull down menus for Repositories (I believe its under Preferences).  This is the same menu you can also access from the main Ubuntu menus called something like Software Sources.

Once you have this screen pulled up, click the Updates tab, and make sure that the intrepid-proposed option is checkmarked.  Exit out of your screen and refresh the package list.

At this point, I would suggest *against* updating everything that just became available.  These are packages that are proposed, but haven't quite gotten approval to go into Intrepid yet.  Anything you install from here does not have the full support of the Ubuntu community.  So, personally, I would suggest that you get what you need, then unselect this repository.

But, while you have it selected -- retrieve the latest zsnes and any library updates that it needs.

Cheers!

---

### Post by LunaticHiatus on 2009-01-21
thank ya, worked wonderfully

---

