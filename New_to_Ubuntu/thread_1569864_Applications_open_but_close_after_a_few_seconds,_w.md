---
title: "Applications open but close after a few seconds, why ?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by l1n0x on 2010-09-07
Hi,
I just finished installing Ubuntu 10.04.1 but I already have a "strange" issue, at least for me because I'm a newbie in the Ubuntu world.

The problem is that when I open some application, it close after one or two seconds and I can't do anything on it :confused:

This issue happens with "Simple Scan", "Xsane Image Scanner" and "Color Profiles (ICC Profile Installer)".

I don't know if this happens with other application because I didn't check all applications that were installed with Ubuntu.

Before you ask here is my hardware and software listing: 
HARDWARE: Asus P4C800 Deluxe, P4 3Ghz, 2 Gb Memory, HDD Samsung 2TB, EIzo CG222W monitor, Ricoh Aficio IS01 scanner, HP 6p printer.
SOFTWARE: Ubuntu 10.04.1, Ubuntu tweak, VLC, Color Profiles (ICC Profile Installer), DjView4, ChmSee, NVidia driver (version 173), UFRaw, BleachBit and OpenOffice Database.

Any suggestion to help me, please ?

TIA ;)

---

### Post by DougieFresh4U on 2010-09-07
Try to open program from terminal and see what errors it's telling you

---

### Post by l1n0x on 2010-09-07
Hi, 

Thank you for your help :)

I tried for the three application and the result is the same for all:
"Segmentation fault"

What does this mean ?

---

### Post by bredman on 2010-09-07
This basically means that the code is not compatible with your Operating System.

This commonly happens if you try to run a 64-bit program on a 32-bit system.

Do you know if you are using a 32-bit or 64-bit version of Ubuntu?

---

### Post by l1n0x on 2010-09-07
Well I think it is a 32 bit because I installed a Ubuntu 9.04 (32 bit) and made the update to 10.04.1 (with Update Manager).

BTW, two of the three application were installed by Ubuntu ("Simple Scan" and "Xsane Image Scanner") not by me.

---

### Post by l1n0x on 2010-09-07
Case closed !

Unfortunately I just found that the problem is a "conflict" with my scanner :(

Anyway, thank you all for your help  ;)

---

### Post by Jazzy_Jeff on 2010-09-07
If you are still having problems with other programs you may want to do a clean install. Upgrades don't always go so well. Just make sure all your important things are backed up.

---

