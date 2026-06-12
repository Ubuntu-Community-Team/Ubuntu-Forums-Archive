---
title: "Downloaded program not accessible"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by RemmeltM on 2009-08-02
Hi,

I recently installed Ubuntu 9.04. It is working fine. I am a photographer so I need a program for my photos. Bibble5 will be my choice, also because they have a Linux version. I downloaded it (a .deb file). Installation went fine. It is listed in the menu Applications-Graphical. However clicking on the icon the program gives no reaction, It will not run.
If I go the location were the program is installed (Filesystem/opt) it says that I do not have rights for that program.

Where did I go wrong and what can I do to make it work !!

Thanks for reading,

Remmelt

---

### Post by pedro3005 on 2009-08-02
Try clicking Applications, Accessories, Terminal. Run 'sudo bibble5' and type your password. If it runs, great: Right click Applications, Edit Menus. Find the icon for Bibble5, edit it, and at the beginning of the command include a 'sudo'. If it says something like 'bibble5: command not found' then bibble5 is the wrong command. To know the right one, right click Applications, Edit Menus. Find the icon for Bibble5, click edit, and post the command it runs for us :)

Hope what I wrote was understandable to you, if not, post and i (or someone else) will explain better.

---

### Post by gorgon on 2009-08-02
> Find the icon for Bibble5, edit it, and at the beginning of the command include a 'sudo'.

I think the 'sudo' should be a 'gksudo' when used in the graphic environment?

---

### Post by SunnyRabbiera on 2009-08-02
Fspot seems to do the same basic job

---

### Post by doas777 on 2009-08-02
first, I would test the application. go to Applications -> Accessories -> Terminal and paste in:
```
gksu <program-name>
```gksu causes the application following it to be run as admin. when you call it, it will prompt you for your password. 

one of two things will happen. either an error message will appear in the terminal, or the application will start.

if the app starts, just use pedro's instructions to add gksu to the begining of the command for the launcher (shortcut). use gksu instead of sudo though, since sudo is for command line applications.

if the app doesn;t start, hopefully the error message will provide a clue as to the problem.

---

### Post by RemmeltM on 2009-08-02
Hi,

Thanks a lot. However I get the following after typing gksudo bibble5pro:

remmelt@remmelt-desktop:~$ gksudo bibble5pro
Using existing Pictures folder
Install Path:  /opt/bibble5pro
LD_PATH:       /opt/bibble5pro/lib:
    linux-gate.so.1 =>  (0xb7f14000)
    libkodakcms.so => /opt/bibble5pro/lib/libkodakcms.so (0xb7e98000)
    libuuid.so.1 => /opt/bibble5pro/lib/libuuid.so.1 (0x0070c000)
    libtcmalloc.so.0 => /opt/bibble5pro/lib/libtcmalloc.so.0 (0xb7e52000)
    libQtScript.so.4 => /opt/bibble5pro/lib/libQtScript.so.4 (0xb7d31000)
    libQtSvg.so.4 => /opt/bibble5pro/lib/libQtSvg.so.4 (0xb7ce5000)
    libQt3Support.so.4 => /opt/bibble5pro/lib/libQt3Support.so.4 (0xb7a00000)
    libQtSql.so.4 => /opt/bibble5pro/lib/libQtSql.so.4 (0xb7967000)
    libQtOpenGL.so.4 => /opt/bibble5pro/lib/libQtOpenGL.so.4 (0xb78f1000)
    libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb786f000)
    libGL.so.1 => /usr/lib/libGL.so.1 (0xb77b5000)
    libQtNetwork.so.4 => /opt/bibble5pro/lib/libQtNetwork.so.4 (0xb76b9000)
    libQtDesigner.so.4 => /opt/bibble5pro/lib/libQtDesigner.so.4 (0xb73dd000)
    libQtXml.so.4 => /opt/bibble5pro/lib/libQtXml.so.4 (0xb7397000)
    libQtGui.so.4 => /opt/bibble5pro/lib/libQtGui.so.4 (0xb6aaf000)
    libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6a89000)
    libSM.so.6 => /usr/lib/libSM.so.6 (0xb6a80000)
    libICE.so.6 => /usr/lib/libICE.so.6 (0xb6a68000)
    libXi.so.6 => /usr/lib/libXi.so.6 (0xb6a5e000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb6a53000)
    libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6a4b000)
    libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb69d4000)
    libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb69a7000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0xb6997000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0xb68a7000)
    libQtCore.so.4 => /opt/bibble5pro/lib/libQtCore.so.4 (0xb6682000)
    libz.so.1 => /lib/libz.so.1 (0xb666c000)
    libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb6666000)
    librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb665d000)
    libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb65a5000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb65a0000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb6587000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb6498000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6472000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6463000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb62ff000)
    /lib/ld-linux.so.2 (0xb7f15000)
    libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb53e7000)
    libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb53e5000)
    libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb53bd000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0xb53b9000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb539f000)
    libpcre.so.3 => /lib/libpcre.so.3 (0xb536d000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb5368000)
