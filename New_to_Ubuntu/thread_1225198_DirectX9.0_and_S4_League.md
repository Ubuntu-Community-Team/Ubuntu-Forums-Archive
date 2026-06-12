---
title: "DirectX9.0 and S4 League?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Marrkle on 2009-07-28
So I read about it, and S4 league only works in Windows 98 compatibility mode in Wine (other modes display 'patcher.exe doesn't work' or something like that). Which fits with the Wine test, but when I run it in Windows 98 compatibility mode DirectX doesn't run with Wine. So I kind of have a dilemma here. How do I modify the DirectX 9.0 such that it runs under Windows 98 compatibility mode in Wine?

---

### Post by braete on 2009-07-28
for 9.04 the rating in the appdb is garbage.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15142&iTestingId=40713]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15142&iTestingId=40713")
don't bother. if over there they cant make it work, i dont think you have a better chance

---

### Post by Marrkle on 2009-07-28
> **braete said:**
> for 9.04 the rating in the appdb is garbage.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15142&iTestingId=40713](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15142&iTestingId=40713)


I use 8.04, and I'm trying to either get:
a) Direct X 9.0 to run in Wine for Windows 98 compatibility
b) S4 patcher.exe to run in Wine for Windows XP compatibility.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14532](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14532)

I'm trying to install the 'dll-overrides', but I have no idea what they are. 

Also
 'Requires you to set windows-version to win98 or HackShield will prevent the game from starting.' 
Which is basically what I did, but we have the directX problem. I'm thinking the 'dll-overrides' have something to do with it.


'required me to manually start the s4_patcher.exe' 
I'm not sure if this is needed, but if installing the dll-overrides doesn't work, then I might try this.

---

### Post by braete on 2009-07-28
try win2000 compatibility mode

---

### Post by Marrkle on 2009-07-28
> **braete said:**
> try win2000 compatibility mode

Windows 2000 returns the same 'patcher_s4.exe' error as Windows XP.

Also, how do I get the 'dll-overrides', whatever they are?

---

