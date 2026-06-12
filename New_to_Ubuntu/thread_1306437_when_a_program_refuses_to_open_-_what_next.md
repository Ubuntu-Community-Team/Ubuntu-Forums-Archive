---
title: "when a program refuses to open - what next?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by listerdl on 2009-10-30
Hi, I use audacious a lot, well used to! The program simply refuses to open.

Any ideas on what I ought to do next to bring it back to life?

Thanks!

---

### Post by Tony Flury on 2009-10-30
if you run it from the terminal - you might get an error message that you can then copy and paste here ...

There could 1000 reasons why it wont start, the error message would help diagnose the problem.

---

### Post by listerdl on 2009-10-30
> **Tony Flury said:**
> if you run it from the terminal - you might get an error message that you can then copy and paste here ..

How do i do that :-k

---

### Post by kansasnoob on 2009-10-30
You might try pressing Alt & F2 then typing audacious and see what happens.

I'm actually thinking reinstall:

```
sudo apt-get install --reinstall audacious
```

**[COLOR="Red"]But that could hose any customizations you've made to Audacious![/COLOR]**

---

### Post by Pogeymanz on 2009-10-30
In your menu, go to Accessories->Terminal

and then type "audacious" (not quotes) into it and hit enter. It will give an error. Post that error here.

---

### Post by sandyd on 2009-10-30
most of the time, its a problem with your settings.
so remove the .audicious folder thats in your home folder and try starting it again.

---

### Post by listerdl on 2009-10-31
> **kansasnoob said:**
> You might try pressing Alt & F2 then typing audacious and see what happens.

I'm actually thinking reinstall:

```
sudo apt-get install --reinstall audacious
```

**[COLOR="Red"]But that could hose any customizations you've made to Audacious![/COLOR]**

Yeah I tried that, re-booted and it still refuses to open - it simply does nothing.

From the terminal I typed in 'audacious' and this is the result:

```
henry@DELL-laptop:~$ audacious
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
Segmentation fault

```

Thanks for all replies/help with this

---

### Post by humphreybc on 2009-10-31
Sounds like a problem with the program itself. Perhaps look on Launchpad for that error message, see if there are any bugs already filed?

If not, you could file one yourself. Alt + F2, and type:

```

ubuntu-bug audacious

```

---

