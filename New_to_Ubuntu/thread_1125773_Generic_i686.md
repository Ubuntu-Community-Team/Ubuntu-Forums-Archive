---
title: "Generic i686"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by neo.patrix on 2009-04-14
Dear Ubuntu,

I have installed Ubuntu 8.10 just today (but I am not new to it, think I had followed up till Feisty Fawn last year). Anyway I downloaded iso-i386 , made a CD & installed it. My old Ext3
/ NTFS partition system is good enough, so just had to format / & /usr mountable partition. 

I really wanted to test miktex-2.8-beta but the .deb package that I tried to install gives me incompatible architecture error. Now that is i386 package

On executing uname -a , I get

```
Linux patrix-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

```

Is something wrong here? I am not sure why it is generic i686, I am very sure that the iso which I downladed is i386 , bootable CD says i386. I hope only my memory has gone rusty concerning some critical info.

---

### Post by nwadams on 2009-04-14
i believe i686 is standard 32 bit now...right???
I don't know what has happened here if this is not right. I use 64 bit so i can't really help more than that

---

### Post by neo.patrix on 2009-04-15
may be :lolflag: but still iso which I downloaded says i386.

---

### Post by nwadams on 2009-04-15
ya, i did more research and it seems 386 is the standard, so i have no idea. I'm sorry

---

### Post by LowSky on 2009-04-15
i686 is your processor type. The Live CD supports processors as far back as i386. Also your 686 processor is backward compatible, so it should work.
Try downloading the MiKTeX Tools 2.8 Beta 2 TGZ file
you will have to install it by hand but it might work

---

### Post by neo.patrix on 2009-04-18
:popcorn: 

Thanx for replies guys, I installed it from source :lolflag:

```
sudo checkinstall
```

Currently I am facing troubles of making MikTex or Texlive 

to recongnize dam fonts for compiling same files that I used

to compile on Windows with same version of Miktex. ](*,)](*,)

Bascially , I want to move my entire TeXing system from

Windows to Ubuntu , so I can use SVN for my TeXing projects.


But , very unfortunately that is not happening MikTeX keeps

getting stuck on ttf2pk not found, although I can use it from 

command line and > The ______ font source file not found or

> ttf2pk not found!

Somehow miktex fails to find paths , mabye even texmf.cnf , sure 

kpathsea-debug showed me that. I have absolutely no clue where miktex

is looking when ttf2pk is in god dam /usr/bin & softlink at 

/usr/local/bin....where miktex puts its binaries !!!

---

