---
title: "Need to install 'Mono&quot;"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-24
How do I install this? I tried via terminal 'install mono,' but that didn't work. I also looked in Synaptic, but there are tons of files with "mono" in them, and I don't know what to download.

I'm trying to install RippedWire, and the deb installer says RW needs mono as a dependency.

---

### Post by x33a on 2009-01-24
maybe this could help:

[http://pkg-mono.alioth.debian.org/](http://pkg-mono.alioth.debian.org/)

---

### Post by directhex on 2009-01-24
Mono is heavily split up, to prevent bloat (i.e. you only install as much Mono as you need).

Unfortunately, SourceForce is completely broken for me today, so I can't determine the required packages. However, judging by the screenshots, I think you might already have everything you need (Mono is installed by default in Ubuntu, to run F-Spot and Tomboy). Try running it from a console (mono foo.exe), and if it moans that there's a missing assembly, install the package containing it

---

### Post by adobrakic on 2009-01-24
Yeah, i read a couple of things that said Mono is pre-installed. And yet, the RippedWire app. still keeps saying it needs mono to run. -_-
I'll just try to find another program like it. :p

---

### Post by directhex on 2009-01-24
> **adobrakic said:**
> Yeah, i read a couple of things that said Mono is pre-installed. And yet, the RippedWire app. still keeps saying it needs mono to run. -_-
I'll just try to find another program like it. :p

Without a specific error, I can't help

And I'm unable to download it to try myself.

---

### Post by bgerlich on 2009-01-24
[http://linuxcrypt.net/?p=119](http://linuxcrypt.net/?p=119)

Full instructions.

---

### Post by directhex on 2009-01-24
> **bgerlich said:**
> [http://linuxcrypt.net/?p=119](http://linuxcrypt.net/?p=119)

Full instructions.

```
............................................________
....................................,.-‘”...................``~.,
.............................,.-”...................................“-.,
.........................,/...............................................”:,
.....................,?......................................................\,
.................../...........................................................,}
................./......................................................,:`^`..}
.............../...................................................,:”........./
..............?.....__.........................................:`.........../
............./__.(.....“~-,_..............................,:`........../
.........../(_....”~,_........“~,_....................,:`........_/
..........{.._$;_......”=,_.......“-,_.......,.-~-,},.~”;/....}
...........((.....*~_.......”=-._......“;,,./`..../”............../
...,,,___.\`~,......“~.,....................`.....}............../
............(....`=-,,.......`........................(......;_,,-”
............/.`~,......`-...............................\....../\
.............\`~.*-,.....................................|,./.....\,__
,,_..........}.>-._\...................................|..............`=~-,
.....`=~-,_\_......`\,.................................\
...................`=~-,,.\,...............................\
................................`:,,...........................`\..............__
.....................................`=-,...................,%`>--==``
........................................_\..........._,-%.......`\
...................................,<`.._|_,-&``................`\
```

Depending on "mono" is COMPLETELY and UTTERLY broken. The "monofix" package in the above instructions is a workaround, but the original software is UTTERLY beyond help if they think "mono" is the right thing to depend on

---

