---
title: "wine--programs don't run"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by penguinee on 2009-06-30
Hey guys, I just had a question about wine:

when i try to run poweriso, I get:

```
joe@ubuntu:~$ wine '/home/joe/.wine/dosdevices/c:/Program Files/PowerISO/PowerISO.exe' 
fixme:win:LockWindowUpdate (0x4007a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x4007a), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e9c8d39 (thread 0047), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e9c8d39).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e9c8d39 ESP:0032f180 EBP:0032f1b8 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0032f6c0 EBX:7e9e4ff4 ECX:00146628 EDX:00000000
 ESI:00000001 EDI:00000000
Stack dump:
0x0032f180:  7b8b3b2d 00000001 00000004 7e9e4ff4
0x0032f190:  00146628 0013ba60 0032f1b8 7e9c7cb9
0x0032f1a0:  0013bd40 7fffffff 00146628 7e9e4ff4
0x0032f1b0:  ffff0002 00146628 0032f208 7e9caf9e
0x0032f1c0:  0032f6c0 00000001 7ed8a148 0004007e
0x0032f1d0:  00000001 00000000 7ed8a148 0004007e
Backtrace:
=>1 0x7e9c8d39 in comctl32 (+0x88d39) (0x0032f1b8)
  2 0x7e9caf9e in comctl32 (+0x8af9e) (0x0032f208)
  3 0x7e9d0959 in comctl32 (+0x90959) (0x0032f388)
  4 0x7ed9629a WINPROC_wrapper+0x1a() in user32 (0x0032f3b8)
  5 0x7ed966ea WINPROC_wrapper+0x46a() in user32 (0x0032f3f8)
  6 0x7ed9a652 CallWindowProcW+0x52() in user32 (0x0032f438)
  7 0x004984dd in poweriso (+0x984dd) (0x0032f458)
  8 0x00498b0c in poweriso (+0x98b0c) (0x0032f474)
  9 0x00497af8 in poweriso (+0x97af8) (0x0032f4d4)
  10 0x00497d00 in poweriso (+0x97d00) (0x0032f4f0)
  11 0x7ed9629a WINPROC_wrapper+0x1a() in user32 (0x0032f520)
  12 0x7ed966ea WINPROC_wrapper+0x46a() in user32 (0x0032f560)
  13 0x7ed9b9fd in user32 (+0xbb9fd) (0x0032f5a0)
  14 0x7ed5bf97 in user32 (+0x7bf97) (0x0032f600)
  15 0x7ed60ec5 in user32 (+0x80ec5) (0x0032f660)
  16 0x7ed613dc SendMessageW+0x4c() in user32 (0x0032f6a0)
  17 0x00495135 in poweriso (+0x95135) (0x0032f6ec)
  18 0x0043f27d in poweriso (+0x3f27d) (0x0090ac30)
  19 0x00000001 (0x004bb6b8)
  20 0x0043ef70 in poweriso (+0x3ef70) (0x0043eee0)
  21 0x9090c300 (0x4bb5a8b8)
  22 0x00000000 (0x00000000)
0x7e9c8d39: cmpw	$0,0x0(%edx)
Modules:
Module	Address			Debug info	Name (95 modules)
PE	  400000-  5ce000	Export          poweriso
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7df22000-7df31000	Deferred        libgcc_s.so.1
ELF	7df8c000-7dfbf000	Deferred        uxtheme<elf>
  \-PE	7df90000-7dfbf000	\               uxtheme
ELF	7dfbf000-7dfc3000	Deferred        libgpg-error.so.0
ELF	7dfc3000-7e02c000	Deferred        libgcrypt.so.11
ELF	7e02c000-7e03e000	Deferred        libtasn1.so.3
ELF	7e03e000-7e042000	Deferred        libkeyutils.so.1
ELF	7e042000-7e04b000	Deferred        libkrb5support.so.0
ELF	7e04b000-7e06f000	Deferred        libk5crypto.so.3
ELF	7e06f000-7e101000	Deferred        libkrb5.so.3
ELF	7e101000-7e19e000	Deferred        libgnutls.so.26
ELF	7e19e000-7e1c9000	Deferred        libgssapi_krb5.so.2
ELF	7e1c9000-7e200000	Deferred        libcups.so.2
ELF	7e200000-7e215000	Deferred        midimap<elf>
  \-PE	7e210000-7e215000	\               midimap
ELF	7e215000-7e23d000	Deferred        msacm32<elf>
  \-PE	7e220000-7e23d000	\               msacm32
ELF	7e23d000-7e256000	Deferred        msacm32<elf>
  \-PE	7e240000-7e256000	\               msacm32
ELF	7e256000-7e25c000	Deferred        libattr.so.1
ELF	7e25c000-7e263000	Deferred        libgdbm.so.3
ELF	7e263000-7e2c2000	Deferred        libpulse.so.0
ELF	7e2d1000-7e399000	Deferred        libasound.so.2
ELF	7e39c000-7e3a1000	Deferred        libcap.so.2
ELF	7e3a1000-7e3a8000	Deferred        libasound_module_pcm_pulse.so
ELF	7e3a8000-7e3df000	Deferred        winealsa<elf>
  \-PE	7e3b0000-7e3df000	\               winealsa
ELF	7e3df000-7e3e8000	Deferred        libxcursor.so.1
ELF	7e3e8000-7e3ed000	Deferred        libxfixes.so.3
ELF	7e3ed000-7e3f1000	Deferred        libxcomposite.so.1
ELF	7e3f1000-7e3f9000	Deferred        libxrandr.so.2
ELF	7e3f9000-7e403000	Deferred        libxrender.so.1
ELF	7e403000-7e406000	Deferred        libxinerama.so.1
ELF	7e406000-7e427000	Deferred        imm32<elf>
  \-PE	7e410000-7e427000	\               imm32
ELF	7e427000-7e42c000	Deferred        libxdmcp.so.6
ELF	7e42c000-7e446000	Deferred        libxcb.so.1
ELF	7e446000-7e44a000	Deferred        libxau.so.6
ELF	7e44a000-7e44f000	Deferred        libuuid.so.1
ELF	7e44f000-7e53e000	Deferred        libx11.so.6
ELF	7e53e000-7e54e000	Deferred        libxext.so.6
ELF	7e54e000-7e554000	Deferred        libxxf86vm.so.1
ELF	7e554000-7e56c000	Deferred        libice.so.6
ELF	7e56c000-7e575000	Deferred        libsm.so.6
ELF	7e575000-7e579000	Deferred        libcom_err.so.2
ELF	7e579000-7e582000	Deferred        librt.so.1
ELF	7e584000-7e61f000	Deferred        winex11<elf>
  \-PE	7e590000-7e61f000	\               winex11
ELF	7e64b000-7e672000	Deferred        libexpat.so.1
ELF	7e672000-7e69f000	Deferred        libfontconfig.so.1
ELF	7e69f000-7e6b5000	Deferred        libz.so.1
ELF	7e6b5000-7e72c000	Deferred        libfreetype.so.6
ELF	7e72c000-7e7d2000	Deferred        oleaut32<elf>
  \-PE	7e740000-7e7d2000	\               oleaut32
ELF	7e7d2000-7e7e6000	Deferred        olepro32<elf>
  \-PE	7e7e0000-7e7e6000	\               olepro32
ELF	7e7e6000-7e7fc000	Deferred        libresolv.so.2
ELF	7e80b000-7e82a000	Deferred        iphlpapi<elf>
  \-PE	7e810000-7e82a000	\               iphlpapi
ELF	7e82a000-7e88d000	Deferred        rpcrt4<elf>
  \-PE	7e840000-7e88d000	\               rpcrt4
ELF	7e88d000-7e933000	Deferred        ole32<elf>
  \-PE	7e8a0000-7e933000	\               ole32
ELF	7e933000-7e9f8000	Export          comctl32<elf>
  \-PE	7e940000-7e9f8000	\               comctl32
ELF	7e9f8000-7eb0c000	Deferred        shell32<elf>
  \-PE	7ea10000-7eb0c000	\               shell32
ELF	7eb0c000-7eb43000	Deferred        winspool<elf>
  \-PE	7eb10000-7eb43000	\               winspool
ELF	7eb43000-7ebd7000	Deferred        winmm<elf>
  \-PE	7eb50000-7ebd7000	\               winmm
ELF	7ebd7000-7ec2a000	Deferred        advapi32<elf>
  \-PE	7ebe0000-7ec2a000	\               advapi32
ELF	7ec2a000-7ecca000	Deferred        gdi32<elf>
  \-PE	7ec40000-7ecca000	\               gdi32
ELF	7ecca000-7ee16000	Export          user32<elf>
  \-PE	7ece0000-7ee16000	\               user32
ELF	7ee16000-7ee71000	Deferred        shlwapi<elf>
  \-PE	7ee20000-7ee71000	\               shlwapi
ELF	7ef9b000-7efa7000	Deferred        libnss_files.so.2
ELF	7efa7000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c43000-b7c47000	Deferred        libdl.so.2
ELF	b7c47000-b7daa000	Deferred        libc.so.6
ELF	b7dab000-b7dc4000	Deferred        libpthread.so.0
ELF	b7dd3000-b7f0a000	Deferred        libwine.so.1
ELF	b7f0c000-b7f2a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001a    0
	0000000e    0
	0000000d    0
00000017 
	0000001c    0
	0000001b    0
	00000019    0
	00000018    0
0000001f 
	00000020    0
00000030 
	00000031    0
00000046 (D) C:\Program Files\PowerISO\PowerISO.exe
	00000047    0 <==
Backtrace:
=>1 0x7e9c8d39 in comctl32 (+0x88d39) (0x0032f1b8)
  2 0x7e9caf9e in comctl32 (+0x8af9e) (0x0032f208)
  3 0x7e9d0959 in comctl32 (+0x90959) (0x0032f388)
  4 0x7ed9629a WINPROC_wrapper+0x1a() in user32 (0x0032f3b8)
  5 0x7ed966ea WINPROC_wrapper+0x46a() in user32 (0x0032f3f8)
  6 0x7ed9a652 CallWindowProcW+0x52() in user32 (0x0032f438)
  7 0x004984dd in poweriso (+0x984dd) (0x0032f458)
  8 0x00498b0c in poweriso (+0x98b0c) (0x0032f474)
  9 0x00497af8 in poweriso (+0x97af8) (0x0032f4d4)
  10 0x00497d00 in poweriso (+0x97d00) (0x0032f4f0)
  11 0x7ed9629a WINPROC_wrapper+0x1a() in user32 (0x0032f520)
  12 0x7ed966ea WINPROC_wrapper+0x46a() in user32 (0x0032f560)
  13 0x7ed9b9fd in user32 (+0xbb9fd) (0x0032f5a0)
  14 0x7ed5bf97 in user32 (+0x7bf97) (0x0032f600)
  15 0x7ed60ec5 in user32 (+0x80ec5) (0x0032f660)
  16 0x7ed613dc SendMessageW+0x4c() in user32 (0x0032f6a0)
  17 0x00495135 in poweriso (+0x95135) (0x0032f6ec)
  18 0x0043f27d in poweriso (+0x3f27d) (0x0090ac30)
  19 0x00000001 (0x004bb6b8)
  20 0x0043ef70 in poweriso (+0x3ef70) (0x0043eee0)
  21 0x9090c300 (0x4bb5a8b8)
  22 0x00000000 (0x00000000)

```


