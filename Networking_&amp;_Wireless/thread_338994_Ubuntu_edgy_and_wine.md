---
title: "Ubuntu edgy and wine"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by Pietje on 2007-01-15
i have installed ubuntu edgy with latest patches and wine 0.9.29. i use a application called osfinancials, [www.osfinancials.org](www.osfinancials.org), this installs, but does not run. Strangly enough, it does run when using suse and wine, so it seems to be related to the combination of ubuntu edgy and wine.

When I run the exe, osfinancials.exe, I get the following errors:

sudo wine osFinancials.exe 
fixme:winspool:WINSPOOL_EnumPrinters We don't handle PRINTER_ENUM_CONNECTIONS
fixme:winspool:WINSPOOL_EnumPrinters We don't handle PRINTER_ENUM_CONNECTIONS
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b8407b0 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc2fc4c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc2fc4c ESP:0033f5c4 EBP:0033f628 EFLAGS:00200282(   - 00      - -IS1)
 EAX:0033f5d0 EBX:7bc78904 ECX:00110020 EDX:0033f9ac
 ESI:0033f9ac EDI:0033f634
Stack dump:
0x0033f5c4:  00110000 00000002 7ed46754 c0000025
0x0033f5d4:  00000001 0033f9ac 7ed01a3c 00000000
0x0033f5e4:  00000000 00173440 0000002e 0033f630
0x0033f5f4:  000003ff 00000000 00000000 0000000b
0x0033f604:  0033fa54 00402c57 0033fa54 004059c5
0x0033f614:  013b8648 0033f630 00405a08 7bc2fc00
Backtrace:
=>1 0x7bc2fc4c __regs_RtlRaiseException+0x4c() in ntdll (0x0033f628)
  2 0x7bc65863 in ntdll (+0x55863) (0x0033f988)
  3 0x7bc2f236 RtlRaiseException+0x6() in ntdll (0x0033fa00)
  4 0x0043f986 in osfinancials (+0x3f986) (0x0033fe78)
  5 0x00440650 in osfinancials (+0x40650) (0x0033fea4)
  6 0x00821a2b in osfinancials (+0x421a2b) (0x0033fec8)
  7 0x004055b7 in osfinancials (+0x55b7) (0x0033ff08)
  8 0x7b8703ae in kernel32 (+0x503ae) (0x0033ffe8)
  9 0xb7e09587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc2fc4c __regs_RtlRaiseException+0x4c in ntdll: subl $4,%esp
Modules:
Module  Address                 Debug info      Name (94 modules)
PE      400000-11a1000  Export          osfinancials
ELF     7b800000-7b91c000       Export          kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Export          ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e06e000-7e083000       Deferred        midimap<elf>
  \-PE  7e070000-7e083000       \               midimap
ELF     7e0a9000-7e0c1000       Deferred        msacm32<elf>
  \-PE  7e0b0000-7e0c1000       \               msacm32
ELF     7e0c1000-7e0fd000       Deferred        wineoss<elf>
  \-PE  7e0d0000-7e0fd000       \               wineoss
ELF     7e0fd000-7e101000       Deferred        libgpg-error.so.0
ELF     7e101000-7e14f000       Deferred        libgcrypt.so.11
ELF     7e14f000-7e162000       Deferred        libtasn1.so.3
ELF     7e162000-7e190000       Deferred        libcrypt.so.1
ELF     7e19b000-7e20a000       Deferred        libgnutls.so.13
ELF     7e20a000-7e239000       Deferred        libcups.so.2
ELF     7e266000-7e298000       Deferred        uxtheme<elf>
  \-PE  7e270000-7e298000       \               uxtheme
ELF     7e29a000-7e29f000       Deferred        libxfixes.so.3
ELF     7e29f000-7e2a8000       Deferred        libxcursor.so.1
ELF     7e2a8000-7e2c6000       Deferred        ximcp.so.2
ELF     7e2c6000-7e2c9000       Deferred        libxrandr.so.2
ELF     7e2c9000-7e2d1000       Deferred        libxrender.so.1
ELF     7e2d1000-7e2d4000       Deferred        libxinerama.so.1
ELF     7e2d4000-7e2db000       Deferred        libdrm.so.2
ELF     7e2db000-7e34a000       Deferred        libgl.so.1
ELF     7e34a000-7e34f000       Deferred        libxdmcp.so.6
ELF     7e34f000-7e352000       Deferred        libxau.so.6
ELF     7e352000-7e41b000       Deferred        libx11.so.6
ELF     7e41b000-7e428000       Deferred        libxext.so.6
ELF     7e428000-7e42d000       Deferred        libxxf86vm.so.1
ELF     7e42d000-7e445000       Deferred        libice.so.6
ELF     7e445000-7e4d2000       Deferred        winex11<elf>
  \-PE  7e450000-7e4d2000       \               winex11