### Post by thomasyen on 2009-10-31
I have the exact same problem. First, I installed the debug symbols, and tried to play the file (in my case, a FLAC). I got this: ```
*** glibc detected *** /usr/bin/audacious2: double free or corruption (out): 0xb4727600 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xbd2ff1]
/lib/tls/i686/cmov/libc.so.6[0xbd46f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xbd779d]
/usr/bin/audacious2[0x805c0e6]
/usr/lib/audacious/Input/flacng.so(flac_play_file+0x33d)[0xaee6ad]
/usr/bin/audacious2[0x805d23e]
/lib/libglib-2.0.so.0[0x66536f]
/lib/tls/i686/cmov/libpthread.so.0[0x44a80e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xc347ee]
======= Memory map: ========
00110000-001a2000 r-xp 00000000 08:16 8299       /usr/lib/libgdk-x11-2.0.so.0.1800.3
001a2000-001a4000 r--p 00092000 08:16 8299       /usr/lib/libgdk-x11-2.0.so.0.1800.3
001a4000-001a5000 rw-p 00094000 08:16 8299       /usr/lib/libgdk-x11-2.0.so.0.1800.3
001a5000-001a7000 r-xp 00000000 08:16 1887884    /usr/lib/libXcomposite.so.1.0.0
001a7000-001a8000 r--p 00001000 08:16 1887884    /usr/lib/libXcomposite.so.1.0.0
001a8000-001a9000 rw-p 00002000 08:16 1887884    /usr/lib/libXcomposite.so.1.0.0
001a9000-001ab000 r-xp 00000000 08:16 1885776    /usr/lib/libXinerama.so.1.0.0
001ab000-001ac000 rw-p 00001000 08:16 1885776    /usr/lib/libXinerama.so.1.0.0
001ac000-001ad000 r-xp 00000000 08:16 2474710    /usr/lib/audacious/Effect/voice_removal.so
001ad000-001ae000 r--p 00000000 08:16 2474710    /usr/lib/audacious/Effect/voice_removal.so
001ae000-001af000 rw-p 00001000 08:16 2474710    /usr/lib/audacious/Effect/voice_removal.so
001af000-001ba000 r-xp 00000000 08:16 1889943    /usr/lib/libaudcore.so.1.0.0
001ba000-001bb000 r--p 0000a000 08:16 1889943    /usr/lib/libaudcore.so.1.0.0
001bb000-001bc000 rw-p 0000b000 08:16 1889943    /usr/lib/libaudcore.so.1.0.0
001bc000-001e3000 r-xp 00000000 08:16 1888365    /usr/lib/libpangoft2-1.0.so.0.2600.0
001e3000-001e4000 r--p 00027000 08:16 1888365    /usr/lib/libpangoft2-1.0.so.0.2600.0
001e4000-001e5000 rw-p 00028000 08:16 1888365    /usr/lib/libpangoft2-1.0.so.0.2600.0
001e5000-001f0000 r-xp 00000000 08:16 1888363    /usr/lib/libpangocairo-1.0.so.0.2600.0
001f0000-001f1000 r--p 0000a000 08:16 1888363    /usr/lib/libpangocairo-1.0.so.0.2600.0
001f1000-001f2000 rw-p 0000b000 08:16 1888363    /usr/lib/libpangocairo-1.0.so.0.2600.0
001f2000-001fe000 r-xp 00000000 08:16 1887364    /usr/lib/libmowgli.so.1.0.0
001fe000-00200000 rw-p 0000b000 08:16 1887364    /usr/lib/libmowgli.so.1.0.0
00200000-00202000 r-xp 00000000 08:16 3244041    /lib/tls/i686/cmov/libdl-2.10.1.so
00202000-00203000 r--p 00001000 08:16 3244041    /lib/tls/i686/cmov/libdl-2.10.1.so
00203000-00204000 rw-p 00002000 08:16 3244041    /lib/tls/i686/cmov/libdl-2.10.1.so
00204000-00205000 r-xp 00000000 08:16 2187480    /usr/lib/tls/libnvidia-tls.so.185.18.36
00205000-00206000 rw-p 00000000 08:16 2187480    /usr/lib/tls/libnvidia-tls.so.185.18.36
00206000-0020c000 r-xp 00000000 08:16 1887297    /usr/lib/libSAD.so.2.0.0
0020c000-0020d000 r--p 00005000 08:16 1887297    /usr/lib/libSAD.so.2.0.0
0020d000-0020e000 rw-p 00006000 08:16 1887297    /usr/lib/libSAD.so.2.0.0
0020e000-00232000 r-xp 00000000 08:16 3244042    /lib/tls/i686/cmov/libm-2.10.1.so
00232000-00233000 r--p 00023000 08:16 3244042    /lib/tls/i686/cmov/libm-2.10.1.so
00233000-00234000 rw-p 00024000 08:16 3244042    /lib/tls/i686/cmov/libm-2.10.1.so
00234000-002c7000 r-xp 00000000 08:16 1887973    /usr/lib/libgio-2.0.so.0.2200.2
002c7000-002c8000 r--p 00092000 08:16 1887973    /usr/lib/libgio-2.0.so.0.2200.2
002c8000-002c9000 rw-p 00093000 08:16 1887973    /usr/lib/libgio-2.0.so.0.2200.2
002c9000-002ca000 rw-p 00000000 00:00 0 
002ca000-00310000 r-xp 00000000 08:16 1885771    /usr/lib/libpango-1.0.so.0.2600.0
00310000-00311000 r--p 00045000 08:16 1885771    /usr/lib/libpango-1.0.so.0.2600.0
00311000-00312000 rw-p 00046000 08:16 1885771    /usr/lib/libpango-1.0.so.0.2600.0
00312000-0038c000 r-xp 00000000 08:16 1884185    /usr/lib/libfreetype.so.6.3.20
0038c000-00390000 r--p 00079000 08:16 1884185    /usr/lib/libfreetype.so.6.3.20
00390000-00391000 rw-p 0007d000 08:16 1884185    /usr/lib/libfreetype.so.6.3.20
00391000-00393000 r-xp 00000000 08:16 2605803    /usr/lib/libXau.so.6.0.0
00393000-00394000 r--p 00001000 08:16 2605803    /usr/lib/libXau.so.6.0.0
00394000-00395000 rw-p 00002000 08:16 2605803    /usr/lib/libXau.so.6.0.0
00395000-00399000 r-xp 00000000 08:16 1885762    /usr/lib/libXdmcp.so.6.0.0
00399000-0039a000 rw-p 00003000 08:16 1885762    /usr/lib/libXdmcp.so.6.0.0
0039a000-0041e000 r-xp 00000000 08:16 1886688    /usr/lib/libcairo.so.2.10800.8
0041e000-00420000 r--p 00083000 08:16 1886688    /usr/lib/libcairo.so.2.10800.8
00420000-00421000 rw-p 00085000 08:16 1886688    /usr/lib/libcairo.so.2.10800.8
00421000-00424000 r-xp 00000000 08:16 1886990    /usr/lib/libcanberra-gtk.so.0.1.1
00424000-00425000 r--p 00002000 08:16 1886990    /usr/lib/libcanberra-gtk.so.0.1.1
00425000-00426000 rw-p 00003000 08:16 1886990    /usr/lib/libcanberra-gtk.so.0.1.1
00426000-00428000 rwxp 00000000 00:0f 1830       /dev/zero
00428000-00443000 r-xp 00000000 08:16 1885289    /usr/lib/libatk-1.0.so.0.2809.1
00443000-00444000 r--p 0001b000 08:16 1885289    /usr/lib/libatk-1.0.so.0.2809.1
00444000-00445000 rw-p 0001c000 08:16 1885289    /usr/lib/libatk-1.0.so.0.2809.1
00445000-0045a000 r-xp 00000000 08:16 3244054    /lib/tls/i686/cmov/libpthread-2.10.1.so
0045a000-0045b000 r--p 00014000 08:16 3244054    /lib/tls/i686/cmov/libpthread-2.10.1.so
0045b000-0045c000 rw-p 00015000 08:16 3244054    /lib/tls/i686/cmov/libpthread-2.10.1.so
0045c000-0045e000 rw-p 00000000 00:00 0 
0045e000-00467000 r-xp 00000000 08:16 1884179    /usr/lib/libXi.so.6.0.0
00467000-00468000 r--p 00008000 08:16 1884179    /usr/lib/libXi.so.6.0.0
00468000-00469000 rw-p 00009000 08:16 1884179    /usr/lib/libXi.so.6.0.0
00469000-0046b000 r-xp 00000000 08:16 655423     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
0046b000-0046c000 r--p 00001000 08:16 655423     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
0046c000-0046d000 rw-p 00002000 08:16 655423     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
0046d000-00485000 r-xp 00000000 08:16 8301       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00485000-00486000 r--p 00017000 08:16 8301       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00486000-00487000 rw-p 00018000 08:16 8301       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00487000-004b2000 r-xp 00000000 08:16 1887174    /usr/lib/libfontconfig.so.1.3.0
004b2000-004b3000 r--p 0002a000 08:16 1887174    /usr/lib/libfontconfig.so.1.3.0
004b3000-004b4000 rw-p 0002b000 08:16 1887174    /usr/lib/libfontconfig.so.1.3.0
004b4000-004cb000 r-xp 00000000 08:16 1887946    /usr/lib/libICE.so.6.3.0
004cb000-004cc000 r--p 00016000 08:16 1887946    /usr/lib/libICE.so.6.3.0
004cc000-004cd000 rw-p 00017000 08:16 1887946    /usr/lib/libICE.so.6.3.0
004cd000-004cf000 rw-p 00000000 00:00 0 Aborted (core dumped)
``` That was one instance. Here's another: ```
*** glibc detected *** /usr/bin/audacious2: double free or corruption (out): 0xb3c19710 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xbcaff1]
/lib/tls/i686/cmov/libc.so.6[0xbcc6f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xbcf79d]
/usr/bin/audacious2[0x805c0e6]
/usr/lib/audacious/Input/flacng.so(flac_play_file+0x33d)[0xae46ad]
/usr/bin/audacious2[0x805d23e]
/lib/libglib-2.0.so.0[0x22836f]
/lib/tls/i686/cmov/libpthread.so.0[0x58880e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xc2c7ee]
======= Memory map: ========
00110000-00117000 r-xp 00000000 08:16 3244056    /lib/tls/i686/cmov/librt-2.10.1.so
00117000-00118000 r--p 00006000 08:16 3244056    /lib/tls/i686/cmov/librt-2.10.1.so
00118000-00119000 rw-p 00007000 08:16 3244056    /lib/tls/i686/cmov/librt-2.10.1.so
00119000-00131000 r-xp 00000000 08:16 8301       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00131000-00132000 r--p 00017000 08:16 8301       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00132000-00133000 rw-p 00018000 08:16 8301       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00133000-0013e000 r-xp 00000000 08:16 1888363    /usr/lib/libpangocairo-1.0.so.0.2600.0
0013e000-0013f000 r--p 0000a000 08:16 1888363    /usr/lib/libpangocairo-1.0.so.0.2600.0
0013f000-00140000 rw-p 0000b000 08:16 1888363    /usr/lib/libpangocairo-1.0.so.0.2600.0
00140000-00143000 r-xp 00000000 08:16 1887970    /usr/lib/libgmodule-2.0.so.0.2200.2
00143000-00144000 r--p 00002000 08:16 1887970    /usr/lib/libgmodule-2.0.so.0.2200.2
00144000-00145000 rw-p 00003000 08:16 1887970    /usr/lib/libgmodule-2.0.so.0.2200.2
00145000-00147000 r-xp 00000000 08:16 1887884    /usr/lib/libXcomposite.so.1.0.0
00147000-00148000 r--p 00001000 08:16 1887884    /usr/lib/libXcomposite.so.1.0.0
00148000-00149000 rw-p 00002000 08:16 1887884    /usr/lib/libXcomposite.so.1.0.0
00149000-0014a000 r-xp 00000000 08:16 2187480    /usr/lib/tls/libnvidia-tls.so.185.18.36
0014a000-0014b000 rw-p 00000000 08:16 2187480    /usr/lib/tls/libnvidia-tls.so.185.18.36
0014b000-00172000 r-xp 00000000 08:16 1888365    /usr/lib/libpangoft2-1.0.so.0.2600.0
00172000-00173000 r--p 00027000 08:16 1888365    /usr/lib/libpangoft2-1.0.so.0.2600.0
00173000-00174000 rw-p 00028000 08:16 1888365    /usr/lib/libpangoft2-1.0.so.0.2600.0
00174000-00198000 r-xp 00000000 08:16 3244042    /lib/tls/i686/cmov/libm-2.10.1.so
00198000-00199000 r--p 00023000 08:16 3244042    /lib/tls/i686/cmov/libm-2.10.1.so
00199000-0019a000 rw-p 00024000 08:16 3244042    /lib/tls/i686/cmov/libm-2.10.1.so
0019a000-001b6000 r-xp 00000000 08:16 1885859    /usr/lib/libdbus-glib-1.so.2.1.0
001b6000-001b7000 r--p 0001b000 08:16 1885859    /usr/lib/libdbus-glib-1.so.2.1.0
001b7000-001b8000 rw-p 0001c000 08:16 1885859    /usr/lib/libdbus-glib-1.so.2.1.0
001b8000-001bc000 r-xp 00000000 08:16 1886156    /usr/lib/libXfixes.so.3.1.0
001bc000-001bd000 r--p 00003000 08:16 1886156    /usr/lib/libXfixes.so.3.1.0
001bd000-001be000 rw-p 00004000 08:16 1886156    /usr/lib/libXfixes.so.3.1.0
001be000-001c0000 r-xp 00000000 08:16 3244041    /lib/tls/i686/cmov/libdl-2.10.1.so
001c0000-001c1000 r--p 00001000 08:16 3244041    /lib/tls/i686/cmov/libdl-2.10.1.so
001c1000-001c2000 rw-p 00002000 08:16 3244041    /lib/tls/i686/cmov/libdl-2.10.1.so
001c2000-001c3000 r-xp 00000000 08:16 2474710    /usr/lib/audacious/Effect/voice_removal.so
001c3000-001c4000 r--p 00000000 08:16 2474710    /usr/lib/audacious/Effect/voice_removal.so
001c4000-001c5000 rw-p 00001000 08:16 2474710    /usr/lib/audacious/Effect/voice_removal.so
001c5000-00279000 r-xp 00000000 08:16 2728052    /lib/libglib-2.0.so.0.2200.2
00279000-0027a000 r--p 000b4000 08:16 2728052    /lib/libglib-2.0.so.0.2200.2
0027a000-0027b000 rw-p 000b5000 08:16 2728052    /lib/libglib-2.0.so.0.2200.2
0027b000-002a6000 r-xp 00000000 08:16 1887174    /usr/lib/libfontconfig.so.1.3.0
002a6000-002a7000 r--p 0002a000 08:16 1887174    /usr/lib/libfontconfig.so.1.3.0
002a7000-002a8000 rw-p 0002b000 08:16 1887174    /usr/lib/libfontconfig.so.1.3.0
002a8000-002b4000 r-xp 00000000 08:16 1887364    /usr/lib/libmowgli.so.1.0.0
002b4000-002b6000 rw-p 0000b000 08:16 1887364    /usr/lib/libmowgli.so.1.0.0
002b6000-002b9000 r-xp 00000000 08:16 1886523    /usr/lib/libxcb-render-util.so.0.0.0
002b9000-002ba000 r--p 00002000 08:16 1886523    /usr/lib/libxcb-render-util.so.0.0.0
002ba000-002bb000 rw-p 00003000 08:16 1886523    /usr/lib/libxcb-render-util.so.0.0.0
002bb000-002c1000 r-xp 00000000 08:16 1887297    /usr/lib/libSAD.so.2.0.0
002c1000-002c2000 r--p 00005000 08:16 1887297    /usr/lib/libSAD.so.2.0.0
002c2000-002c3000 rw-p 00006000 08:16 1887297    /usr/lib/libSAD.so.2.0.0
002c3000-00356000 r-xp 00000000 08:16 1887973    /usr/lib/libgio-2.0.so.0.2200.2
00356000-00357000 r--p 00092000 08:16 1887973    /usr/lib/libgio-2.0.so.0.2200.2
00357000-00358000 rw-p 00093000 08:16 1887973    /usr/lib/libgio-2.0.so.0.2200.2
00358000-00359000 rw-p 00000000 00:00 0 
00359000-0039f000 r-xp 00000000 08:16 1885771    /usr/lib/libpango-1.0.so.0.2600.0
0039f000-003a0000 r--p 00045000 08:16 1885771    /usr/lib/libpango-1.0.so.0.2600.0
003a0000-003a1000 rw-p 00046000 08:16 1885771    /usr/lib/libpango-1.0.so.0.2600.0
003a1000-0041b000 r-xp 00000000 08:16 1884185    /usr/lib/libfreetype.so.6.3.20
0041b000-0041f000 r--p 00079000 08:16 1884185    /usr/lib/libfreetype.so.6.3.20
0041f000-00420000 rw-p 0007d000 08:16 1884185    /usr/lib/libfreetype.so.6.3.20
00420000-00457000 r-xp 00000000 08:16 2728042    /lib/libdbus-1.so.3.4.0
00457000-00458000 r--p 00036000 08:16 2728042    /lib/libdbus-1.so.3.4.0
00458000-00459000 rw-p 00037000 08:16 2728042    /lib/libdbus-1.so.3.4.0
00459000-00470000 r-xp 00000000 08:16 1887946    /usr/lib/libICE.so.6.3.0
00470000-00471000 r--p 00016000 08:16 1887946    /usr/lib/libICE.so.6.3.0
00471000-00472000 rw-p 00017000 08:16 1887946    /usr/lib/libICE.so.6.3.0
00472000-00474000 rw-p 00000000 00:00 0 
00474000-00482000 r-xp 00000000 08:16 1884162    /usr/lib/libXext.so.6.4.0
00482000-00483000 r--p 0000d000 08:16 1884162    /usr/lib/libXext.so.6.4.0
00483000-00484000 rw-p 0000e000 08:16 1884162    /usr/lib/libXext.so.6.4.0
00484000-0048c000 r-xp 00000000 08:16 1887745    /usr/lib/libXrender.so.1.3.0
0048c000-0048d000 r--p 00007000 08:16 1887745    /usr/lib/libXrender.so.1.3.0
0048d000-0048e000 rw-p 00008000 08:16 1887745    /usr/lib/libXrender.so.1.3.0
0048e000-00495000 r-xp 00000000 08:16 1885773    /usr/lib/libXrandr.so.2.2.0
00495000-00496000 r--p 00006000 08:16 1885773    /usr/lib/libXrandr.so.2.2.0
00496000-00497000 rw-p 00007000 08:16 1885773    /usr/lib/libXrandr.so.2.2.0Aborted (core dumped)

```I noticed that every time I attempted to play the file, the debug output would differ slightly (specifically, the memory map). In one instance, Audacious opened the file, played it at a higher pitch than normal for a few seconds, then segfaulted. Later, I tried removing all the Audacious binaries and configuration files (by running apt-get purge audacious2), and compiled from source (I only compiled the Audacious binary itself; version is the same as the repository's, 2.1). However, the binary I compiled gave this: ```
audacious2: unable to launch selected interface skinned
``` when I tried to start it up. I tried giving it the switches "-i newui", "-i gtkui", and "-i headless"; it didn't help, either. There doesn't seem to be any mention of this behavior on the Audacious forums. Can anyone tell me what I overlooked?

UPDATE: compiled the beta version (version 2.2) and its plugins; didn't work either (still gives "audacious2: unable to launch selected interface skinned" error)

UPDATE: it seems that the getdeb.net packagers have packaged a version 2.2 Audacious which works

---

