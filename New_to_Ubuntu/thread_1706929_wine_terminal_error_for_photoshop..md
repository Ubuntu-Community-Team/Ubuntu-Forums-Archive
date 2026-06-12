---
title: "wine terminal error for photoshop."
date: 2011-03-14
forum: New to Ubuntu
---

### Post by thecompgame on 2011-03-14
Hi, i was reading a thread that told me to launch photoshop from the terminal so i tried it and this is the error i got: 

[email]neal@neal-AW012AAR-ABA-p6280t:~/.wine[/email]/drive_c/Program Files/Adobe$ wine photoshop.exe
err:module:import_dll Library cg.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library cgGL.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library adbeape.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library ahclient.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library AXEDOMCore.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library MPS.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:import_dll Library PlugPlug.dll (which is needed by L"C:\\windows\\system32\\photoshop.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\photoshop.exe" failed, status c0000135

I have no idea what to do -.-

---

### Post by 311005901 on 2011-03-14
You may want to check out [PlayOnLinux]("http://www.playonlinux.com/en/"). This is an app that allows you to install and run Windows programs with Wine with an easy GUI. [This forum post]("http://www.playonlinux.com/en/topic-3104-Adobe_Photoshop_CS4.html") has information on Photoshop CS4 and may be helpful to you.

---

### Post by thecompgame on 2011-03-14
> **311005901 said:**
> You may want to check out [PlayOnLinux]("http://www.playonlinux.com/en/"). This is an app that allows you to install and run Windows programs with Wine with an easy GUI. [This forum post]("http://www.playonlinux.com/en/topic-3104-Adobe_Photoshop_CS4.html") has information on Photoshop CS4 and may be helpful to you.

I already have PLayonlinux and iv used it to install microsoft 2007 on it already but i need ps cs5 because it has more features that i use.

---

### Post by Crxss on 2011-03-14
Indeed, CS5 is much better. I'm still waiting for the day adobe finally supports linux OS's.

Apparently, CS5 runs fine on wine in 10.4 but will not run on 10.10 through wine. Here's a link that may help you:

[http://maketecheasier.com/install-photoshop-cs5-in-ubuntu-maverick/2010/11/02](http://maketecheasier.com/install-photoshop-cs5-in-ubuntu-maverick/2010/11/02)

---

### Post by jcolyn on 2011-03-14
> **Crxss said:**
> Indeed, CS5 is much better. I'm still waiting for the day adobe finally supports linux OS's.

You have a long wait ahead of ya..

Adobe has no intentions of porting PhotoShop to Linux since the user base is so small..

---

### Post by jcolyn on 2011-03-14
> **thecompgame said:**
> I already have PLayonlinux and iv used it to install microsoft 2007 on it already but i need ps cs5 because it has more features that i use.

The best way to install PhotoShop or any other program from a CD is to create a temp directory in your /home folder and copy the contents of the CD/DVD including any hidden files into this directory. Then open a terminal and cd to the folder and enter ```
wine photoshop.exe
```Do not do this under root.

If you get any errors of missing dll's you can download them to your downloads directory by searching google for the dll's.

Once you download all needed dll's open your /home folder and enable show hidden files and locate the .wine folder. Open it and open the drive_c folder-windows folder-system 32 folder and copy the dll's into it. Then open the terminal and re-enter ```
wine photoshop.exe
``` and the setup program should now start.

Once done reboot and then locate wine in applications click programs and you should then see the photoshop start link..

---

### Post by thecompgame on 2011-03-14
> **jcolyn said:**
> The best way to install PhotoShop or any other program from a CD is to create a temp directory in your /home folder and copy the contents of the CD/DVD including any hidden files into this directory. Then open a terminal and cd to the folder and enter ```
wine photoshop.exe
```Do not do this under root.

If you get any errors of missing dll's you can download them to your downloads directory by searching google for the dll's.

Once you download all needed dll's open your /home folder and enable show hidden files and locate the .wine folder. Open it and open the drive_c folder-windows folder-system 32 folder and copy the dll's into it. Then open the terminal and re-enter ```
wine photoshop.exe
``` and the setup program should now start.

Once done reboot and then locate wine in applications click programs and you should then see the photoshop start link..

THanks for the info hopefully after i find all the dll's it'll work :)
Thanks again

---

### Post by thecompgame on 2011-03-14
> **jcolyn said:**
> The best way to install PhotoShop or any other program from a CD is to create a temp directory in your /home folder and copy the contents of the CD/DVD including any hidden files into this directory. Then open a terminal and cd to the folder and enter ```
wine photoshop.exe
```Do not do this under root.

If you get any errors of missing dll's you can download them to your downloads directory by searching google for the dll's.

Once you download all needed dll's open your /home folder and enable show hidden files and locate the .wine folder. Open it and open the drive_c folder-windows folder-system 32 folder and copy the dll's into it. Then open the terminal and re-enter ```
wine photoshop.exe
``` and the setup program should now start.

Once done reboot and then locate wine in applications click programs and you should then see the photoshop start link..

I got all the dll's and this is the error i got :

> neal@neal-AW012AAR-ABA-p6280t:~$ wine photoshop.exe
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
wine: Unhandled exception 0xc06d007e at address 0x7b839962 (thread 0045), starting debugger...
Unhandled exception: 0xc06d007e in 32-bit code (0x7b839962).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b839962 ESP:0032fd14 EBP:0032fd78 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b82585d EBX:7b888ff4 ECX:0032fd9c EDX:0032fd38
 ESI:c06d007e EDI:00000000
Stack dump:
0x0032fd14:  0032fdec 00000004 034c38b8 c06d007e
0x0032fd24:  00000000 00000000 7b839962 00000001
0x0032fd34:  0032fd9c 7ffd8c00 0218dd0c 00000000
0x0032fd44:  0032fd64 7b8531e5 7ffd8c00 00000000
0x0032fd54:  00000000 00000000 7b8531ab 7b888ff4
0x0032fd64:  0032fd84 7b85321f 7b83991a 00000000
Backtrace:
=>0 0x7b839962 in kernel32 (+0x29962) (0x0032fd78)
  1 0x01c4dac2 in photoshop (+0x184dac1) (0x0032fde0)
  2 0x014248b7 in photoshop (+0x10248b6) (0x0032fe08)
  3 0x013127be in photoshop (+0xf127bd) (0x0032fe90)
  4 0x7b85885c call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b8594ff ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc72f78 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75a30 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a9ea call_dll_entry_point+0x629() in ntdll (0x0032ffe8)
0x7b839962: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (108 modules)
PE      340000-  3b6000    Deferred        cggl
PE      3c0000-  3c9000    Deferred        adbeape
PE      400000- 2c2c000    Export          photoshop
PE     2c30000- 2d84000    Deferred        adobeowl
PE     2d90000- 2dd8000    Deferred        adobeowlcanvas
PE     2de0000- 2e1c000    Deferred        ahclient
PE     2e20000- 2ec6000    Deferred        axedomcore
PE     2ed0000- 3372000    Deferred        mps
PE     3380000- 3497000    Deferred        plugplug
PE    10000000-100fe000    Deferred        cg
PE    4ec50000-4edfb000    Deferred        gdiplus
PE    78480000-7850e000    Deferred        msvcp90
PE    78520000-785c3000    Deferred        msvcr90
ELF    79c9c000-7b800000    Deferred        fglrx_dri.so
ELF    7b800000-7b990000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b990000    \               kernel32
ELF    7bc00000-7bcbb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcbb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cf1c000-7cf50000    Deferred        uxtheme<elf>
  \-PE    7cf20000-7cf50000    \               uxtheme
ELF    7cf50000-7cf8c000    Deferred        libdbus-1.so.3
ELF    7cf8c000-7cf9d000    Deferred        libtasn1.so.3
ELF    7cf9d000-7d04b000    Deferred        libkrb5.so.3
ELF    7d04b000-7d0bf000    Deferred        libgcrypt.so.11
ELF    7d0bf000-7d15a000    Deferred        libgnutls.so.26
ELF    7d15a000-7d1a4000    Deferred        libcups.so.2
ELF    7d3c9000-7d3ce000    Deferred        libgpg-error.so.0
ELF    7d3ce000-7d3e2000    Deferred        libresolv.so.2
ELF    7d3e2000-7d3e6000    Deferred        libkeyutils.so.1
ELF    7d3e6000-7d3ee000    Deferred        libkrb5support.so.0
ELF    7d3ee000-7d3f2000    Deferred        libcom_err.so.2
ELF    7d3f2000-7d416000    Deferred        libk5crypto.so.3
ELF    7d416000-7d445000    Deferred        libgssapi_krb5.so.2
ELF    7d602000-7d634000    Deferred        libatiadlxx.so
ELF    7d637000-7d647000    Deferred        libavahi-client.so.3
ELF    7d647000-7d653000    Deferred        libavahi-common.so.3
ELF    7dd53000-7dd5d000    Deferred        libxcursor.so.1
ELF    7dd5d000-7dd63000    Deferred        libxfixes.so.3
ELF    7dd63000-7dd67000    Deferred        libxcomposite.so.1
ELF    7dd67000-7dd6f000    Deferred        libxrandr.so.2
ELF    7dd6f000-7dd79000    Deferred        libxrender.so.1
ELF    7dd79000-7dd7f000    Deferred        libxxf86vm.so.1
ELF    7dd7f000-7dd83000    Deferred        libxinerama.so.1
ELF    7dd97000-7dda0000    Deferred        librt.so.1
ELF    7dda2000-7ddc3000    Deferred        imm32<elf>
  \-PE    7ddb0000-7ddc3000    \               imm32
ELF    7ddc3000-7de6c000    Deferred        winex11<elf>
  \-PE    7ddd0000-7de6c000    \               winex11
ELF    7dfb1000-7dfd8000    Deferred        libexpat.so.1
ELF    7dfd8000-7e008000    Deferred        libfontconfig.so.1
ELF    7e008000-7e07f000    Deferred        libfreetype.so.6
ELF    7e07f000-7e0b8000    Deferred        libncurses.so.5
ELF    7e0b8000-7e1a5000    Deferred        oleaut32<elf>
  \-PE    7e0d0000-7e1a5000    \               oleaut32
ELF    7e1a5000-7e20c000    Deferred        wininet<elf>
  \-PE    7e1b0000-7e20c000    \               wininet
ELF    7e24a000-7e26e000    Deferred        mpr<elf>
  \-PE    7e250000-7e26e000    \               mpr
ELF    7e26e000-7e283000    Deferred        libz.so.1
ELF    7e283000-7e2b3000    Deferred        ws2_32<elf>
  \-PE    7e290000-7e2b3000    \               ws2_32
ELF    7e2b3000-7e3a7000    Deferred        comctl32<elf>
  \-PE    7e2c0000-7e3a7000    \               comctl32
ELF    7e3a7000-7e40b000    Deferred        shlwapi<elf>
  \-PE    7e3b0000-7e40b000    \               shlwapi
ELF    7e40b000-7e608000    Deferred        shell32<elf>
  \-PE    7e420000-7e608000    \               shell32
ELF    7e608000-7e640000    Deferred        winspool<elf>
  \-PE    7e610000-7e640000    \               winspool
ELF    7e640000-7e65c000    Deferred        libgcc_s.so.1
ELF    7e65c000-7e676000    Deferred        libxcb.so.1
ELF    7e676000-7e73a000    Deferred        libgl.so.1
ELF    7e73a000-7e857000    Deferred        libx11.so.6
ELF    7e857000-7e867000    Deferred        libxext.so.6
ELF    7e867000-7e880000    Deferred        libice.so.6
ELF    7e89f000-7e951000    Deferred        opengl32<elf>
  \-PE    7e8c0000-7e951000    \               opengl32
ELF    7e951000-7e9c4000    Deferred        rpcrt4<elf>
  \-PE    7e960000-7e9c4000    \               rpcrt4
ELF    7e9c4000-7eac8000    Deferred        ole32<elf>
  \-PE    7e9e0000-7eac8000    \               ole32
ELF    7eac8000-7eae1000    Deferred        version<elf>
  \-PE    7ead0000-7eae1000    \               version
ELF    7eae1000-7eb3d000    Deferred        advapi32<elf>
  \-PE    7eaf0000-7eb3d000    \               advapi32
ELF    7eb3d000-7ebcb000    Deferred        gdi32<elf>
  \-PE    7eb50000-7ebcb000    \               gdi32
ELF    7ebcb000-7ed00000    Deferred        user32<elf>
  \-PE    7ebe0000-7ed00000    \               user32
ELF    7ed00000-7ed8d000    Deferred        msvcrt<elf>
  \-PE    7ed10000-7ed8d000    \               msvcrt
ELF    7ef8d000-7ef99000    Deferred        libnss_files.so.2
ELF    7ef99000-7efa4000    Deferred        libnss_nis.so.2
ELF    7efa4000-7efbb000    Deferred        libnsl.so.1
ELF    7efbb000-7efe1000    Deferred        libm.so.6
ELF    7efe2000-7efe8000    Deferred        libxdmcp.so.6
ELF    7efe8000-7eff0000    Deferred        libatiuki.so.1
ELF    7eff0000-7eff9000    Deferred        libsm.so.6
ELF    f74e2000-f74e6000    Deferred        libxau.so.6
ELF    f74e7000-f74eb000    Deferred        libdl.so.2
ELF    f74eb000-f7646000    Deferred        libc.so.6
ELF    f7647000-f7660000    Deferred        libpthread.so.0
ELF    f7671000-f7676000    Deferred        libuuid.so.1
ELF    f7677000-f767f000    Deferred        libnss_compat.so.2
ELF    f767f000-f77c0000    Dwarf           libwine.so.1
ELF    f77c2000-f77e0000    Deferred        ld-linux.so.2
ELF    f77e0000-f77e1000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000016    0
    00000013    0
    00000012    0
00000019 plugplay.exe
    0000001d    0
    0000001b    0
    0000001a    0
0000001e explorer.exe
    0000001f    0
00000020 Photoshop.exe
    00000027    0
    00000026    0
    00000025    0
    00000024    0
    00000023    0
    00000022    0
00000044 (D) C:\windows\system32\photoshop.exe
    00000045    0 <==
Backtrace:
=>0 0x7b839962 in kernel32 (+0x29962) (0x0032fd78)
  1 0x01c4dac2 in photoshop (+0x184dac1) (0x0032fde0)
  2 0x014248b7 in photoshop (+0x10248b6) (0x0032fe08)
  3 0x013127be in photoshop (+0xf127bd) (0x0032fe90)
  4 0x7b85885c call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b8594ff ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc72f78 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75a30 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4a9ea call_dll_entry_point+0x629() in ntdll (0x0032ffe8)


---

### Post by jcolyn on 2011-03-14
I would say CS4-5 is not compatible with your system. I've heard of some getting it to work but the last version fully compatible is PhotoShop 7

Gimp once you get used to the interface is a very good image editing program but if you want to keep PS you might want to consider dual booting Windows and Linux..

---

### Post by thecompgame on 2011-03-14
> **jcolyn said:**
> I would say CS4-5 is not compatible with your system. I've heard of some getting it to work but the last version fully compatible is PhotoShop 7

Gimp once you get used to the interface is a very good image editing program but if you want to keep PS you might want to consider dual booting Windows and Linux..
I already dual boot and i have windows 7/xp on VB on ubuntu but its much easier to use photoshop on ubuntu cause i usually have other stuff running and downloading.

---

