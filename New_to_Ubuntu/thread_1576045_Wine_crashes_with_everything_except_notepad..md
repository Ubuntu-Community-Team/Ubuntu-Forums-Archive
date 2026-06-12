---
title: "Wine crashes with everything except notepad."
date: 2010-09-16
forum: New to Ubuntu
---

### Post by MacFall on 2010-09-16
When I try to run a program using (for example) "wine gens", I get this dialog:> The program gens.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.The terminal has this to say about it:> Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
wine: Unhandled page fault on read access to 0x00000030 at address 0x20056572 (thread 0047), starting debugger...
Unhandled exception: page fault on read access to 0x00000030 in 32-bit code (0x20056572).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:20056572 ESP:0032f5b4 EBP:0032f66c EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:20133ff4 ECX:00000000 EDX:00160794
 ESI:00164638 EDI:0032f634
Stack dump:
0x0032f5b4:  00160794 0032f5e8 00164660 7b84064f
0x0032f5c4:  00110000 200359d0 00160330 7bc4613e
0x0032f5d4:  00000000 00000000 00160770 00160794
0x0032f5e4:  00170000 00000000 00000000 00000000
0x0032f5f4:  00000000 00000000 00000000 00000000
0x0032f604:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x20056572 in wined3d (+0x46572) (0x0032f66c)
  1 0x2005946b in wined3d (+0x4946a) (0x0032f6cc)
  2 0x68301fea in ddraw (+0x21fe9) (0x0032f74c)
  3 0x683024a1 DirectDrawCreate+0x50() in ddraw (0x0032f79c)
  4 0x0047ce1f in gens (+0x7ce1e) (0x0032f844)
  5 0x00488435 in gens (+0x88434) (0x0032f914)
  6 0x00471b13 in gens (+0x71b12) (0x00400000)
  7 0x00000003 (0x00905a4d)
0x20056572: call    *0x30(%eax)
Modules:
Module    Address            Debug info    Name (94 modules)
PE      400000- 15c8000    Export          gens
ELF    20000000-20136000    Export          wined3d<elf>
  \-PE    20010000-20136000    \               wined3d
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68158000    Deferred        libwine.so.1
ELF    68158000-6815c000    Deferred        libdl.so.2
ELF    6815c000-68182000    Deferred        libm.so.6
ELF    68182000-6818a000    Deferred        libnss_compat.so.2
ELF    6818a000-681a1000    Deferred        libnsl.so.1
ELF    681a1000-681ab000    Deferred        libnss_nis.so.2
ELF    681ab000-681b7000    Deferred        libnss_files.so.2
ELF    681b7000-681d2000    Deferred        wsock32<elf>
  \-PE    681c0000-681d2000    \               wsock32
ELF    681d2000-681f2000    Deferred        iphlpapi<elf>
  \-PE    681e0000-681f2000    \               iphlpapi
ELF    681f2000-68206000    Deferred        libresolv.so.2
ELF    68206000-6825f000    Deferred        advapi32<elf>
  \-PE    68210000-6825f000    \               advapi32
ELF    6825f000-682d0000    Deferred        rpcrt4<elf>
  \-PE    68270000-682d0000    \               rpcrt4
ELF    682d0000-68328000    Export          ddraw<elf>
  \-PE    682e0000-68328000    \               ddraw
ELF    68328000-68424000    Deferred        ole32<elf>
  \-PE    68340000-68424000    \               ole32
ELF    68424000-68533000    Deferred        user32<elf>
  \-PE    68440000-68533000    \               user32
ELF    68533000-685bd000    Deferred        gdi32<elf>
  \-PE    68540000-685bd000    \               gdi32
ELF    685bd000-68605000    Deferred        dsound<elf>
  \-PE    685c0000-68605000    \               dsound
ELF    68605000-6868c000    Deferred        winmm<elf>
  \-PE    68610000-6868c000    \               winmm
ELF    6868c000-686c5000    Deferred        dinput<elf>
  \-PE    68690000-686c5000    \               dinput
ELF    686c5000-68859000    Deferred        shell32<elf>
  \-PE    686e0000-68859000    \               shell32
ELF    68859000-688b8000    Deferred        shlwapi<elf>
  \-PE    68870000-688b8000    \               shlwapi
ELF    688b8000-688ee000    Deferred        winspool<elf>
  \-PE    688c0000-688ee000    \               winspool
ELF    688ee000-68964000    Deferred        libfreetype.so.6
ELF    68964000-68979000    Deferred        libz.so.1
ELF    68979000-689a9000    Deferred        libfontconfig.so.1
ELF    689a9000-689d0000    Deferred        libexpat.so.1
ELF    689d0000-68a6f000    Deferred        winex11<elf>
  \-PE    689e0000-68a6f000    \               winex11
