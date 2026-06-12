---
title: "Wine Help"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by austinpsycho on 2009-07-05
I had the 32 bit version of ubuntu installed; with wine 1.24 and rosetta stone working just fine on it.  I deleted that distro and upgraded to 64bit with wine 1.24 and rosetta stone was working just fine.  The developement release of wine 1.25 came out; and my computer grabbed it from the repos and updated it.  rosettastone stopped working.  I have since uninstalled wine with synaptic complete remove, and *sudo apt-get purge wine* even so far as to uninstall all unused dependanceis afterwards..  and still when I reinstall 1.24, rosetta stone will install but just error out; starting it from command line gets this response:```
-desktop:~$ env WINEPREFIX="/home/jeff/.wine" wine "C:\Program Files\Rosetta Stone\Rosetta Stone Version 3\RosettaStoneVersion3.exe" 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:shdocvw:taskbar_list_HrInit iface 0x1368c0 stub!
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
wine: Unhandled page fault on write access to 0xcb1b00af at address 0x7db92a46 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0xcb1b00af in 32-bit code (0x7db92a46).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7db92a46 ESP:0032f0a0 EBP:00000009 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000018 EBX:f7ce36c0 ECX:7dbe5d20 EDX:cb1b00af
 ESI:f7ce36c0 EDI:000011f3
Stack dump:
0x0032f0a0:  00000000 7db9a282 00000002 00000000
0x0032f0b0:  7ca2c840 01a2c86c 000011f3 7ca2c840
0x0032f0c0:  ffedac08 7db9a871 f7ce36c0 000011f3
0x0032f0d0:  00000001 00000000 7dbc0920 7dbc1bc0
0x0032f0e0:  0032f100 7c59c912 f7fd9ff4 00000000
0x0032f0f0:  f7e29e41 f7fd9ff4 7d363da0 00000000
Backtrace:
=>0 0x7db92a46 in libgl.so.1 (+0x52a46) (0x00000009)
  1 0x00000000 (0x00000000)
0x7db92a46: movl    $0x7dbc2e60,0x0(%edx)
Modules:
Module    Address            Debug info    Name (115 modules)
PE      400000-  89d000    Deferred        rosettastoneversion3
PE     2400000- 241c000    Deferred        0.mdd
PE     2530000- 255a000    Deferred        5.mdd
PE     2670000- 268e000    Deferred        1.mdd
PE     27a0000- 27bb000    Deferred        3.mdd
PE     28d0000- 28e8000    Deferred        4.mdd
PE    10000000-1002e000    Deferred        2.mdd
ELF    7b800000-7b954000    Deferred        kernel32<elf>
  \-PE    7b820000-7b954000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c34a000-7d2af000    Deferred        libglcore.so.1
ELF    7d6d4000-7d804000    Deferred        wined3d<elf>
  \-PE    7d6f0000-7d804000    \               wined3d
ELF    7db40000-7dbe7000    Export          libgl.so.1
ELF    7dbff000-7dc2d000    Deferred        ws2_32<elf>
  \-PE    7dc10000-7dc2d000    \               ws2_32
ELF    7dc2d000-7dcb0000    Deferred        crypt32<elf>
  \-PE    7dc40000-7dcb0000    \               crypt32
ELF    7dcb0000-7dccb000    Deferred        version<elf>
  \-PE    7dcc0000-7dccb000    \               version
ELF    7dccb000-7dcee000    Deferred        mpr<elf>
  \-PE    7dcd0000-7dcee000    \               mpr
ELF    7dcee000-7dd41000    Deferred        wininet<elf>
  \-PE    7dd00000-7dd41000    \               wininet
ELF    7dd41000-7dd84000    Deferred        urlmon<elf>
  \-PE    7dd50000-7dd84000    \               urlmon
ELF    7dd84000-7ddc4000    Deferred        shdocvw<elf>
  \-PE    7dd90000-7ddc4000    \               shdocvw
ELF    7ddc4000-7ddc8000    Deferred        libgpg-error.so.0
ELF    7ddc8000-7de31000    Deferred        libgcrypt.so.11
ELF    7de31000-7de43000    Deferred        libtasn1.so.3
ELF    7de43000-7de59000    Deferred        libresolv.so.2
ELF    7de59000-7de5d000    Deferred        libkeyutils.so.1
ELF    7de5d000-7de66000    Deferred        libkrb5support.so.0
ELF    7de66000-7de8a000    Deferred        libk5crypto.so.3
ELF    7de8a000-7df1c000    Deferred        libkrb5.so.3
ELF    7df1c000-7dfb9000    Deferred        libgnutls.so.26
ELF    7dfb9000-7dfe4000    Deferred        libgssapi_krb5.so.2
ELF    7dfe4000-7e01b000    Deferred        libcups.so.2
ELF    7e01f000-7e033000    Deferred        lz32<elf>
  \-PE    7e020000-7e033000    \               lz32
ELF    7e081000-7e0a7000    Deferred        msacm32<elf>
  \-PE    7e090000-7e0a7000    \               msacm32
ELF    7e0a7000-7e0bf000    Deferred        msacm32<elf>
  \-PE    7e0b0000-7e0bf000    \               msacm32
ELF    7e0c0000-7e188000    Deferred        libasound.so.2
ELF    7e189000-7e18b000    Deferred        libnvidia-tls.so.1
ELF    7e18b000-7e1a0000    Deferred        midimap<elf>
  \-PE    7e190000-7e1a0000    \               midimap
ELF    7e1a0000-7e1d7000    Deferred        winealsa<elf>
  \-PE    7e1b0000-7e1d7000    \               winealsa
ELF    7e1d7000-7e20b000    Deferred        uxtheme<elf>
  \-PE    7e1e0000-7e20b000    \               uxtheme
ELF    7e20b000-7e210000    Deferred        libxfixes.so.3
ELF    7e210000-7e219000    Deferred        libxcursor.so.1
ELF    7e219000-7e221000    Deferred        libxrandr.so.2
ELF    7e221000-7e22b000    Deferred        libxrender.so.1
ELF    7e22b000-7e231000    Deferred        libxxf86vm.so.1
ELF    7e231000-7e234000    Deferred        libxinerama.so.1
ELF    7e234000-7e255000    Deferred        imm32<elf>
  \-PE    7e240000-7e255000    \               imm32
ELF    7e255000-7e25a000    Deferred        libxdmcp.so.6
ELF    7e25a000-7e274000    Deferred        libxcb.so.1
ELF    7e274000-7e278000    Deferred        libxau.so.6
ELF    7e278000-7e27d000    Deferred        libuuid.so.1
ELF    7e27d000-7e36c000    Deferred        libx11.so.6
ELF    7e36c000-7e37c000    Deferred        libxext.so.6
ELF    7e37c000-7e394000    Deferred        libice.so.6
ELF    7e394000-7e39d000    Deferred        libsm.so.6
ELF    7e3a6000-7e3aa000    Deferred        libcom_err.so.2
ELF    7e3aa000-7e3b3000    Deferred        librt.so.1
ELF    7e3b5000-7e451000    Deferred        winex11<elf>
  \-PE    7e3c0000-7e451000    \               winex11
ELF    7e45f000-7e486000    Deferred        libexpat.so.1
ELF    7e486000-7e4b3000    Deferred        libfontconfig.so.1
ELF    7e4b3000-7e4c9000    Deferred        libz.so.1
ELF    7e4c9000-7e540000    Deferred        libfreetype.so.6
ELF    7e558000-7e640000    Deferred        oleaut32<elf>
  \-PE    7e570000-7e640000    \               oleaut32
ELF    7e640000-7e676000    Deferred        winspool<elf>
  \-PE    7e650000-7e676000    \               winspool
ELF    7e676000-7e6d4000    Deferred        shlwapi<elf>
  \-PE    7e680000-7e6d4000    \               shlwapi
ELF    7e6d4000-7e860000    Deferred        shell32<elf>
  \-PE    7e6e0000-7e860000    \               shell32
ELF    7e860000-7e912000    Deferred        comdlg32<elf>
  \-PE    7e870000-7e912000    \               comdlg32
ELF    7e912000-7e9a9000    Deferred        winmm<elf>
  \-PE    7e920000-7e9a9000    \               winmm
ELF    7e9a9000-7ea71000    Deferred        comctl32<elf>
  \-PE    7e9b0000-7ea71000    \               comctl32
ELF    7ea71000-7eade000    Deferred        rpcrt4<elf>
  \-PE    7ea80000-7eade000    \               rpcrt4
ELF    7eade000-7eb7f000    Deferred        gdi32<elf>
  \-PE    7eaf0000-7eb7f000    \               gdi32
ELF    7eb7f000-7ecca000    Deferred        user32<elf>
  \-PE    7eba0000-7ecca000    \               user32
ELF    7ecca000-7ed20000    Deferred        advapi32<elf>
  \-PE    7ece0000-7ed20000    \               advapi32
ELF    7ed20000-7ee1b000    Deferred        ole32<elf>
  \-PE    7ed40000-7ee1b000    \               ole32
ELF    7ee1b000-7ee73000    Deferred        ddraw<elf>
  \-PE    7ee20000-7ee73000    \               ddraw
ELF    7ef9d000-7efa9000    Deferred        libnss_files.so.2
ELF    7efa9000-7efc2000    Deferred        libnsl.so.1
ELF    7efc2000-7efe8000    Deferred        libm.so.6
ELF    7efec000-7eff7000    Deferred        libnss_nis.so.2
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    f7ce4000-f7ce8000    Deferred        libdl.so.2
ELF    f7ce8000-f7e4b000    Deferred        libc.so.6
ELF    f7e4c000-f7e65000    Deferred        libpthread.so.0
ELF    f7e7d000-f7fb8000    Deferred        libwine.so.1
ELF    f7fba000-f7fdb000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rosetta Stone\Rosetta Stone Version 3\RosettaStoneVersion3.exe
    00000015    0
    00000014    0
    00000013   15
    00000012    0
    00000011    0
    00000009    0 <==
0000000c 
    0000000e    0
    0000000d    0
0000000f 
    00000010    0
Backtrace:
=>0 0x7db92a46 in libgl.so.1 (+0x52a46) (0x00000009)
  1 0x00000000 (0x00000000)
Killed

```

---

### Post by austinpsycho on 2009-07-05
so yeah.. guess nobody has any ideas?

---

### Post by austinpsycho on 2009-07-05
and I thought we were all friends here :(   *sheepish grin* oh well; guess i don't get to use it or i can reinstall....... again

---

### Post by Jazzy_Jeff on 2009-07-05
Give people time to help you. It is after all a holiday weekend here in the U.S.

---

### Post by Mark Phelps on 2009-07-06
The standard rule of thumb for bumping posts is no more than once every 24 hours -- not once an hour as you have done.

Show some patience if you want support.

---

### Post by carml on 2009-07-06
It's a shot in the dark: remove your version of wine like before,go to yuor home folder,press ctrl+h to shot hidden files,then check if you find a .wine directory there,if so delete it and reinstall Wine and Rosetta Stone,if you see still any problems let know us.

---

