---
title: "Wine Problem"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-03-04
Hi - I'm not sure where this goes, so I guessed it might be here. I installed wine this morning - via .deb if it matters - and I'm experiencing a small problem.

I can run a .exe fine, and any program that just runs from the .exe works as in windows, though Ubuntu still wants to open it with archive manager as standard (I have to right click -> open with to open with Wine)

However, I've installed a few programs via an .exe (into the virtual C:/ drive) and these don't seem to be working for some reason. I've tried running them via desktop icon, through wine -> programs, and also by simply running the whatever.exe in the virtual C:/ drive - all  ways give the same problem. I get a few screen flickers, and one time I had a 'Loading Program' window pop up, but have been unable to load a program this way. Can anyone help?

Please note that at the moment I have no internet access on y ubuntu computer ([http://ubuntuforums.org/showthread.php?t=1038335]("no internet access on my ubuntu computer")) so I can't use apt-get and suchlike.

---

### Post by Sirron on 2009-03-04
First make sure that the programs you're trying to run can actually run in Wine. To check, look them up on [http://appdb.winehq.org/](http://appdb.winehq.org/)

You can change the file type association by opening an exe file's properties dialog, select the "Open With" tab, and select "Wine Windows Program Loader". This should cause all exe files opened by your user to open run via Wine.

---

### Post by yeats on 2009-03-04
> I can run a .exe fine, and any program that just runs from the .exe works as in windows, though Ubuntu still wants to open it with archive manager as standard (I have to right click -> open with to open with Wine)


If you're talking about programs opening from a Firefox download, you can change you associated application by going to Edit > Preferences > Applications in Firefox to set Wine as the default.

> 
However, I've installed a few programs via an .exe (into the virtual C:/ drive) and these don't seem to be working for some reason. I've tried running them via desktop icon, through wine -> programs, and also by simply running the whatever.exe in the virtual C:/ drive - all ways give the same problem. I get a few screen flickers, and one time I had a 'Loading Program' window pop up, but have been unable to load a program this way. Can anyone help?

This really depends on the program.  If it's an older program it might be trying to run in the DOS window (dosbox is a good alternative for those types of programs, by the way).  I would also suggest looking for your program in the Wine App DB:

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Wine is a truly great program, but you have to have realistic expectations about what it does - depending on what you're trying to do, it will work wonderfully or not at all :-).

---

### Post by presence1960 on 2009-03-04
> **Azhtabak said:**
> Hi - I'm not sure where this goes, so I guessed it might be here. I installed wine this morning - via .deb if it matters - and I'm experiencing a small problem.

I can run a .exe fine, and any program that just runs from the .exe works as in windows, though Ubuntu still wants to open it with archive manager as standard (I have to right click -> open with to open with Wine)

However, I've installed a few programs via an .exe (into the virtual C:/ drive) and these don't seem to be working for some reason. I've tried running them via desktop icon, through wine -> programs, and also by simply running the whatever.exe in the virtual C:/ drive - all  ways give the same problem. I get a few screen flickers, and one time I had a 'Loading Program' window pop up, but have been unable to load a program this way. Can anyone help?

Please note that at the moment I have no internet access on y ubuntu computer ([http://ubuntuforums.org/showthread.php?t=1038335]("no internet access on my ubuntu computer")) so I can't use apt-get and suchlike.

This is why I am not too fond of Wine. I ran windows in Ubuntu with Sun Virtual Box for a while. Then my DSL went on the fritz and the techs needed Windows installed. So I went ahead and installed it on my hard drive.** But either way I know ALL my windows software will work.** Wine is very limited in what can run.

---

### Post by yeats on 2009-03-04
> This is why I am not too fond of Wine. I ran windows in Ubuntu with Sun Virtual Box for a while. Then my DSL went on the fritz and the techs needed Windows installed. So I went ahead and installed it on my hard drive. But either way I know ALL my windows software will work. Wine is very limited in what can run.

I heartily agree - VirtualBox is a great option if you need certain Windows programs.

---

### Post by Azhtabak on 2009-03-04
@The wine-not-the-automatic-choice-problem: I mean just a normal exe on the laptop. If I just doubleclick, it defaults to archive manager. Right clicking the .exe gives me an option to run it with wine.

@The not-running-problem: I don't think it's compatablity - the original .exe runs fine, installing the program, but then I can't run the program afterwards. They're new programs that run fine on windows, as normal.

---

### Post by skymera on 2009-03-04
> **Azhtabak said:**
> @The wine-not-the-automatic-choice-problem: I mean just a normal exe on the laptop. If I just doubleclick, it defaults to archive manager. Right clicking the .exe gives me an option to run it with wine.

@The not-running-problem: I don't think it's compatablity - the original .exe runs fine, installing the program, but then I can't run the program afterwards. They're new programs that run fine on windows, as normal.

WINE isn't Windows!
It's merely a compatibility layer that can run EXE files. 
Just because it installed doesn't mean it will work.

Run it from the command line and see the output
```
 wine ~/.wine/drive_c/Program Files/whatever/program.exe 
```

For example

---

### Post by 3rdalbum on 2009-03-04
> **Azhtabak said:**
> @The not-running-problem: I don't think it's compatablity - the original .exe runs fine, installing the program, but then I can't run the program afterwards. They're new programs that run fine on windows, as normal.

That's very common. An installer program is a very simple sort of program; it just copies files into a location. The actual program you are trying to run is literally 1000x more complex than the installer.

It is probably a compatibility problem, or you might need to place some Windows DLLs into the appropriate locations in your user's Wine folder (i.e. /home/azhtabak/.wine/drive_c/Windows/system32/). If you run Wine from a terminal, it might complain that a particular DLL is missing or that it doesn't contain the functions it needs; this is where you find a native Windows DLL and add it.

Wine is an amazing feat of engineering, but it only works with a very limited selection of Windows programs. I'd advise to find Linux alternatives if that's possible, otherwise try doing the DLL trick with Wine, otherwise use Windows inside a virtual machine.

---

### Post by Azhtabak on 2009-03-04
The program in question (Wolflair's Army Builder) is listed on the Wine site as compatible.

That command (though the program wasn't in program files) gives:

```

azhtabak@azhtabak-laptop:~$ wine ~/.wine/drive_c/ArmyBuilderEX/ArmyBuilder.exe

wine: Unhandled page fault on read access to 0x00000004 at address 0x504f75 (thread 0047), starting debugger...

Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00504f75).

Register dump:

 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b

 EIP:00504f75 ESP:0032d08c EBP:00000000 EFLAGS:00210246(   - 00      -RIZP1)

 EAX:ffffff00 EBX:000007f6 ECX:00000000 EDX:00000000

 ESI:016ff760 EDI:00000002

Stack dump:

0x0032d08c:  0040d95b 00000000 000007f6 016ff760

0x0032d09c:  00000000 00000000 00000000 00000000

0x0032d0ac:  00000000 00000000 00000000 00000000

0x0032d0bc:  00000000 00000000 00000000 00000000

0x0032d0cc:  00000000 0032d114 00000040 0032d2a0

0x0032d0dc:  0032d114 b7ec1114 00000040 7bc6bb31

Backtrace:

=>0 0x00504f75 in armybuilder (+0x104f75) (0x00000000)

0x00504f75: movl	0x4(%ecx),%ecx

Modules:

Module	Address			Debug info	Name (81 modules)

PE	  400000-  663000	Export          armybuilder

PE	1ff70000-1ffb6000	Deferred        ltdis13n

PE	1ffc0000-1ffee000	Deferred        ltfil13n

PE	1fff0000-20064000	Deferred        ltkrn13n

ELF	7b800000-7b93f000	Deferred        kernel32<elf>

  \-PE	7b820000-7b93f000	\               kernel32

ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>

  \-PE	7bc10000-7bcb1000	\               ntdll

ELF	7bf00000-7bf04000	Deferred        <wine-loader>

ELF	7e078000-7e0df000	Deferred        rpcrt4<elf>

  \-PE	7e080000-7e0df000	\               rpcrt4

ELF	7e0df000-7e1f1000	Deferred        ole32<elf>

  \-PE	7e100000-7e1f1000	\               ole32

ELF	7e219000-7e24c000	Deferred        uxtheme<elf>

  \-PE	7e220000-7e24c000	\               uxtheme

ELF	7e24c000-7e250000	Deferred        libgpg-error.so.0

ELF	7e250000-7e2b9000	Deferred        libgcrypt.so.11

ELF	7e2b9000-7e2cb000	Deferred        libtasn1.so.3

ELF	7e2cb000-7e2df000	Deferred        libresolv.so.2

ELF	7e2df000-7e2e3000	Deferred        libkeyutils.so.1

ELF	7e2e3000-7e2ec000	Deferred        libkrb5support.so.0

ELF	7e2ec000-7e31e000	Deferred        libcrypt.so.1

ELF	7e31e000-7e3bb000	Deferred        libgnutls.so.26

ELF	7e3bb000-7e3bf000	Deferred        libcom_err.so.2

ELF	7e3bf000-7e3e3000	Deferred        libk5crypto.so.3

ELF	7e3e3000-7e475000	Deferred        libkrb5.so.3

ELF	7e475000-7e49f000	Deferred        libgssapi_krb5.so.2

ELF	7e49f000-7e4d5000	Deferred        libcups.so.2

ELF	7e4d5000-7e4de000	Deferred        libxcursor.so.1

ELF	7e4de000-7e4e3000	Deferred        libxfixes.so.3

ELF	7e4e3000-7e4e7000	Deferred        libxcomposite.so.1

ELF	7e4e7000-7e4ee000	Deferred        libxrandr.so.2

ELF	7e4ee000-7e4f8000	Deferred        libxrender.so.1

ELF	7e4f8000-7e4fe000	Deferred        libxxf86vm.so.1

ELF	7e4fe000-7e501000	Deferred        libxinerama.so.1

ELF	7e501000-7e522000	Deferred        imm32<elf>

  \-PE	7e510000-7e522000	\               imm32

ELF	7e522000-7e527000	Deferred        libxdmcp.so.6

ELF	7e527000-7e540000	Deferred        libxcb.so.1

ELF	7e540000-7e543000	Deferred        libxcb-xlib.so.0

ELF	7e543000-7e632000	Deferred        libx11.so.6

ELF	7e632000-7e641000	Deferred        libxext.so.6

ELF	7e641000-7e659000	Deferred        libice.so.6

ELF	7e659000-7e662000	Deferred        libsm.so.6

ELF	7e66f000-7e70b000	Deferred        winex11<elf>

  \-PE	7e680000-7e70b000	\               winex11

ELF	7e73c000-7e763000	Deferred        libexpat.so.1

ELF	7e763000-7e790000	Deferred        libfontconfig.so.1

ELF	7e790000-7e7a6000	Deferred        libz.so.1

ELF	7e7a6000-7e81c000	Deferred        libfreetype.so.6

ELF	7e81e000-7e821000	Deferred        libxau.so.6

ELF	7e829000-7e84c000	Deferred        mpr<elf>

  \-PE	7e830000-7e84c000	\               mpr

ELF	7e84c000-7e89e000	Deferred        wininet<elf>

  \-PE	7e860000-7e89e000	\               wininet

ELF	7e89e000-7e965000	Deferred        comctl32<elf>

  \-PE	7e8b0000-7e965000	\               comctl32

ELF	7e965000-7e9c3000	Deferred        shlwapi<elf>

  \-PE	7e970000-7e9c3000	\               shlwapi

ELF	7e9c3000-7eb50000	Deferred        shell32<elf>

  \-PE	7e9d0000-7eb50000	\               shell32

ELF	7eb50000-7ec01000	Deferred        comdlg32<elf>

  \-PE	7eb60000-7ec01000	\               comdlg32

ELF	7ec01000-7ec37000	Deferred        winspool<elf>

  \-PE	7ec10000-7ec37000	\               winspool

ELF	7ec37000-7ec8c000	Deferred        advapi32<elf>

  \-PE	7ec40000-7ec8c000	\               advapi32

ELF	7ec8c000-7ed2d000	Deferred        gdi32<elf>

  \-PE	7eca0000-7ed2d000	\               gdi32

ELF	7ed2d000-7ee7c000	Deferred        user32<elf>

  \-PE	7ed50000-7ee7c000	\               user32

ELF	7ef9d000-7efa9000	Deferred        libnss_files.so.2

ELF	7efa9000-7efb4000	Deferred        libnss_nis.so.2

ELF	7efb4000-7efcd000	Deferred        libnsl.so.1

ELF	7efcd000-7eff3000	Deferred        libm.so.6

ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2

ELF	b7d51000-b7d55000	Deferred        libdl.so.2

ELF	b7d55000-b7eb3000	Deferred        libc.so.6

ELF	b7eb4000-b7ecd000	Deferred        libpthread.so.0

ELF	b7eda000-b8015000	Deferred        libwine.so.1

ELF	b8017000-b8034000	Deferred        ld-linux.so.2

Threads:

process  tid      prio (all id:s are in hex)

0000000c 

	00000012    0

	0000000e    0

	0000000d    0

0000000f 

	00000015    0

	00000014    0

	00000011    0

	00000010    0

00000019 

	0000001a    0

00000023 

	00000028   15

	00000027    2

	00000026   15

	00000025   15

	00000024    0

00000029 

	0000002e   15

	0000002d    2

	0000002c   15

	0000002b   15

	0000002a    0

00000031 

	00000036   15

	00000035   15

	00000033    0

	00000032    0

00000039 

	0000003e   15

	0000003d   15

	0000003b    0

	0000003a    0

00000020 

	00000018   15

	0000001c    2

	00000021   15

	00000022   15

	0000001f    0

00000040 

	00000045   15

	00000044   15

	00000013    0

	00000016    0

00000046 (D) C:\ArmyBuilderEX\ArmyBuilder.exe

	00000038    0

	0000001d    0

	00000041    0

	0000003f    0

	00000042    0

	00000009    0

	0000000b    2

	00000047    0 <==

Backtrace:

=>0 0x00504f75 in armybuilder (+0x104f75) (0x00000000)

```

---

### Post by yeats on 2009-03-05
> The program in question (Wolflair's Army Builder) is listed on the Wine site as compatible.

I've found that "compatible" can mean that experienced and determined people have tinkered and toyed with the program until it works, meaning that it doesn't necessarily mean "out-of-the-box compatible."

If you want to dig in and learn the intricacies of Wine so that you can use this particular program, that might be worth it to you, but this is why many gamers continue to use Windows - Wine just can't handle it sometimes.

---

### Post by cwsnyder on 2009-03-05
You may also want to check into the Transgaming Cedega or Codeweaver's Crossover commercial packages for running games under Linux, both of which are based on WINE originally, but have been extended with graphics packages to be more compatible with Windows gaming.

---