ELF    68a6f000-68a88000    Deferred        libice.so.6
ELF    68a88000-68a98000    Deferred        libxext.so.6
ELF    68a98000-68a9d000    Deferred        libuuid.so.1
ELF    68a9d000-68aa1000    Deferred        libxau.so.6
ELF    68aa1000-68aa7000    Deferred        libxdmcp.so.6
ELF    68aa7000-68ac8000    Deferred        imm32<elf>
  \-PE    68ab0000-68ac8000    \               imm32
ELF    68ac8000-68acc000    Deferred        libxinerama.so.1
ELF    68acc000-68ad2000    Deferred        libxxf86vm.so.1
ELF    68ad2000-68adc000    Deferred        libxrender.so.1
ELF    68adc000-68ae4000    Deferred        libxrandr.so.2
ELF    68ae4000-68ae8000    Deferred        libxcomposite.so.1
ELF    68ae8000-68aee000    Deferred        libxfixes.so.3
ELF    68aee000-68af8000    Deferred        libxcursor.so.1
ELF    68af8000-68b2b000    Deferred        uxtheme<elf>
  \-PE    68b00000-68b2b000    \               uxtheme
ELF    68b2b000-68b72000    Deferred        libcups.so.2
ELF    68b72000-68c0d000    Deferred        libgnutls.so.26
ELF    68c0d000-68c19000    Deferred        libavahi-common.so.3
ELF    68c19000-68c2a000    Deferred        libavahi-client.so.3
ELF    68c2a000-68cdb000    Deferred        libkrb5.so.3
ELF    68cdb000-68cff000    Deferred        libk5crypto.so.3
ELF    68cff000-68d03000    Deferred        libcom_err.so.2
ELF    68d03000-68d07000    Deferred        libkeyutils.so.1
ELF    68d07000-68d18000    Deferred        libtasn1.so.3
ELF    68d18000-68d8b000    Deferred        libgcrypt.so.11
ELF    68d8b000-68d94000    Deferred        librt.so.1
ELF    68d94000-68d99000    Deferred        libgpg-error.so.0
ELF    69573000-695a2000    Deferred        libgssapi_krb5.so.2
ELF    6a83f000-6a841000    Deferred        libnvidia-tls.so.1
ELF    6bee2000-6beeb000    Deferred        libsm.so.6
ELF    6fa78000-6fb46000    Deferred        comctl32<elf>
  \-PE    6fa80000-6fb46000    \               comctl32
ELF    71062000-7106a000    Deferred        libkrb5support.so.0
ELF    7320f000-73369000    Deferred        libc.so.6
ELF    77a58000-77a84000    Deferred        ws2_32<elf>
  \-PE    77a60000-77a84000    \               ws2_32
ELF    78aa7000-78ac0000    Deferred        libpthread.so.0
ELF    794c3000-794dd000    Deferred        libxcb.so.1
ELF    79b8b000-79bc4000    Deferred        libdbus-1.so.3
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cc4e000-7cd6b000    Deferred        libx11.so.6
ELF    7cebb000-7cf66000    Deferred        comdlg32<elf>
  \-PE    7cec0000-7cf66000    \               comdlg32
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000016    0
    00000013    0
    00000012    0
0000001c explorer.exe
    0000001d    0
0000003a eCalc Calculator.exe
    0000003b    0
0000000c (D) C:\windows\system32\gens.exe
    00000009    0 <==
Backtrace:
=>0 0x20056572 in wined3d (+0x46572) (0x0032f66c)
  1 0x2005946b in wined3d (+0x4946a) (0x0032f6cc)
  2 0x68301fea in ddraw (+0x21fe9) (0x0032f74c)
  3 0x683024a1 DirectDrawCreate+0x50() in ddraw (0x0032f79c)
  4 0x0047ce1f in gens (+0x7ce1e) (0x0032f844)
  5 0x00488435 in gens (+0x88434) (0x0032f914)
  6 0x00471b13 in gens (+0x71b12) (0x00400000)
  7 0x00000003 (0x00905a4d)
This has happened with all four of the programs I've tried so far.

---

### Post by sandyd on 2010-09-16
> **MacFall said:**
> When I try to run a program using (for example) "wine gens", I get this dialog:The terminal has this to say about it:This has happened with all four of the programs I've tried so far.
what video card do you have.
your missing the xorg GLX extensions.

have you installed any drivers for it either?

---

