---
title: "how to install"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by mekanik7777 on 2010-01-30
when i try to install a fressh copy of xbuntu on a machine with 256mb of ram it says i dont have enough memory and i need at least 256?

xbuntu is advertised as being able to install on 128, am i wrong?

---

### Post by NightwishFan on 2010-01-30
Hi, and welcome. 

Can you tell me exactly when the install step fails?

---

### Post by mekanik7777 on 2010-01-30
it never gets past the first screen that resembles the gui

---

### Post by mekanik7777 on 2010-01-30
actually i get past the screen that lets me choose wehter to try or install or memry test ect.. but the next sreen past that is the it

---

### Post by Primefalcon on 2010-01-30
> **mekanik7777 said:**
> it never gets past the first screen that resembles the gui
hmm you might want try installing using the alternate disk you can download it from the same area you got downloaded from in the first place

---

### Post by NightwishFan on 2010-01-30
The alternate installer would be more appropriate to your hardware, as the above poster says. Do you have any questions about Ubuntu or installing?

---

### Post by A&#11375;A on 2010-01-30
For leaner systems you might need to go and use the text based installer

---

### Post by mekanik7777 on 2010-01-30
where do i get the text based installer

---

### Post by NightwishFan on 2010-01-30
[http://www.xubuntu.org/get#karmic](http://www.xubuntu.org/get#karmic)
Chose a location near you, and select the PC Intel x86 Alternate Cd.

Please note, that if you have Windows installed, you will need to shrink the Windows partition to install Ubuntu. If you want to delete Windows, the installer can do so.

---

### Post by mekanik7777 on 2010-01-30
is xbuntu less hungry for cpu and ram

---

### Post by NightwishFan on 2010-01-30
I would say it is about the same. A modern Xubuntu will use more RAM, but manage it better. Perhaps try a Debian live cd. Ubuntu is based on Debian.

[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

---

### Post by Primefalcon on 2010-01-30
The installer for the alternate disk dose use less ram, that's why its recommended for lower systems.

If you want something even lighter, use the alternate disk and install only the base system, no gui (you have this option on the alternate disk)

then just update your repo's
```
sudo aptitude update
```

install your graphics system plus the lxde desktop
```
sudo apt-get install xorg lxde
```

create a folder for backgrounds (this is for the screensaver)
```
sudo mkdir /usr/share/backgrounds
```

and that's it, you'll have a super light fast system, even lighter than xfce (about half the resources!), I've done this for my brother in law, who runs an older system and it runs great

---