ELF     7e4d2000-7e4f0000       Deferred        libexpat.so.1
ELF     7e4f0000-7e51f000       Deferred        libfontconfig.so.1
ELF     7e51f000-7e533000       Deferred        libz.so.1
ELF     7e533000-7e59d000       Deferred        libfreetype.so.6
ELF     7e59d000-7e62b000       Deferred        winmm<elf>
  \-PE  7e5b0000-7e62b000       \               winmm
ELF     7e62b000-7e63f000       Deferred        lz32<elf>
  \-PE  7e630000-7e63f000       \               lz32
ELF     7e63f000-7e658000       Deferred        version<elf>
  \-PE  7e650000-7e658000       \               version
ELF     7e658000-7e66c000       Deferred        shfolder<elf>
  \-PE  7e660000-7e66c000       \               shfolder
ELF     7e66c000-7e68e000       Deferred        oledlg<elf>
  \-PE  7e670000-7e68e000       \               oledlg
ELF     7e68e000-7e6ad000       Deferred        mpr<elf>
  \-PE  7e6a0000-7e6ad000       \               mpr
ELF     7e6ad000-7e6c9000       Deferred        imm32<elf>
  \-PE  7e6b0000-7e6c9000       \               imm32
ELF     7e6c9000-7e761000       Deferred        oleaut32<elf>
  \-PE  7e6e0000-7e761000       \               oleaut32
ELF     7e761000-7e77e000       Deferred        hhctrl<elf>
  \-PE  7e770000-7e77e000       \               hhctrl
ELF     7e77e000-7e7b0000       Deferred        winspool<elf>
  \-PE  7e790000-7e7b0000       \               winspool
ELF     7e7b0000-7e7c3000       Deferred        libresolv.so.2
ELF     7e7c3000-7e7e1000       Deferred        iphlpapi<elf>
  \-PE  7e7d0000-7e7e1000       \               iphlpapi
ELF     7e7e1000-7e835000       Deferred        rpcrt4<elf>
  \-PE  7e7f0000-7e835000       \               rpcrt4
ELF     7e835000-7e8ce000       Deferred        ole32<elf>
  \-PE  7e840000-7e8ce000       \               ole32
ELF     7e8ce000-7e926000       Deferred        shlwapi<elf>
  \-PE  7e8e0000-7e926000       \               shlwapi
ELF     7e926000-7ea18000       Deferred        shell32<elf>
  \-PE  7e940000-7ea18000       \               shell32
ELF     7ea18000-7eab8000       Deferred        comdlg32<elf>
  \-PE  7ea20000-7eab8000       \               comdlg32
ELF     7eab8000-7eac3000       Deferred        libgcc_s.so.1
ELF     7eac3000-7eac5000       Deferred        xlcutf8load.so.2
ELF     7eac5000-7eace000       Deferred        libsm.so.6
ELF     7ebad000-7ec63000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec63000       \               gdi32
ELF     7ec63000-7ed9b000       Deferred        user32<elf>
  \-PE  7ec80000-7ed9b000       \               user32
ELF     7ed9b000-7ee5b000       Deferred        comctl32<elf>
  \-PE  7eda0000-7ee5b000       \               comctl32
ELF     7ee5b000-7eea1000       Deferred        advapi32<elf>
  \-PE  7ee70000-7eea1000       \               advapi32
ELF     7efae000-7efb9000       Deferred        libnss_files.so.2
ELF     7efb9000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff5000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca2000-b7cab000       Deferred        libnss_compat.so.2
ELF     b7cac000-b7cb0000       Deferred        libdl.so.2
ELF     b7cb0000-b7de4000       Deferred        libc.so.6
ELF     b7de4000-b7df7000       Deferred        libpthread.so.0
ELF     b7e02000-b7f13000       Export          libwine.so.1
ELF     b7f15000-b7f30000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\osFinancials\osFinancials.exe
        00000009    0 <==

Can anybody help?

---

### Post by rowanparker on 2007-01-15
What's this to do with networking?

---

### Post by Pietje on 2007-01-16
Hoops, you are right, i meant to post this to the desktop section, but seem to have made a mistake sorry..

---

### Post by rowanparker on 2007-01-16
> **Pietje said:**
> Hoops, you are right, i meant to post this to the desktop section, but seem to have made a mistake sorry..
That's quite alright, a mod will move it.


In answer to your question:
If you cannot get maybe you could try crossover (google it) or installing Windows in VMware.

---

