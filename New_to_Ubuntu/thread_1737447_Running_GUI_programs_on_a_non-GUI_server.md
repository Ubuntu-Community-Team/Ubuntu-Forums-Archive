---
title: "Running GUI programs on a non-GUI server"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Jgke on 2011-04-23
My configuration: A non-GUI server without hardware access, a Windows computer with PuTTY. 
I have a Windows-GUI program I want to run in my server using Wine. Possible?

---

### Post by scott-ian on 2011-04-23
I don't think that is possible.  What program are you trying to run?  There may be a better way.  Look at this for simple (sort of GUI) control over a server.
[http://www.webmin.com/](http://www.webmin.com/)
PS: It's free!

---

### Post by Jgke on 2011-04-23
It would be a server for one (-98 ) game. Yes, it is a good game ;)

---

### Post by tordeu on 2011-04-23
I don't think it's possible, either. It would probably exit with an exception once it tries to create and display it's GUI.

Does the software not exist without a GUI? Or maybe it's possible to run the software without a GUI (that is possible with some). 
It's weird that a server application would need a GUI (although of course, on Windows every server version of the OS does contain a GUI). But maybe check if there is an option to run it without a GUI. That would be the first thing to try.

---

### Post by Jgke on 2011-04-23
I wish there was a non-GUI version of it...
But, the server is run with the same program as the game is played.
I'll mark the thread as 'solved' and try to get a GUI to the server ;)

---