*** glibc detected *** ./bibblepro: free(): invalid pointer: 0x09623f00 ***======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb64b3604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb64b55b6]
/usr/lib/tls/libnvidia-tls.so.1[0xb552aaa0]
======= Memory map: ========
0070c000-0070f000 r-xp 00000000 08:05 1259321    /opt/bibble5pro/lib/libuuid.so
0070f000-00710000 rwxp 00002000 08:05 1259321    /opt/bibble5pro/lib/libuuid.so
08048000-08cf3000 r-xp 00000000 08:05 1259332    /opt/bibble5pro/bin/bibblepro
08cf3000-08d0c000 rwxp 00cab000 08:05 1259332    /opt/bibble5pro/bin/bibblepro
08d0c000-08d31000 rwxp 08d0c000 00:00 0 
095a0000-09720000 rwxp 095a0000 00:00 0          [heap]
b54aa000-b54ad000 rwxp b54aa000 00:00 0 
b54ad000-b54b1000 r-xp 00000000 08:05 1973078    /usr/lib/libXdmcp.so.6.0.0
b54b1000-b54b2000 rwxp 00003000 08:05 1973078    /usr/lib/libXdmcp.so.6.0.0
b54b2000-b54e2000 r-xp 00000000 08:05 417010     /lib/libpcre.so.3.12.1
b54e2000-b54e3000 r-xp 0002f000 08:05 417010     /lib/libpcre.so.3.12.1
b54e3000-b54e4000 rwxp 00030000 08:05 417010     /lib/libpcre.so.3.12.1
b54e4000-b54fc000 r-xp 00000000 08:05 1972263    /usr/lib/libxcb.so.1.1.0
b54fc000-b54fd000 r-xp 00017000 08:05 1972263    /usr/lib/libxcb.so.1.1.0
b54fd000-b54fe000 rwxp 00018000 08:05 1972263    /usr/lib/libxcb.so.1.1.0
b54fe000-b5500000 r-xp 00000000 08:05 1972261    /usr/lib/libXau.so.6.0.0
b5500000-b5501000 r-xp 00001000 08:05 1972261    /usr/lib/libXau.so.6.0.0
b5501000-b5502000 rwxp 00002000 08:05 1972261    /usr/lib/libXau.so.6.0.0
b5502000-b5526000 r-xp 00000000 08:05 1973320    /usr/lib/libexpat.so.1.5.2
b5526000-b5528000 r-xp 00023000 08:05 1973320    /usr/lib/libexpat.so.1.5.2
b5528000-b5529000 rwxp 00025000 08:05 1973320    /usr/lib/libexpat.so.1.5.2
b5529000-b552a000 rwxp b5529000 00:00 0 
b552a000-b552b000 r-xp 00000000 08:05 2004356    /usr/lib/tls/libnvidia-tls.so.180.44
b552b000-b552c000 rwxp 00000000 08:05 2004356    /usr/lib/tls/libnvidia-tls.so.180.44
b552c000-b6246000 r-xp 00000000 08:05 1971605    /usr/lib/libGLcore.so.180.44
b6246000-b6438000 rwxp 00d19000 08:05 1971605    /usr/lib/libGLcore.so.180.44
b6438000-b6444000 rwxp b6438000 00:00 0 
b6444000-b65a0000 r-xp 00000000 08:05 436702     /lib/tls/i686/cmov/libc-2.9.so
b65a0000-b65a1000 ---p 0015c000 08:05 436702     /lib/tls/i686/cmov/libc-2.9.so
b65a1000-b65a3000 r-xp 0015c000 08:05 436702     /lib/tls/i686/cmov/libc-2.9.so
b65a3000-b65a4000 rwxp 0015e000 08:05 436702     /lib/tls/i686/cmov/libc-2.9.so
b65a4000-b65a8000 rwxp b65a4000 00:00 0 
b65a8000-b65b5000 r-xp 00000000 08:05 416997     /lib/libgcc_s.so.1
b65b5000-b65b6000 r-xp 0000c000 08:05 416997     /lib/libgcc_s.so.1
b65b6000-b65b7000 rwxp 0000d000 08:05 416997     /lib/libgcc_s.so.1
b65b7000-b65db000 r-xp 00000000 08:05 437149     /lib/tls/i686/cmov/libm-2.9.so
b65db000-b65dc000 r-xp 00023000 08:05 437149     /lib/tls/i686/cmov/libm-2.9.so
b65dc000-b65dd000 rwxp 00024000 08:05 437149     /lib/tls/i686/cmov/libm-2.9.so
b65dd000-b66c1000 r-xp 00000000 08:05 1970523    /usr/lib/libstdc++.so.6.0.10
b66c1000-b66c5000 r-xp 000e3000 08:05 1970523    /usr/lib/libstdc++.so.6.0.10
b66c5000-b66c6000 rwxp 000e7000 08:05 1970523    /usr/lib/libstdc++.so.6.0.10
b66c6000-b66cc000 rwxp b66c6000 00:00 0 
b66cc000-b66e1000 r-xp 00000000 08:05 440987     /lib/tls/i686/cmov/libpthread-2.9.so
b66e1000-b66e2000 r-xp 00014000 08:05 440987     /lib/tls/i686/cmov/libpthread-2.9.so
b66e2000-b66e3000 rwxp 00015000 08:05 440987     /lib/tls/i686/cmov/libpthread-2.9.so
b66e3000-b66e5000 rwxp b66e3000 00:00 0 
b66e5000-b66e7000 r-xp 00000000 08:05 437145     /lib/tls/i686/cmov/libdl-2.9.so
b66e7000-b66e8000 r-xp 00001000 08:05 437145     /lib/tls/i686/cmov/libdl-2.9.so
b66e8000-b66e9000 rwxp 00002000 08:05 437145     /lib/tls/i686/cmov/libdl-2.9.so
b66e9000-b66ea000 rwxp b66e9000 00:00 0 
b66ea000-b67a0000 r-xp 00000000 08:05 1971635    /usr/lib/libglib-2.0.so.0.2000.1
b67a0000-b67a1000 r-xp 000b5000 08:05 1971635    /usr/lib/libglib-2.0.so.0.2000.1
b67a1000-b67a2000 rwxp 000b6000 08:05 1971635    /usr/lib/libglib-2.0.so.0.2000.1
b67a2000-b67a9000 r-xp 00000000 08:05 440993     /lib/tls/i686/cmov/librt-2.9.so
b67a9000-b67aa000 r-xp 00006000 08:05 440993     /lib/tls/i686/cmov/librt-2.9.so
b67aa000-b67ab000 rwxp 00007000 08:05 440993     /lib/tls/i686/cmov/librt-2.9.so
b67ab000-b67af000 r-xp 00000000 08:05 1973457    /usr/lib/libgthread-2.0.so.0.2000.1
b67af000-b67b0000 r-xp 00003000 08:05 1973457    /usr/lib/libgthread-2.0.so.0.2000.1
b67b0000-b67b1000 rwxp 00004000 08:05 1973457    /usr/lib/libgthread-2.0.so.0.2000.1
b67b1000-b67c5000 r-xp 00000000 08:05 416999     /lib/libz.so.1.2.3.3
b67c5000-b67c6000 r-xp 00013000 08:05 416999     /lib/libz.so.1.2.3.3
b67c6000-b67c7000 rwxp 00014000 08:05 416999     /lib/libz.so.1.2.3.3
b67c7000-b69e4000 r-xp 00000000 08:05 1259327    /opt/bibble5pro/lib/libQtCore.so.4
b69e4000-b69eb000 rwxp 0021d000 08:05 1259327    /opt/bibble5pro/lib/libQtCore.so.4
b69eb000-b69ec000 rwxp b69eb000 00:00 0 
b69ec000-b6ad6000 r-xp 00000000 08:05 1972259    /usr/lib/libX11.so.6.2.0
b6ad6000-b6ad7000 ---p 000ea000 08:05 1972259    /usr/lib/libX11.so.6.2.0
b6ad7000-b6ad8000 r-xp 000ea000 08:05 1972259    /usr/lib/libX11.so.6.2.0
b6ad8000-b6ada000 rwxp 000eb000 08:05 1972259    /usr/lib/libX11.so.6.2.0
b6ada000-b6adc000 rwxp b6ada000 00:00 0 
b6adc000-b6aea000 r-xp 00000000 08:05 1970557    /usr/lib/libXext.so.6.4.0
b6aea000-b6aeb000 r-xp 0000d000 08:05 1970557    /usr/lib/libXext.so.6.4.0
b6aeb000-b6aec000 rwxp 0000e000 08:05 1970557    /usr/lib/libXext.so.6.4.0
b6aec000-b6b17000 r-xp 00000000 08:05 1972123    /usr/lib/libfontconfig.so.1.3.0
b6b17000-b6b18000 r-xp 0002a000 08:05 1972123    /usr/lib/libfontconfig.so.1.3.0
b6b18000-b6b19000 rwxp 0002b000 08:05 1972123    /usr/lib/libfontconfig.so.1.3.0
b6b19000-b6b8b000 r-xp 00000000 08:05 1972119    /usr/lib/libfreetype.so.6.3.20
b6b8b000-b6b8f000 r-xp 00071000 08:05 1972119    /usr/lib/libfreetype.so.6.3.20
b6b8f000-b6b90000 rwxp 00075000 08:05 1972119    /usr/lib/libfreetype.so.6.3.20
b6b90000-b6b96000 r-xp 00000000 08:05 1971357    /usr/lib/libXrandr.so.2.2.0
b6b96000-b6b97000 r-xp 00006000 08:05 1971357    /usr/lib/libXrandr.so.2.2.0
b6b97000-b6b98000 rwxp 00007000 08:05 1971357    /usr/lib/libXrandr.so.2.2.0
b6b98000-b6ba0000 r-xp 00000000 08:05 1973104    /usr/lib/libXrender.so.1.3.0
b6ba0000-b6ba1000 r-xp 00007000 08:05 1973104    /usr/lib/libXrender.so.1.3.0
b6ba1000-b6ba2000 rwxp 00008000 08:05 1973104    /usr/lib/libXrender.so.1.3.0
b6ba2000-b6ba3000 rwxp b6ba2000 00:00 0 
b6ba3000-b6bab000 r-xp 00000000 08:05 1971153    /usr/lib/libXi.so.6.0.0
b6bab000-b6bac000 r-xp 00007000 08:05 1971153    /usr/lib/libXi.so.6.0.0
b6bac000-b6bad000 rwxp 00008000 08:05 1971153    /usr/lib/libXi.so.6.0.0
b6bad000-b6bc2000 r-xp 00000000 08:05 1973026    /usr/lib/libICE.so.6.3.0
b6bc2000-b6bc3000 rwxp 00014000 08:05 1973026    /usr/lib/libICE.so.6.3.0
b6bc3000-b6bc5000 rwxp b6bc3000 00:00 0 
b6bc5000-b6bcc000 r-xp 00000000 08:05 1970543    /usr/lib/libSM.so.6.0.0
b6bcc000-b6bcd000 r-xp 00006000 08:05 1970543    /usr/lib/libSM.so.6.0.0
b6bcd000-b6bce000 rwxp 00007000 08:05 1970543    /usr/lib/libSM.so.6.0.0
b6bce000-b6bf2000 r-xp 00000000 08:05 1972257    /usr/lib/libpng12.so.0.27.0
b6bf2000-b6bf3000 r-xp 00023000 08:05 1972257    /usr/lib/libpng12.so.0.27.0
b6bf3000-b6bf4000 rwxp 00024000 08:05 1972257    /usr/lib/libpng12.so.0.27.0
b6bf4000-b74b6000 r-xp 00000000 08:05 1259328    /opt/bibble5pro/lib/libQtGui.so.4
b74b6000-b74db000 rwxp 008c1000 08:05 1259328    /opt/bibble5pro/lib/libQtGui.so.4
b74db000-b74dc000 rwxp b74db000 00:00 0 
b74dc000-b751f000 r-xp 00000000 08:05 1259316    /opt/bibble5pro/lib/libQtXml.so.4
b751f000-b7521000 rwxp 00042000 08:05 1259316    /opt/bibble5pro/lib/libQtXml.so.4
b7521000-b7522000 rwxp b7521000 00:00 0 
b7522000-b77f1000 r-xp 00000000 08:05 1259323    /opt/bibble5pro/lib/libQtDesigner.so.4
b77f1000-b77fe000 rwxp 002cf000 08:05 1259323    /opt/bibble5pro/lib/libQtDesigner.so.4
b77fe000-b78f6000 r-xp 00000000 08:05 1259325    /opt/bibble5pro/lib/libQtNetwork.so.4
b78f6000-b78fa000 rwxp 000f7000 08:05 1259325    /opt/bibble5pro/lib/libQtNetwork.so.4
b78fa000-b7987000 r-xp 00000000 08:05 1971593    /usr/lib/libGL.so.180.44
b7987000-b79a5000 rwxp 0008d000 08:05 1971593    /usr/lib/libGL.so.180.44
b79a5000-b79b4000 rwxp b79a5000 00:00 0 
b79b4000-b7a23000 r-xp 00000000 08:05 1970671    /usr/lib/libGLU.so.1.3.070300
b7a23000-b7a24000 ---p 0006f000 08:05 1970671    /usr/lib/libGLU.so.1.3.070300
b7a24000-b7a25000 r-xp 0006f000 08:05 1970671    /usr/lib/libGLU.so.1.3.070300
b7a25000-b7a26000 rwxp 00070000 08:05 1970671    /usr/lib/libGLU.so.1.3.070300
b7a34000-b7a36000 rwxp 00000000 00:0f 745        /dev/zero
b7a36000-b7aa6000 r-xp 00000000 08:05 1259319    /opt/bibble5pro/lib/libQtOpenGL.so.4
b7aa6000-b7aab000 rwxp 0006f000 08:05 1259319    /opt/bibble5pro/lib/libQtOpenGL.so.4
b7aab000-b7aac000 rwxp b7aab000 00:00 0 
b7aac000-b7b42000 r-xp 00000000 08:05 1259329    /opt/bibble5pro/lib/libQtSql.so.4
b7b42000-b7b45000 rwxp 00095000 08:05 1259329    /opt/bibble5pro/lib/libQtSql.so.4
b7b45000-b7e1a000 r-xp 00000000 08:05 1259326    /opt/bibble5pro/lib/libQt3Support.so.4
b7e1a000-b7e2a000 rwxp 002d5000 08:05 1259326    /opt/bibble5pro/lib/libQt3Support.so.4
b7e2a000-b7e74000 r-xp 00000000 08:05 1259320    /opt/bibble5pro/lib/libQtSvg.so.4
b7e74000-b7e76000 rwxp 0004a000 08:05 1259320    /opt/bibble5pro/lib/libQtSvg.so.4
b7e76000-b7f93000 r-xp 00000000 08:05 1259315    /opt/bibble5pro/lib/libQtScript.so.4
b7f93000-b7f97000 rwxp 0011c000 08:05 1259315    /opt/bibble5pro/lib/libQtScript.so.4
b7f97000-b7fc7000 r-xp 00000000 08:05 1259330    /opt/bibble5pro/lib/libtcmalloc.so
b7fc7000-b7fc8000 rwxp 00030000 08:05 1259330    /opt/bibble5pro/lib/libtcmalloc.so
b7fc8000-b7fdd000 rwxp b7fc8000 00:00 0 
b7fdd000-b8053000 r-xp 00000000 08:05 1259317    /opt/bibble5pro/lib/libkodakcms.so
b8053000-b8057000 rwxp 00076000 08:05 1259317    /opt/bibble5pro/lib/libkodakcms.so
b8057000-b8059000 rwxp b8057000 00:00 0 
b8059000-b805a000 r-xp b8059000 00:00 0          [vdso]
b805a000-b8076000 r-xp 00000000 08:05 416988     /lib/ld-2.9.so
b8076000-b8077000 r-xp 0001b000 08:05 416988     /lib/ld-2.9.so
b8077000-b8078000 rwxp 0001c000 08:05 416988     /lib/ld-2.9.so
bfe63000-bfe78000 rwxp bffeb000 00:00 0          [stack]
remmelt@remmelt-desktop:~$ 


After this the program does not work. I do not understand anything of the info above. Hope you guys can help me out !!

Remmelt

---

### Post by doas777 on 2009-08-02
check out this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6923758](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6923758)
looks like a very similar issue.

---

### Post by RemmeltM on 2009-08-02
Hi,

Ok, I got the files but how do I paste them there (I do not understand the line 'The folder is root protected so you'll have to use Run Application to navigate to it, change permissions & paste the new libs.'

Thanks again,

Remmelt

---

### Post by doas777 on 2009-08-02
the easiest way is to run a file manager window as admin temporarily. 
hit Alt + F2. and enter
```
gksu nautilus
```
you will be prompted for you password and a window will open.

navigate to your destination, and simply paste in the files. 

be very careful with the admin window, as you can make destructive changes with it. close it as soon as you are done.

---

### Post by RemmeltM on 2009-08-02
Hi,

Thanks a lot !! I copied/pasted the downloaded 'missing driver files' with nautilus !! The program now runs !!

Thanks for the very fast help. Amazing.:D

Remmelt

---

