---
title: "typing tutor klavaro not working"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by savadibrahim on 2010-01-24
When i installed klavaro ,it doest start n shows that 
 Error: Dependency is not satisfiable: libgtkdatabox-0.9.0-0

what to do??

---

### Post by ozbolt on 2010-01-24
The thing with dependencies is that it needs to be installed in order to program to work. So all you need to do is install it. 
Go in synaptic package manager (find it in menues) and search for " libgtkdatabox" (without brackets) and install it. And if after that there is still dependancy problem you should also install that.

And next time you install program install it from synaptic package manager or Ubuntu software center. You don't have to search for deb package on da internet.

If you don't understand something just ask :)

---

### Post by savadibrahim on 2010-01-25
But only found libgtkdatabox-0.9.0-**1** in synaptic which is already installed....

---

### Post by Kangarooo on 2010-05-06
for me also not working. not opening. if i open in terminal this is what i get- it opens gives output and closes but visually not opening.
output:
```

abc@easyasdoremi:~$ klavaro
*** glibc detected *** klavaro: double free or corruption (fasttop): 0x080f1ba0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xee2ff1]
/lib/tls/i686/cmov/libc.so.6[0xee46f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xee77cd]
/lib/libglib-2.0.so.0(g_free+0x36)[0x7b7196]
klavaro(trans_init_language_env+0xee)[0x80572be]
klavaro(main_initialize_global_variables+0x165)[0x8051a25]
klavaro(main+0x78)[0x8052438]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xe8eb56]
klavaro[0x8051741]
======= Memory map: ========
00110000-004c8000 r-xp 00000000 08:05 16035      /usr/lib/libgtk-x11-2.0.so.0.1800.3
004c8000-004c9000 ---p 003b8000 08:05 16035      /usr/lib/libgtk-x11-2.0.so.0.1800.3
004c9000-004cd000 r--p 003b8000 08:05 16035      /usr/lib/libgtk-x11-2.0.so.0.1800.3
004cd000-004cf000 rw-p 003bc000 08:05 16035      /usr/lib/libgtk-x11-2.0.so.0.1800.3
004cf000-004d1000 rw-p 00000000 00:00 0 
004d1000-00563000 r-xp 00000000 08:05 16951      /usr/lib/libgdk-x11-2.0.so.0.1800.3
00563000-00565000 r--p 00092000 08:05 16951      /usr/lib/libgdk-x11-2.0.so.0.1800.3
00565000-00566000 rw-p 00094000 08:05 16951      /usr/lib/libgdk-x11-2.0.so.0.1800.3
00566000-00581000 r-xp 00000000 08:05 7691       /usr/lib/libatk-1.0.so.0.2809.1
00581000-00582000 r--p 0001b000 08:05 7691       /usr/lib/libatk-1.0.so.0.2809.1
00582000-00583000 rw-p 0001c000 08:05 7691       /usr/lib/libatk-1.0.so.0.2809.1
00583000-005aa000 r-xp 00000000 08:05 8311       /usr/lib/libpangoft2-1.0.so.0.2600.0
005aa000-005ab000 r--p 00027000 08:05 8311       /usr/lib/libpangoft2-1.0.so.0.2600.0
005ab000-005ac000 rw-p 00028000 08:05 8311       /usr/lib/libpangoft2-1.0.so.0.2600.0
005ac000-005c4000 r-xp 00000000 08:05 16962      /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
005c4000-005c5000 r--p 00017000 08:05 16962      /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
005c5000-005c6000 rw-p 00018000 08:05 16962      /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
005c6000-005ea000 r-xp 00000000 08:05 1395       /lib/tls/i686/cmov/libm-2.10.1.so
005ea000-005eb000 r--p 00023000 08:05 1395       /lib/tls/i686/cmov/libm-2.10.1.so
005eb000-005ec000 rw-p 00024000 08:05 1395       /lib/tls/i686/cmov/libm-2.10.1.so
005ec000-005f3000 r-xp 00000000 08:05 9812       /lib/tls/i686/cmov/librt-2.10.1.so
005f3000-005f4000 r--p 00006000 08:05 9812       /lib/tls/i686/cmov/librt-2.10.1.so
005f4000-005f5000 rw-p 00007000 08:05 9812       /lib/tls/i686/cmov/librt-2.10.1.so
005f6000-00605000 r-xp 00000000 08:05 8417       /usr/lib/libsexy.so.2.0.4
00605000-00606000 r--p 0000f000 08:05 8417       /usr/lib/libsexy.so.2.0.4
00606000-00607000 rw-p 00010000 08:05 8417       /usr/lib/libsexy.so.2.0.4
00607000-00609000 r-xp 00000000 08:05 7618       /usr/lib/libXcomposite.so.1.0.0
00609000-0060a000 r--p 00001000 08:05 7618       /usr/lib/libXcomposite.so.1.0.0
0060a000-0060b000 rw-p 00002000 08:05 7618       /usr/lib/libXcomposite.so.1.0.0
0060b000-0060d000 r-xp 00000000 08:05 7622       /usr/lib/libXdamage.so.1.1.0
0060d000-0060e000 rw-p 00001000 08:05 7622       /usr/lib/libXdamage.so.1.1.0
0060e000-00610000 r-xp 00000000 08:05 7636       /usr/lib/libXinerama.so.1.0.0
00610000-00611000 rw-p 00001000 08:05 7636       /usr/lib/libXinerama.so.1.0.0
00611000-00623000 r-xp 00000000 08:05 9728       /usr/lib/libgtkdatabox-0.9.0.so.1.0.0
00623000-00624000 r--p 00011000 08:05 9728       /usr/lib/libgtkdatabox-0.9.0.so.1.0.0
00624000-00625000 rw-p 00012000 08:05 9728       /usr/lib/libgtkdatabox-0.9.0.so.1.0.0
00625000-0066b000 r-xp 00000000 08:05 8307       /usr/lib/libpango-1.0.so.0.2600.0
0066b000-0066c000 r--p 00045000 08:05 8307       /usr/lib/libpango-1.0.so.0.2600.0
0066c000-0066d000 rw-p 00046000 08:05 8307       /usr/lib/libpango-1.0.so.0.2600.0
0066d000-00698000 r-xp 00000000 08:05 7868       /usr/lib/libfontconfig.so.1.3.0
00698000-00699000 r--p 0002a000 08:05 7868       /usr/lib/libfontconfig.so.1.3.0
00699000-0069a000 rw-p 0002b000 08:05 7868       /usr/lib/libfontconfig.so.1.3.0
0069a000-006a7000 r-xp 00000000 08:05 8191       /usr/lib/liblber-2.4.so.2.5.1
006a7000-006a8000 r--p 0000c000 08:05 8191       /usr/lib/liblber-2.4.so.2.5.1
006a8000-006a9000 rw-p 0000d000 08:05 8191       /usr/lib/liblber-2.4.so.2.5.1
006a9000-006ad000 r-xp 00000000 08:05 7628       /usr/lib/libXfixes.so.3.1.0
006ad000-006ae000 r--p 00003000 08:05 7628       /usr/lib/libXfixes.so.3.1.0
006ae000-006af000 rw-p 00004000 08:05 7628       /usr/lib/libXfixes.so.3.1.0
006af000-006b7000 r-xp 00000000 08:05 7648       /usr/lib/libXrender.so.1.3.0
006b7000-006b8000 r--p 00007000 08:05 7648       /usr/lib/libXrender.so.1.3.0
006b8000-006b9000 rw-p 00008000 08:05 7648       /usr/lib/libXrender.so.1.3.0
006b9000-00733000 r-xp 00000000 08:05 7876       /usr/lib/libfreetype.so.6.3.20
00733000-00737000 r--p 00079000 08:05 7876       /usr/lib/libfreetype.so.6.3.20
00737000-00738000 rw-p 0007d000 08:05 7876       /usr/lib/libfreetype.so.6.3.20
00738000-00774000 r-xp 00000000 08:05 17040      /usr/lib/libgobject-2.0.so.0.2200.3
00774000-00775000 r--p 0003b000 08:05 17040      /usr/lib/libgobject-2.0.so.0.2200.3
00775000-00776000 rw-p 0003c000 08:05 17040      /usr/lib/libgobject-2.0.so.0.2200.3
00776000-0082b000 r-xp 00000000 08:05 17038      /lib/libglib-2.0.so.0.2200.3
0082b000-0082c000 r--p 000b4000 08:05 17038      /lib/libglib-2.0.so.0.2200.3
0082c000-0082d000 rw-p 000b5000 08:05 17038      /lib/libglib-2.0.so.0.2200.3
0082d000-00855000 r-xp 00000000 08:05 17855      /usr/lib/libgssapi_krb5.so.2.2
00855000-00856000 r--p 00027000 08:05 17855      /usr/lib/libgssapi_krb5.so.2.2
00856000-00857000 rw-p 00028000 08:05 17855      /usr/lib/libgssapi_krb5.so.2.2
00857000-00860000 r-xp 00000000 08:05 7634       /usr/lib/libXi.so.6.0.0
00860000-00861000 r--p 00008000 08:05 7634       /usr/lib/libXi.so.6.0.0
00861000-00862000 rw-p 00009000 08:05 7634       /usr/lib/libXi.so.6.0.0
00862000-00864000 r-xp 00000000 08:05 1394       /lib/tls/i686/cmov/libdl-2.10.1.so
00864000-00865000 r--p 00001000 08:05 1394       /lib/tls/i686/cmov/libdl-2.10.1.so
00865000-00866000 rw-p 00002000 08:05 1394       /lib/tls/i686/cmov/libdl-2.10.1.so
00867000-008de000 r-xp 00000000 08:05 25135      /usr/lib/libcairo.so.2.10800.8
008de000-008e0000 r--p 00076000 08:05 25135      /usr/lib/libcairo.so.2.10800.8
008e0000-008e1000 rw-p 00078000 08:05 25135      /usr/lib/libcairo.so.2.10800.8
008e1000-008e8000 r-xp 00000000 08:05 7646       /usr/lib/libXrandr.so.2.2.0
008e8000-008e9000 r--p 00006000 08:05 7646       /usr/lib/libXrandr.so.2.2.0
008e9000-008ea000 rw-p 00007000 08:05 7646       /usr/lib/libXrandr.so.2.2.0
008ea000-008f3000 r-xp 00000000 08:05 7620       /usr/lib/libXcursor.so.1.0.2
008f3000-008f4000 r--p 00008000 08:05 7620       /usr/lib/libXcursor.so.1.0.2
008f4000-008f5000 rw-p 00009000 08:05 7620       /usr/lib/libXcursor.so.1.0.2
008f5000-00905000 r-xp 00000000 08:05 9811       /lib/tls/i686/cmov/libresolv-2.10.1.so
00905000-00906000 r--p 00010000 08:05 9811       /lib/tls/i686/cmov/libresolv-2.10.1.so
00906000-00907000 rw-p 00011000 08:05 9811       /lib/tls/i686/cmov/libresolv-2.10.1.so
00907000-00909000 rw-p 00000000 00:00 0 
00909000-00911000 r-xp 00000000 08:05 7880       /usr/lib/libfusion-1.2.so.0.7.0
00911000-00912000 r--p 00007000 08:05 7880       /usr/lib/libfusion-1.2.so.0.7.0Aborted
abc@easyasdoremi:~$ 

```


also i found solution but its manualy done in 10seconds. from here [https://bugs.launchpad.net/ubuntu/+source/klavaro/+bug/439753](https://bugs.launchpad.net/ubuntu/+source/klavaro/+bug/439753)
also as newcommer ill give u 3 ways to make solution for this bug so ull learn something also :)
like a joe
A.) create in home folder .klavaro and in there preferences.ini
folder with .instart are hidden so to see created file use ctrl+h to see/hide hiden files

or like hacker :)

B.)esyr to make folder and file is in terminal copy this
Code:

mkdir ~/.klavaro & touch ~/.klavaro/preferences.ini

C.)more esyrif u know command then just open alt+f2 and copy there the same. with alt+f2 it will execute without showing terminal but u can check option to show in terminal command executing but terminal will close when command is finished thats the only difference

---

