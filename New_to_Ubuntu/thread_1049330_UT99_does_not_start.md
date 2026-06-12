---
title: "UT99 does not start"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Zopiac on 2009-01-24
Mounted the UT99 .iso and ran the installer. However, when i open it it does not start. Here is the output:

```
zopiac@zopiac-desktop:~$ wine /home/zopiac/.wine/drive_c/UnrealTournament/System/UnrealTournament.exe 
wine: Unhandled privileged instruction at address 0x40aae4 (thread 0009), starting debugger...
Unhandled exception: privileged instruction in 32-bit code (0x0040aae4).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040aae4 ESP:0033fd98 EBP:0033fe7c EFLAGS:00010293(   - 00      RISA1C)
 EAX:0033008a EBX:00000000 ECX:00000067 EDX:00400000
 ESI:7b8824d0 EDI:00400000
Stack dump:
0x0033fd98:  00410fed 00000000 00400000 00000067
0x0033fda8:  7ffdf000 00113bf7 7b8b7ff4 00560f30
0x0033fdb8:  7bc90ff4 00000800 005605a8 0033fde4
0x0033fdc8:  7bc44781 00000180 00000094 00000005
0x0033fdd8:  00000001 00000a28 00000002 76726553
0x0033fde8:  20656369 6b636150 00003220 00000800
Backtrace:
=>0 0x0040aae4 in unrealtournament (+0xaae4) (0x0033fe7c)
  1 0x0041ace2 in unrealtournament (+0x1ace2) (0x0033ff08)
  2 0x7b878a98 in kernel32 (+0x58a98) (0x0033ffe8)
  3 0xb7eaad37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0040aae4: outl	%eax,$0x99
Modules:
Module	Address			Debug info	Name (49 modules)
PE	  400000-  44b000	Export          unrealtournament
ELF	7b800000-7b940000	Export          kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcad000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e89c000-7e8a5000	Deferred        libxcursor.so.1
ELF	7e8a5000-7e8aa000	Deferred        libxfixes.so.3
ELF	7e8aa000-7e8ae000	Deferred        libxcomposite.so.1
ELF	7e8ae000-7e8b5000	Deferred        libxrandr.so.2
ELF	7e8b5000-7e8bf000	Deferred        libxrender.so.1
ELF	7e8bf000-7e8c5000	Deferred        libxxf86vm.so.1
ELF	7e8c5000-7e8c8000	Deferred        libxinerama.so.1
ELF	7e8c8000-7e8e9000	Deferred        imm32<elf>
  \-PE	7e8d0000-7e8e9000	\               imm32
ELF	7e8e9000-7e8ee000	Deferred        libxdmcp.so.6
ELF	7e8ee000-7e907000	Deferred        libxcb.so.1
ELF	7e907000-7e90a000	Deferred        libxcb-xlib.so.0
ELF	7e90a000-7e90d000	Deferred        libxau.so.6
ELF	7e90d000-7e9fc000	Deferred        libx11.so.6
ELF	7e9fc000-7ea0b000	Deferred        libxext.so.6
ELF	7ea0b000-7ea23000	Deferred        libice.so.6
ELF	7ea23000-7ea2c000	Deferred        libsm.so.6
ELF	7ea3e000-7eada000	Deferred        winex11<elf>
  \-PE	7ea50000-7eada000	\               winex11
ELF	7eaff000-7eb26000	Deferred        libexpat.so.1
ELF	7eb26000-7eb53000	Deferred        libfontconfig.so.1
ELF	7eb65000-7eb7b000	Deferred        libz.so.1
ELF	7eb7b000-7ebf1000	Deferred        libfreetype.so.6
ELF	7ec03000-7ec18000	Deferred        lz32<elf>
  \-PE	7ec10000-7ec18000	\               lz32
ELF	7ec18000-7ec33000	Deferred        version<elf>
  \-PE	7ec20000-7ec33000	\               version
ELF	7ec33000-7ec88000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec88000	\               advapi32
ELF	7ec88000-7ed29000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed29000	\               gdi32
ELF	7ed29000-7ee78000	Deferred        user32<elf>
  \-PE	7ed40000-7ee78000	\               user32
ELF	7ef98000-7efa4000	Deferred        libnss_files.so.2
ELF	7efa4000-7efaf000	Deferred        libnss_nis.so.2
ELF	7efaf000-7efc8000	Deferred        libnsl.so.1
ELF	7efc8000-7efee000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7d15000-b7d19000	Deferred        libdl.so.2
ELF	b7d19000-b7e77000	Deferred        libc.so.6
ELF	b7e78000-b7e91000	Deferred        libpthread.so.0
ELF	b7ea3000-b7fda000	Export          libwine.so.1
ELF	b7fdc000-b7ff9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\UnrealTournament\System\UnrealTournament.exe
	00000009    0 <==
0000000c 
	00000016    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>0 0x0040aae4 in unrealtournament (+0xaae4) (0x0033fe7c)
  1 0x0041ace2 in unrealtournament (+0x1ace2) (0x0033ff08)
  2 0x7b878a98 in kernel32 (+0x58a98) (0x0033ffe8)
  3 0xb7eaad37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

Program terminates after that. No window is opened, or anything.


I tried to use a loki installer, but it just says:

```
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/zopiac/.setup27460: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Could anyone help?

---