### Post by scott-ian on 2011-04-23
I may have an answer.
See this: [http://forum.notebookreview.com/linux-compatibility-software/37741-linux-linux-gui-through-ssh.html](http://forum.notebookreview.com/linux-compatibility-software/37741-linux-linux-gui-through-ssh.html)

You will need CygWin to use a windows computer.

Note: You would need to install X.org on the server to run a GUI

---

### Post by tordeu on 2011-04-23
Okay, so it might work with cygwin and x.org.

One other solution (which might be easier for a new user) is just to install a complete GUI (or even simpler: just install a desktop edition) on the server and use VNC (if both are connected via LAN).

---

### Post by Jgke on 2011-04-23
```
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0". (this error repeats about 30 times)
fixme:system:SystemParametersInfoW Unimplemented action: 79 (SPI_GETLOWPOWERTIMEOUT)
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
fixme:winsock:is_sockaddr_bound don't know how to tell if IPX socket is bound, assuming it is!
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq faile
d: No such file or directory
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
fixme:event:wait_for_withdrawn_state window 0x1004e/e00001 wait timed out
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
fixme:event:wait_for_withdrawn_state window 0x10058/e00004 wait timed out
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
fixme:event:wait_for_withdrawn_state window 0x2004e/e00006 wait timed out
wine: Unhandled page fault on read access to 0x00000030 at address 0x7e0a2766 (thread 0009), starting debugger...
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
fixme:event:wait_for_withdrawn_state window 0x2006c/1200001 wait timed out
Unhandled exception: page fault on read access to 0x00000030 in 32-bit code (0x7e0a2766).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e0a2766 ESP:0033f47c EBP:0033f4f4 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:0016a860 EBX:7e17cff4 ECX:00000000 EDX:00000000
 ESI:0033f560 EDI:00169fd0
Stack dump:
0x0033f47c:  00169ff4 0033f4ac 0033f4d8 7ec73069
0x0033f48c:  7eca0ff4 0033f540 7bc35bc1 00010058
0x0033f49c:  0016a860 00000000 00169ff4 00000000
0x0033f4ac:  00000001 00000b4a 7eca0ff4 0000001c
0x0033f4bc:  00010058 0033f4e0 7ec730b0 7ecdb020
0x0033f4cc:  0033f560 7d643a10 00000004 00000004
Backtrace:
=>0 0x7e0a2766 in wined3d (+0x52766) (0x0033f4f4)
  1 0x7e08e882 in wined3d (+0x3e881) (0x0033f524)
  2 0x7e21beaf in ddraw (+0xbeae) (0x0033f884)
  3 0x7e220733 in ddraw (+0x10732) (0x0033f8a4)
  4 0x0049579c in jazz2 (+0x9579b) (0x0033fe90)
  5 0x7b8559fc call_process_entry+0xb() in kernel32 (0x0033fea8)
  6 0x7b857e6b in kernel32 (+0x47e6a) (0x0033fee8)
  7 0x7bc716e0 call_thread_func+0xb() in ntdll (0x0033fef8)
  8 0x7bc718b0 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  9 0x7bc4c64a in ntdll (+0x3c649) (0x0033ffe8)
0x7e0a2766: call        *0x30(%ecx)
Modules:
Module  Address                 Debug info      Name (83 modules)
PE        400000-  647000       Export          jazz2
ELF     7b800000-7b97d000       Export          kernel32<elf>
  \-PE  7b810000-7b97d000       \               kernel32
ELF     7bc00000-7bcb9000       Export          ntdll<elf>
  \-PE  7bc10000-7bcb9000       \               ntdll
ELF     7bf00000-7bf04000       Deferred        <wine-loader>
ELF     7dff1000-7e007000       Deferred        midimap<elf>
  \-PE  7e000000-7e007000       \               midimap
ELF     7e007000-7e02e000       Deferred        msacm32<elf>
  \-PE  7e010000-7e02e000       \               msacm32
ELF     7e02e000-7e047000       Deferred        msacm32<elf>
  \-PE  7e030000-7e047000       \               msacm32
ELF     7e047000-7e17f000       Export          wined3d<elf>
  \-PE  7e050000-7e17f000       \               wined3d
ELF     7e1bd000-7e205000       Deferred        dsound<elf>
  \-PE  7e1c0000-7e205000       \               dsound
ELF     7e205000-7e25d000       Export          ddraw<elf>
  \-PE  7e210000-7e25d000       \               ddraw
ELF     7e28b000-7e2bf000       Deferred        uxtheme<elf>
  \-PE  7e290000-7e2bf000       \               uxtheme
ELF     7e2bf000-7e2c9000       Deferred        libxcursor.so.1
ELF     7e2c9000-7e2cf000       Deferred        libxfixes.so.3
ELF     7e2cf000-7e2d3000       Deferred        libxcomposite.so.1
ELF     7e2d3000-7e2db000       Deferred        libxrandr.so.2
ELF     7e2db000-7e2e5000       Deferred        libxrender.so.1
ELF     7e2e5000-7e2eb000       Deferred        libxxf86vm.so.1
ELF     7e2eb000-7e2ef000       Deferred        libxinerama.so.1
ELF     7e2ef000-7e311000       Deferred        imm32<elf>
  \-PE  7e300000-7e311000       \               imm32
ELF     7e311000-7e317000       Deferred        libxdmcp.so.6
ELF     7e317000-7e31b000       Deferred        libxau.so.6
ELF     7e31b000-7e335000       Deferred        libxcb.so.1
ELF     7e335000-7e33a000       Deferred        libuuid.so.1
ELF     7e33a000-7e457000       Deferred        libx11.so.6
ELF     7e457000-7e467000       Deferred        libxext.so.6
ELF     7e467000-7e480000       Deferred        libice.so.6
ELF     7e485000-7e48e000       Deferred        librt.so.1
ELF     7e490000-7e533000       Deferred        winex11<elf>
  \-PE  7e4a0000-7e533000       \               winex11
ELF     7e555000-7e57c000       Deferred        libexpat.so.1
ELF     7e57c000-7e5ac000       Deferred        libfontconfig.so.1
ELF     7e5ad000-7e5b6000       Deferred        libsm.so.6
ELF     7e5bc000-7e5d1000       Deferred        libz.so.1
ELF     7e5d1000-7e647000       Deferred        libfreetype.so.6
ELF     7e647000-7e6bc000       Deferred        rpcrt4<elf>
  \-PE  7e650000-7e6bc000       \               rpcrt4
ELF     7e6bc000-7e7bc000       Deferred        ole32<elf>
  \-PE  7e6e0000-7e7bc000       \               ole32
ELF     7e7bc000-7e7d0000       Deferred        lz32<elf>
  \-PE  7e7c0000-7e7d0000       \               lz32
ELF     7e7d0000-7e7e9000       Deferred        version<elf>
  \-PE  7e7e0000-7e7e9000       \               version
ELF     7e7e9000-7e7fd000       Deferred        libresolv.so.2
ELF     7e80d000-7e82e000       Deferred        iphlpapi<elf>
  \-PE  7e810000-7e82e000       \               iphlpapi
ELF     7e82e000-7e85b000       Deferred        ws2_32<elf>
  \-PE  7e840000-7e85b000       \               ws2_32
ELF     7e85b000-7e876000       Deferred        wsock32<elf>
  \-PE  7e860000-7e876000       \               wsock32
ELF     7e876000-7e90b000       Deferred        winmm<elf>
  \-PE  7e880000-7e90b000       \               winmm
ELF     7e90b000-7e96d000       Deferred        shlwapi<elf>
  \-PE  7e920000-7e96d000       \               shlwapi
ELF     7e96d000-7eb47000       Deferred        shell32<elf>
  \-PE  7e980000-7eb47000       \               shell32
ELF     7eb47000-7ebd3000       Deferred        gdi32<elf>
  \-PE  7eb50000-7ebd3000       \               gdi32
ELF     7ebd3000-7ed04000       Deferred        user32<elf>
  \-PE  7ebf0000-7ed04000       \               user32
ELF     7ed04000-7edef000       Deferred        comctl32<elf>
  \-PE  7ed10000-7edef000       \               comctl32
ELF     7edef000-7ee4a000       Deferred        advapi32<elf>
  \-PE  7ee00000-7ee4a000       \               advapi32
ELF     7efa7000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f74f2000-f74fa000       Deferred        libnss_compat.so.2
ELF     f74fb000-f74ff000       Deferred        libdl.so.2
ELF     f74ff000-f7659000       Deferred        libc.so.6
ELF     f765a000-f7673000       Deferred        libpthread.so.0
ELF     f7683000-f77c3000       Export          libwine.so.1
ELF     f77c5000-f77e3000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\jaakko\JJ2\jazz2.exe
        0000001b   15
        00000009    0 <==
0000000e services.exe
        00000014    0
        00000010    0
        0000000f    0
00000011 winedevice.exe
        00000018    0
        00000017    0
        00000013    0
        00000012    0
00000019 explorer.exe
        0000001a    0
Backtrace:
=>0 0x7e0a2766 in wined3d (+0x52766) (0x0033f4f4)
  1 0x7e08e882 in wined3d (+0x3e881) (0x0033f524)
  2 0x7e21beaf in ddraw (+0xbeae) (0x0033f884)
  3 0x7e220733 in ddraw (+0x10732) (0x0033f8a4)
  4 0x0049579c in jazz2 (+0x9579b) (0x0033fe90)
  5 0x7b8559fc call_process_entry+0xb() in kernel32 (0x0033fea8)
  6 0x7b857e6b in kernel32 (+0x47e6a) (0x0033fee8)
  7 0x7bc716e0 call_thread_func+0xb() in ntdll (0x0033fef8)
  8 0x7bc718b0 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  9 0x7bc4c64a in ntdll (+0x3c649) (0x0033ffe8)
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
Xlib:  extension "MIT-SHM" missing on display "localhost:10.0".
err:xrender:get_xrender_format_from_color_shifts No XRender format found!


```

So humm, any tips? Or should I start looking into the GUI? (The GUI did start, but the game crashed with an access violation error :/)

---

### Post by tordeu on 2011-04-23
How did this happen? Did you try the link scott-ian posted or did you install a desktop on the server?

---

### Post by fdrake on 2011-04-23
you will need to install X.server to initiate GUI program. even if you install it it wont be enough since you need to get also a windows manager and a Desktop manager.. . Also installing an Xserver on a server has some security bridges you may want to look into.

---

### Post by lunix- on 2011-04-23
I think i'd install KVM and a small debian-squeeze virtual machine with just the tools you need to get it running. Then you can connect to gui from vnc. That way you dont need to mess up existing server. I have found kvm to be extremely fast and light!  can be hell to set up if you have never done it before but easypeasy the second time ;)

gl

---

### Post by tordeu on 2011-04-23
If it's a "server" (by which I mean it should just function like a server at home, but there is no necessity for it to be based upon a server based operating system with potentially different security aspects etc. etc.) you might just consider installing Xubuntu on it.
It's certainly easier than to start with a server os and install a complete desktop environment on top of it and then, as previously mentioned, use VNC.

I think this would be the easiest solution, if there is nothing would prevent you from doing that.

---

### Post by Jgke on 2011-04-24
Tordeu: I used cygwin and X.
Fdrake: Links?
lunix-: I will consider this, but first I'd like to know if this works.
Tordeu: It's a virtual machine server, located in a private commercial-grade server room.

---

### Post by tordeu on 2011-04-24
Well, if it's a virtual machine, then it might be even more problematic, if the normal game software is used as a server software. If the game uses OpenGL, for example, then it might not even run in a virtual machine at all. I just remember having some problems with OpenGL based 3D-stuff in virtual machines.

But maybe someone with more experience in this field can say something about it. 

I just think that running a possible **3D** **OpenGL** (or maybe even DirectX?)-based Windows game in a **VM** with a dedicated **linux** based **server** operating system using **Cygwin+X** is probably one of the most complicated scenarios when it comes to trying to run a software.
I don't want to discourage you, because it might be possible (depending on the game), but it might as well be impossible due to the fact that it's a virtual machine alone.

Which game is it? Do you know if it is a OpenGL or DirectX game? Is it 3D? And how old is it?

---

### Post by Jgke on 2011-04-25
The game is Jazz Jackrabbit 2 ([http://en.wikipedia.org/wiki/Jazz_Jackrabbit_2](http://en.wikipedia.org/wiki/Jazz_Jackrabbit_2)), and it uses directx 5.0 to run. 2d.

---