maybe I installed ubuntu wrong? I think I installed the 32 bit version...


here's what it says if I try to install utorrent:
```
joe@ubuntu:~$ wine '/home/joe/Desktop/utorrent.exe' 
fixme:heap:HeapSetInformation 0x110000 0 0x479e3c 4
fixme:heap:HeapSetInformation 0x5d0000 0 0x479e3c 4
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_SECURITY_FLAGS: Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_SECURITY_FLAGS: Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_SECURITY_FLAGS: Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
WARNING: Trying to use ICMP (network ping) will fail unless running as root
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_SECURITY_FLAGS: Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_SECURITY_FLAGS: Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB
fixme:heap:RtlCompactHeap (0x5d0000, 0x0) stub


```


Thanks for your help!!

---

### Post by kixome on 2009-06-30
why would you install either of those, there are open source ISO editors, and is there not a Nix* version of utorrent?

---

### Post by Paqman on 2009-06-30
You probably don't need to bother with Wine. It's not something I do a lot of, but i'd be very surprised if there weren't copious native Linux tools for handling ISO files. What exactly did you want to do with them? Maybe someone can recommend a good Linux app that will help you out?

---

### Post by kixome on 2009-06-30
ISO master, it is in the repositories

---

### Post by kixome on 2009-06-30
add/remove and search for iso editor, you have to have third party repo's enabled, as far as torrents, there is a torrent handler installed by default called transmission.

---

### Post by Mick8882003 on 2009-06-30
Another option, which is the way I went. Is to use virtual box, you will need a copy of windows, but most people have these laying around don't they?

Mick

---

### Post by penguinee on 2009-07-01
Hey guys, thanks for your replies.


But still, if I wanted to use wine, could you guys tell me what was wrong? Let's say that I'm not interested in native software (IF, not that I am). What can I do to solve my problem?

Thanks!

---

### Post by Bigtime_Scrub on 2009-07-01
> **penguinee said:**
> Hey guys, thanks for your replies.


But still, if I wanted to use wine, could you guys tell me what was wrong? Let's say that I'm not interested in native software (IF, not that I am). What can I do to solve my problem?

Thanks!

I haven't used Wine in a very loooong time but I'll try. 

First of all how did you install Wine? I would suggest to get whatever is in the repositories because it would be better supported. If you have that Wine.....

I never use the command line to install .exe files in Wine. I let them "unpack" or install the "Windows way." By that I mean simply double click the exe and open with Wine where it can all be saved and ready to go in a nice C: drive. Then when you drop down wine under programs you will see it, right underneath notepad. At least, last time I used it.

---

