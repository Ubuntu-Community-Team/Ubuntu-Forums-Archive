---
title: "Klavaro crashes before starting"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by naomibrown on 2010-04-12
Hi,

I've just installed Klavaro, to learn how to type better, and I have installed it but every time I start it the program briefly flashes in the bottom panel, but then disappears again. 

Any ideas?

Thanks,
Naomi

---

### Post by enceladus47 on 2010-04-12
I had the very same problem a while back and managed to solve it but don't really remember how:oops:, but I remember some of the stuff I tried.

Try opening the terminal then typing klavaro I think it will tell you some packages are missing or something, tell me the output.

---

### Post by naomibrown on 2010-04-13
I've just tried that and I got the following

```
*** glibc detected *** klavaro: double free or corruption (fasttop): 0x096f18e0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x2445ff1]
/lib/tls/i686/cmov/libc.so.6[0x24476f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x244a7cd]
/lib/libglib-2.0.so.0(g_free+0x36)[0x390196]
klavaro(trans_init_language_env+0xee)[0x80572be]
klavaro(main_initialize_global_variables+0x165)[0x8051a25]
klavaro(main+0x78)[0x8052438]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x23f1b56]
klavaro[0x8051741]
======= Memory map: ========
00110000-0011f000 r-xp 00000000 08:05 3612       /usr/lib/libsexy.so.2.0.4
0011f000-00120000 r--p 0000f000 08:05 3612       /usr/lib/libsexy.so.2.0.4
00120000-00121000 rw-p 00010000 08:05 3612       /usr/lib/libsexy.so.2.0.4
00121000-001b3000 r-xp 00000000 08:05 6078       /usr/lib/libgdk-x11-2.0.so.0.1800.3
001b3000-001b5000 r--p 00092000 08:05 6078       /usr/lib/libgdk-x11-2.0.so.0.1800.3
001b5000-001b6000 rw-p 00094000 08:05 6078       /usr/lib/libgdk-x11-2.0.so.0.1800.3
001b6000-0022d000 r-xp 00000000 08:05 566        /usr/lib/libcairo.so.2.10800.8
0022d000-0022f000 r--p 00076000 08:05 566        /usr/lib/libcairo.so.2.10800.8
0022f000-00230000 rw-p 00078000 08:05 566        /usr/lib/libcairo.so.2.10800.8
00230000-00276000 r-xp 00000000 08:05 3488       /usr/lib/libpango-1.0.so.0.2600.0
00276000-00277000 r--p 00045000 08:05 3488       /usr/lib/libpango-1.0.so.0.2600.0
00277000-00278000 rw-p 00046000 08:05 3488       /usr/lib/libpango-1.0.so.0.2600.0
00278000-002a8000 r-xp 00000000 08:05 3332       /usr/lib/libidn.so.11.5.44
002a8000-002a9000 ---p 00030000 08:05 3332       /usr/lib/libidn.so.11.5.44
002a9000-002aa000 r--p 00030000 08:05 3332       /usr/lib/libidn.so.11.5.44
002aa000-002ab000 rw-p 00031000 08:05 3332       /usr/lib/libidn.so.11.5.44
002ab000-002ad000 r-xp 00000000 08:05 2730       /usr/lib/libXdamage.so.1.1.0
002ad000-002ae000 rw-p 00001000 08:05 2730       /usr/lib/libXdamage.so.1.1.0
002ae000-002d2000 r-xp 00000000 08:05 394187     /lib/tls/i686/cmov/libm-2.10.1.so
002d2000-002d3000 r--p 00023000 08:05 394187     /lib/tls/i686/cmov/libm-2.10.1.so
002d3000-002d4000 rw-p 00024000 08:05 394187     /lib/tls/i686/cmov/libm-2.10.1.so
002d4000-00310000 r-xp 00000000 08:05 1781       /usr/lib/libgobject-2.0.so.0.2200.3
00310000-00311000 r--p 0003b000 08:05 1781       /usr/lib/libgobject-2.0.so.0.2200.3
00311000-00312000 rw-p 0003c000 08:05 1781       /usr/lib/libgobject-2.0.so.0.2200.3
00312000-0031f000 r-xp 00000000 08:05 3366       /usr/lib/liblber-2.4.so.2.5.1
0031f000-00320000 r--p 0000c000 08:05 3366       /usr/lib/liblber-2.4.so.2.5.1
00320000-00321000 rw-p 0000d000 08:05 3366       /usr/lib/liblber-2.4.so.2.5.1
00321000-00323000 r-xp 00000000 08:05 2726       /usr/lib/libXcomposite.so.1.0.0
00323000-00324000 r--p 00001000 08:05 2726       /usr/lib/libXcomposite.so.1.0.0
00324000-00325000 rw-p 00002000 08:05 2726       /usr/lib/libXcomposite.so.1.0.0
00325000-0032d000 r-xp 00000000 08:05 2756       /usr/lib/libXrender.so.1.3.0
0032d000-0032e000 r--p 00007000 08:05 2756       /usr/lib/libXrender.so.1.3.0
0032e000-0032f000 rw-p 00008000 08:05 2756       /usr/lib/libXrender.so.1.3.0
0032f000-00331000 r-xp 00000000 08:05 2744       /usr/lib/libXinerama.so.1.0.0
00331000-00332000 rw-p 00001000 08:05 2744       /usr/lib/libXinerama.so.1.0.0
00332000-0034d000 r-xp 00000000 08:05 2805       /usr/lib/libatk-1.0.so.0.2809.1
0034d000-0034e000 r--p 0001b000 08:05 2805       /usr/lib/libatk-1.0.so.0.2809.1
0034e000-0034f000 rw-p 0001c000 08:05 2805       /usr/lib/libatk-1.0.so.0.2809.1
0034f000-00404000 r-xp 00000000 08:05 832        /lib/libglib-2.0.so.0.2200.3
00404000-00405000 r--p 000b4000 08:05 832        /lib/libglib-2.0.so.0.2200.3
00405000-00406000 rw-p 000b5000 08:05 832        /lib/libglib-2.0.so.0.2200.3
00406000-0042e000 r-xp 00000000 08:05 5772       /usr/lib/libgssapi_krb5.so.2.2
0042e000-0042f000 r--p 00027000 08:05 5772       /usr/lib/libgssapi_krb5.so.2.2
0042f000-00430000 rw-p 00028000 08:05 5772       /usr/lib/libgssapi_krb5.so.2.2
00430000-00444000 r-xp 00000000 08:05 673        /lib/libz.so.1.2.3.3
00444000-00445000 r--p 00013000 08:05 673        /lib/libz.so.1.2.3.3
00445000-00446000 rw-p 00014000 08:05 673        /lib/libz.so.1.2.3.3
00446000-004bf000 r-xp 00000000 08:05 573        /lib/libgcrypt.so.11.5.2
004bf000-004c0000 r--p 00078000 08:05 573        /lib/libgcrypt.so.11.5.2
004c0000-004c2000 rw-p 00079000 08:05 573        /lib/libgcrypt.so.11.5.2
004c2000-004d0000 r-xp 00000000 08:05 2734       /usr/lib/libXext.so.6.4.0
004d0000-004d1000 r--p 0000d000 08:05 2734       /usr/lib/libXext.so.6.4.0
004d1000-004d2000 rw-p 0000e000 08:05 2734       /usr/lib/libXext.so.6.4.0
004d5000-004e7000 r-xp 00000000 08:05 69         /usr/lib/libgtkdatabox-0.9.0.so.1.0.0
004e7000-004e8000 r--p 00011000 08:05 69         /usr/lib/libgtkdatabox-0.9.0.so.1.0.0
004e8000-004e9000 rw-p 00012000 08:05 69         /usr/lib/libgtkdatabox-0.9.0.so.1.0.0
004e9000-004f2000 r-xp 00000000 08:05 2742       /usr/lib/libXi.so.6.0.0
004f2000-004f3000 r--p 00008000 08:05 2742       /usr/lib/libXi.so.6.0.0
004f3000-004f4000 rw-p 00009000 08:05 2742       /usr/lib/libXi.so.6.0.0
004f4000-004fd000 r-xp 00000000 08:05 2728       /usr/lib/libXcursor.so.1.0.2
004fd000-004fe000 r--p 00008000 08:05 2728       /usr/lib/libXcursor.so.1.0.2
004fe000-004ff000 rw-p 00009000 08:05 2728       /usr/lib/libXcursor.so.1.0.2
004ff000-00501000 r-xp 00000000 08:05 394186     /lib/tls/i686/cmov/libdl-2.10.1.so
00501000-00502000 r--p 00001000 08:05 394186     /lib/tls/i686/cmov/libdl-2.10.1.so
00502000-00503000 rw-p 00002000 08:05 394186     /lib/tls/i686/cmov/libdl-2.10.1.so
00503000-0050b000 r-xp 00000000 08:05 3031       /usr/lib/libfusion-1.2.so.0.7.0
0050b000-0050c000 r--p 00007000 08:05 3031       /usr/lib/libfusion-1.2.so.0.7.0
0050c000-0050d000 rw-p 00008000 08:05 3031       /usr/lib/libfusion-1.2.so.0.7.0
0050d000-00510000 r-xp 00000000 08:05 3749       /usr/lib/libxcb-render-util.so.0.0.0
00510000-00511000 r--p 00002000 08:05 3749       /usr/lib/libxcb-render-util.so.0.0.0
00511000-00512000 rw-p 00003000 08:05 3749       /usr/lib/libxcb-render-util.so.0.0.0
00512000-00519000 r-xp 00000000 08:05 3751       /usr/lib/libxcb-render.so.0.0.0
00519000-0051a000 r--p 00007000 08:05 3751       /usr/lib/libxcb-render.so.0.0.0
0051a000-0051b000 rw-p 00008000 08:05 3751       /usr/lib/libxcb-render.so.0.0.0
0051b000-00533000 r-xp 00000000 08:05 6122       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00533000-00534000 r--p 00017000 08:05 6122       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00534000-00535000 rw-p 00018000 08:05 6122       /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00535000-00564000 r-xp 00000000 08:05 626        /lib/libpcre.so.3.12.1
00564000-00565000 r--p 0002e000 08:05 626        /lib/libpcre.so.3.12.1
00565000-00566000 rw-p 0002f000 08:05 626        /lib/libpcre.so.3.12.1
00566000-00569000 r-xp 00000000 08:05 2551       /usr/lib/libgmodule-2.0.so.0.2200.3
00569000-0056a000 r--p 00002000 08:05 2551       /usr/lib/libgmodule-2.0.so.0.2200.3
0056a000-0056b000 rw-p 00003000 08:05 2551       /usr/lib/libgmodule-2.0.so.0.2200.3
0056b000-0056d000 r-xp 00000000 08:05 552        /lib/libcom_err.so.2.1
0056d000-0056e000 r--p 00001000 08:05 552        /lib/libcom_err.so.2.1Aborted

```

---

### Post by enceladus47 on 2010-04-14
Sorry but not really sure what to do next, I searched for a while and the problem I had involved missing gtk+ files, but I don't think it's the case here.

You can try uninstalling klavaro and installing a previous version from here [http://sourceforge.net/projects/klavaro/files/](http://sourceforge.net/projects/klavaro/files/). Version 1.3.1 has a debian package which is easy to install, but not sure installing a previous version would solve the problem.

---