### Post by braete on 2009-07-28
[http://www.winehq.org/docs/wineusr-guide/config-wine-main]("http://www.winehq.org/docs/wineusr-guide/config-wine-main")

---

### Post by Marrkle on 2009-07-28
> **braete said:**
> [http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)


Alright, so which DLL's do I install? It's got to be something related to with the DirectX checking which version it is, etc.

---

### Post by braete on 2009-07-28
> **Marrkle said:**
> Alright, so which DLL's do I install?

i realy dont know ... i saw on winehq (for the open beta client) that the maintainer did it by using native dlls but he didnt say witch.

it's hackshields fault (from what i see)
it doesnt "see" the native dlls, but the ones built in wine and it thinks you try to hack the game.

---

### Post by Marrkle on 2009-07-28
> **braete said:**
> i realy dont know ... i saw on winehq (for the open beta client) that the maintainer did it by using native dlls but he didnt say witch.

it's hackshields fault (from what i see)
it doesnt "see" the native dlls, but the ones built in wine and it thinks you try to hack the game.

Okay, fine, if you can't solve that avenue, how about making DirectX compatible with Windows 98?

---

### Post by braete on 2009-07-28
wine translates dx calls in opengl

you dont make "dx compatibile with win98"

the maintainer proposed setting env os to win 98/2000 to fool hackshield into accepting the built in ddls offered by wine.

you could try to run s4patcher using the CLI, it might hold some hints on what ddl you need.
if that doesnt work you could try running it in a VM (not a good ideea but you might give it a go)

---

### Post by Marrkle on 2009-07-28
> **braete said:**
> wine translates dx calls in opengl

you dont make "dx compatibile with win98"

the maintainer proposed setting env os to win 98/2000 to fool hackshield into accepting the built in ddls offered by wine.

you could try to run s4patcher using the CLI, it might hold some hints on what ddl you need.
if that doesnt work you could try running it in a VM (not a good ideea but you might give it a go)

How do I run s4patcher using the CLI? what is a CLI?

---

### Post by braete on 2009-07-28
cli is command line interface, terminal
you open a terminal, browse to the location of the game ```
cd ~/.wine/drive_c ...(the install location)
```and you run it using wine ```
wine s4_patcher.exe
```

---

### Post by Marrkle on 2009-07-28
```



fixme:shdocvw:PersistStreamInit_InitNew (0x144778)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32ebc0:3; TargetFrameName 0x32ebb0:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32c190
fixme:iphlpapi:NotifyAddrChange (Handle 0x23de928, overlapped 0x23de930): stub
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x144818)->((null) 1 0x32cfb8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 25 2 0x32cfcc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32cfcc (nil))
fixme:shdocvw:ClientSite_GetContainer (0x144818)->(0x32d008)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32d0cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d15c)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32ebf0:3; TargetFrameName 0x32ebe0:8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 29 2 0x32f11c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x144818)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClientSite_GetContainer (0x144818)->(0x32ef80)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x144818)->(0xb7f11251)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 25 2 0x32eeb4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32eeb4 (nil))
fixme:mshtml:HlinkTarget_SetBrowseContext (0x146260)->((nil))
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x144818)->((null) 1 0x32dce8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 25 2 0x32dcfc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32dcfc (nil))
fixme:shdocvw:ClientSite_GetContainer (0x144818)->(0x32dd38)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32ddfc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32de8c)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f458:3; TargetFrameName 0x32f448:8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 29 2 0x32f11c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x144818)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f044)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f044)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32f0fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 29 2 0x32f10c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 28 2 0x32f044 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x144818)->(0x32f498)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x144818)->(0xb7f11251)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 25 2 0x32f3cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32f3cc (nil))
fixme:mshtml:HlinkTarget_SetBrowseContext (0x146260)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x144818)->((null) 1 0x32e188 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 25 2 0x32e19c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32e19c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x144818)->(0x32e1d8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e29c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x2492888)->(L"" L"" 0 0x32e2d4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 29 2 0x32f11c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x144818)
fixme:shdocvw:ClientSite_GetContainer (0x144818)->(0x32f498)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x144818)->(0xb7f11251)
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 25 2 0x32f3cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 26 2 0x32f3cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x144818)->((null) 28 2 0x32f484 (nil))
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x144778)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x146248)->((nil))
fixme:shdocvw:OleObject_Close (0x144778)->(1)
wine: Unhandled page fault on write access to 0xfe832287 at address 0x8000e1 (thread 000b), starting debugger...
fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
Unhandled exception: page fault on write access to 0xfe832287 in 32-bit code (0x008000e1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:008000e1 ESP:0032f248 EBP:0032f260 EFLAGS:00210202(  R- --  I   - - - )
 EAX:7df4da87 EBX:7df608b4 ECX:c000000d EDX:00808ec4
 ESI:00144778 EDI:00144778
Stack dump:
0x0032f248:  00808ec4 0032f238 0032f280 00442e10
0x0032f258:  7df608b4 00000000 0032f290 7df55fa4
0x0032f268:  00144778 0041064d 7183bb47 0003007a
0x0032f278:  00808d70 00410ec7 0041fd1b 00410ec7
0x0032f288:  00808d70 7ed29c00 0032f2e0 00406fe1
0x0032f298:  00144778 00808d70 0041088a 00808d70
Backtrace:
=>0 0x008000e1 (0x0032f260)
  1 0x7df55fa4 in shdocvw (+0x25fa4) (0x0032f290)
  2 0x00406fe1 in patcher_s4 (+0x6fe1) (0x0032f2e0)
  3 0x004126c6 in patcher_s4 (+0x126c6) (0x0032f374)
  4 0x0040ea1c in patcher_s4 (+0xea1c) (0x0032f394)
  5 0x00410e6e in patcher_s4 (+0x10e6e) (0x0032f3fc)
  6 0x00410efb in patcher_s4 (+0x10efb) (0x0032f41c)
  7 0x7ed3575a WINPROC_wrapper+0x1a() in user32 (0x0032f44c)
  8 0x7ed35e3e WINPROC_wrapper+0x6fe() in user32 (0x0032f48c)
  9 0x7ed3b1fb in user32 (+0xab1fb) (0x0032f4cc)
  10 0x7ecfbe51 in user32 (+0x6be51) (0x0032f52c)
  11 0x7ecfffcd in user32 (+0x6ffcd) (0x0032f58c)
  12 0x7ed0043a SendMessageW+0x4a() in user32 (0x0032f5cc)
  13 0x7ed2b55c in user32 (+0x9b55c) (0x0032f66c)
  14 0x7ed2b49c in user32 (+0x9b49c) (0x0032f70c)
  15 0x7ed2b2ff DestroyWindow+0x1df() in user32 (0x0032f74c)
  16 0x004108db in patcher_s4 (+0x108db) (0x0032f7a4)
  17 0x004031cb in patcher_s4 (+0x31cb) (0x0032fe60)
  18 0x00442392 in patcher_s4 (+0x42392) (0x0032ff08)
  19 0x7b877379 in kernel32 (+0x57379) (0x0032ffe8)
  20 0xb7dfbb1d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x008000e1: popl    0x808e4800(%eax)
Modules:
Module    Address            Debug info    Name (138 modules)
PE      330000-  338000    Deferred        xpcom
PE      3a0000-  3db000    Deferred        nspr4
PE      3e0000-  3f5000    Deferred        nssutil3
PE      400000-  5db000    Export          patcher_s4
PE      910000-  9d3000    Deferred        js3250
PE      9e0000-  abe000    Deferred        nss3
PE      bd0000- 1dbb000    Deferred        xul
PE     1dc0000- 1dca000    Deferred        plds4
PE     1dd0000- 1dda000    Deferred        plc4
PE     1de0000- 1e01000    Deferred        smime3
PE     1e10000- 1e89000    Deferred        sqlite3
PE     1e90000- 1eb9000    Deferred        ssl3
PE    10000000-1002e000    Deferred        patchexplib
ELF    7b800000-7b95e000    Export          kernel32<elf>
  \-PE    7b820000-7b95e000    \               kernel32
ELF    7bc00000-7bcae000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcae000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7db06000-7db11000    Deferred        libgcc_s.so.1
ELF    7db11000-7db17000    Deferred        libnss_dns.so.2
ELF    7db17000-7db2a000    Deferred        t2embed<elf>
  \-PE    7db20000-7db2a000    \               t2embed
ELF    7db2a000-7db3e000    Deferred        dwmapi<elf>
  \-PE    7db30000-7db3e000    \               dwmapi
ELF    7db3e000-7db52000    Deferred        midimap<elf>
  \-PE    7db40000-7db52000    \               midimap
ELF    7db52000-7db77000    Deferred        msacm32<elf>
  \-PE    7db60000-7db77000    \               msacm32
ELF    7db77000-7db8e000    Deferred        msacm32<elf>
  \-PE    7db80000-7db8e000    \               msacm32
ELF    7db8e000-7dc51000    Deferred        libasound.so.2
ELF    7dc63000-7dc99000    Deferred        winealsa<elf>
  \-PE    7dc70000-7dc99000    \               winealsa
ELF    7dc99000-7dcac000    Deferred        lz32<elf>
  \-PE    7dca0000-7dcac000    \               lz32
ELF    7dcac000-7dcc5000    Deferred        version<elf>
  \-PE    7dcb0000-7dcc5000    \               version
ELF    7dcc5000-7dcdd000    Deferred        usp10<elf>
  \-PE    7dcd0000-7dcdd000    \               usp10
ELF    7dcdd000-7dcf0000    Deferred        msimg32<elf>
  \-PE    7dce0000-7dcf0000    \               msimg32
ELF    7dcf0000-7dd0e000    Deferred        iphlpapi<elf>
  \-PE    7dd00000-7dd0e000    \               iphlpapi
ELF    7dd0e000-7dd28000    Deferred        wsock32<elf>
  \-PE    7dd10000-7dd28000    \               wsock32
ELF    7dd28000-7ddc2000    Deferred        winmm<elf>
  \-PE    7dd30000-7ddc2000    \               winmm
ELF    7ddc2000-7de2e000    Deferred        msvcrt<elf>
  \-PE    7ddd0000-7de2e000    \               msvcrt
ELF    7de2e000-7dee9000    Deferred        mshtml<elf>
  \-PE    7de40000-7dee9000    \               mshtml
ELF    7dee9000-7df2d000    Deferred        urlmon<elf>
  \-PE    7def0000-7df2d000    \               urlmon
ELF    7df2d000-7df6d000    Export          shdocvw<elf>
  \-PE    7df30000-7df6d000    \               shdocvw
ELF    7df77000-7df7b000    Deferred        libgpg-error.so.0
ELF    7df7b000-7dfc8000    Deferred        libgcrypt.so.11
ELF    7dfc8000-7dfd8000    Deferred        libtasn1.so.3
ELF    7dfd8000-7dfeb000    Deferred        libresolv.so.2
ELF    7dfeb000-7dfee000    Deferred        libkeyutils.so.1
ELF    7dfee000-7dff6000    Deferred        libkrb5support.so.0
ELF    7dff6000-7e028000    Deferred        libcrypt.so.1
ELF    7e028000-7e09e000    Deferred        libgnutls.so.13
ELF    7e09e000-7e0c1000    Deferred        libk5crypto.so.3
ELF    7e0c1000-7e14e000    Deferred        libkrb5.so.3
ELF    7e14e000-7e177000    Deferred        libgssapi_krb5.so.2
ELF    7e177000-7e1aa000    Deferred        libcups.so.2
ELF    7e1af000-7e1b2000    Deferred        libnss_mdns4_minimal.so.2
ELF    7e1bc000-7e1d4000    Deferred        spoolss<elf>
  \-PE    7e1c0000-7e1d4000    \               spoolss
ELF    7e1d4000-7e1f1000    Deferred        localspl<elf>
  \-PE    7e1e0000-7e1f1000    \               localspl
ELF    7e23f000-7e272000    Deferred        uxtheme<elf>
  \-PE    7e250000-7e272000    \               uxtheme
ELF    7e272000-7e27b000    Deferred        libxcursor.so.1
ELF    7e27b000-7e280000    Deferred        libxfixes.so.3
ELF    7e280000-7e283000    Deferred        libxcomposite.so.1
ELF    7e283000-7e289000    Deferred        libxrandr.so.2
ELF    7e289000-7e291000    Deferred        libxrender.so.1
ELF    7e291000-7e296000    Deferred        libxxf86vm.so.1
ELF    7e296000-7e299000    Deferred        libxinerama.so.1
ELF    7e299000-7e2b8000    Deferred        imm32<elf>
  \-PE    7e2a0000-7e2b8000    \               imm32
ELF    7e2b8000-7e2bd000    Deferred        libxdmcp.so.6
ELF    7e2bd000-7e2d5000    Deferred        libxcb.so.1
ELF    7e2d5000-7e2d7000    Deferred        libxcb-xlib.so.0
ELF    7e2d7000-7e2da000    Deferred        libxau.so.6
ELF    7e2da000-7e3c1000    Deferred        libx11.so.6
ELF    7e3c1000-7e3cf000    Deferred        libxext.so.6
ELF    7e3cf000-7e3e7000    Deferred        libice.so.6
ELF    7e3e7000-7e3ef000    Deferred        libsm.so.6
ELF    7e3fc000-7e3ff000    Deferred        libcom_err.so.2
ELF    7e401000-7e49b000    Deferred        winex11<elf>
  \-PE    7e410000-7e49b000    \               winex11
ELF    7e4af000-7e4d0000    Deferred        libexpat.so.1
ELF    7e4d0000-7e4fa000    Deferred        libfontconfig.so.1
ELF    7e50c000-7e579000    Deferred        libfreetype.so.6
ELF    7e579000-7e65b000    Deferred        oleaut32<elf>
  \-PE    7e590000-7e65b000    \               oleaut32
ELF    7e65b000-7e6c6000    Deferred        rpcrt4<elf>
  \-PE    7e670000-7e6c6000    \               rpcrt4
ELF    7e6c6000-7e7bd000    Deferred        ole32<elf>
  \-PE    7e6e0000-7e7bd000    \               ole32
ELF    7e7bd000-7e7e6000    Deferred        oledlg<elf>
  \-PE    7e7c0000-7e7e6000    \               oledlg
ELF    7e7e6000-7e81b000    Deferred        winspool<elf>
  \-PE    7e7f0000-7e81b000    \               winspool
ELF    7e81b000-7e8cc000    Deferred        comdlg32<elf>
  \-PE    7e820000-7e8cc000    \               comdlg32
ELF    7e8cc000-7e990000    Deferred        comctl32<elf>
  \-PE    7e8d0000-7e990000    \               comctl32
ELF    7e990000-7eb1d000    Deferred        shell32<elf>
  \-PE    7e9a0000-7eb1d000    \               shell32
ELF    7eb1d000-7eb79000    Deferred        shlwapi<elf>
  \-PE    7eb30000-7eb79000    \               shlwapi
ELF    7eb79000-7ebce000    Deferred        advapi32<elf>
  \-PE    7eb90000-7ebce000    \               advapi32
ELF    7ebce000-7ec6d000    Deferred        gdi32<elf>
  \-PE    7ebe0000-7ec6d000    \               gdi32
ELF    7ec6d000-7edb3000    Export          user32<elf>
  \-PE    7ec90000-7edb3000    \               user32
ELF    7edb3000-7edd5000    Deferred        mpr<elf>
  \-PE    7edc0000-7edd5000    \               mpr
ELF    7edd5000-7edea000    Deferred        libz.so.1
ELF    7edfc000-7ee4f000    Deferred        wininet<elf>
  \-PE    7ee10000-7ee4f000    \               wininet
ELF    7ee4f000-7ee7c000    Deferred        ws2_32<elf>
  \-PE    7ee60000-7ee7c000    \               ws2_32
ELF    7ef9c000-7efa7000    Deferred        libnss_files.so.2
ELF    7efa7000-7efb1000    Deferred        libnss_nis.so.2
ELF    7efb1000-7efc9000    Deferred        libnsl.so.1
ELF    7efc9000-7efee000    Deferred        libm.so.6
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b7c76000-b7c7a000    Deferred        libdl.so.2
ELF    b7c7a000-b7dc9000    Deferred        libc.so.6
ELF    b7dca000-b7de2000    Deferred        libpthread.so.0
ELF    b7df4000-b7f2f000    Export          libwine.so.1
ELF    b7f31000-b7f4d000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
    00000027    0
    00000023    0
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 
    00000019    0
00000045 
    00000046    0
00000047 (D) C:\ProgramFiles\alaplaya\S4League\patcher_s4.exe
    00000025    0
    00000029    0
    00000024    0
    0000000c    0
    0000000d    0
    0000000b    0 <==
00000028 
    0000002a    0
0000002d 
    0000002e    0
Backtrace:
=>0 0x008000e1 (0x0032f260)
  1 0x7df55fa4 in shdocvw (+0x25fa4) (0x0032f290)
  2 0x00406fe1 in patcher_s4 (+0x6fe1) (0x0032f2e0)
  3 0x004126c6 in patcher_s4 (+0x126c6) (0x0032f374)
  4 0x0040ea1c in patcher_s4 (+0xea1c) (0x0032f394)
  5 0x00410e6e in patcher_s4 (+0x10e6e) (0x0032f3fc)
  6 0x00410efb in patcher_s4 (+0x10efb) (0x0032f41c)
  7 0x7ed3575a WINPROC_wrapper+0x1a() in user32 (0x0032f44c)
  8 0x7ed35e3e WINPROC_wrapper+0x6fe() in user32 (0x0032f48c)
  9 0x7ed3b1fb in user32 (+0xab1fb) (0x0032f4cc)
  10 0x7ecfbe51 in user32 (+0x6be51) (0x0032f52c)
  11 0x7ecfffcd in user32 (+0x6ffcd) (0x0032f58c)
  12 0x7ed0043a SendMessageW+0x4a() in user32 (0x0032f5cc)
  13 0x7ed2b55c in user32 (+0x9b55c) (0x0032f66c)
  14 0x7ed2b49c in user32 (+0x9b49c) (0x0032f70c)
  15 0x7ed2b2ff DestroyWindow+0x1df() in user32 (0x0032f74c)
  16 0x004108db in patcher_s4 (+0x108db) (0x0032f7a4)
  17 0x004031cb in patcher_s4 (+0x31cb) (0x0032fe60)
  18 0x00442392 in patcher_s4 (+0x42392) (0x0032ff08)
  19 0x7b877379 in kernel32 (+0x57379) (0x0032ffe8)
  20 0xb7dfbb1d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_CONNECT_RETRIES 5
fixme:wininet:InternetSetOptionW Option 12 STUB
fixme:wininet:InternetSetOptionW Option 12 STUB
fixme:reg:GetNativeSystemInfo (0x1da4bec) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:thread:NtSetInformationThread info class 17 not supported yet
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1deb4b5): Stub!
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
Terminated


```Again, the same error seems to come up.

---

### Post by braete on 2009-07-28
darn, that's a big output 

ok, i am no wine specialist but you could start by getting the dlls stated there (shdocvw, dwmapi, mshtml, urlmon, wininet)

other then that i recommand you to go to winehq forum or here at wine subforum and seek "profesional" help. there they know what they are doing a lot more than me.

---

### Post by Marrkle on 2009-07-28
> **braete said:**
> darn, that's a big output 

ok, i am no wine specialist but you could start by getting the dlls stated there (shdocvw, dwmapi, mshtml, urlmon, wininet)

other then that i recommand you to go to winehq forum or here at wine subforum and seek "profesional" help. there they know what they are doing a lot more than me.


I typed in the 5 dlls into my library. No luck

---

### Post by braete on 2009-07-28
to override dlls you dont just type there the name, you need to have those files in ur system32 (usualy) folder.
still that output doesnt say much to me(not to mention is huge).
you should realy try winehq forum/ubuntu wine subforum.

---

### Post by Bigfootmech on 2009-09-08
Heya, Install S4 League normally with wine (let it do the desktop shortcut for ease of use).

Go to the folder (Browse C Drive -> program files -> alaplaya) and run pather_s4.exe manually otherwise it appears and disappears and the launcher tells you it's already running but it isn't - let it run for a while (it took me quite a bit but you can see the progress).

After it's installed it'll start to load in WINDOWS 98 MODE but it'll get stuck sorta 2/3 of the way.

To remedy this google the 2 words 'directx wine' and you eventually get to

[http://www.wine-reviews.net/wine-reviews/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)

This tells you how to install DirectX on wine for the first time, or enable it's update. You need this for any good game to work on wine (ie valve games). 

Install DirectX on wine following the guide to the letter (PS: if you don't have the DLL's for the system 32 folder - like me - you can download them by googling and going to the dll-files.com link to download them for free), then after the end, switch from Windows 2000 mode to Windows 98 and run the installer again.

HEY PRESTO.

S4 League works now.

So far the only error I see is my +10%exp mask thing makes some sort of head graphical error, but not sure why this is.


I managed to pull this off with the latest stable version of everything: Ubuntu 9.04 Jaunty Jackalope - booted from a memory stick none the less; Wine 1.01 (installed with applications -> add/remove); DirectX Mar 2009 (installed manually with a guide); S4 (looking at the version.ini) 1044

I did this just before posting so the 8 Sep 2009

EDIT: Hopefully this miniguide will help lost souls like I was before completing this and make it easier, quicker, and less painful to play S4 :).

---

