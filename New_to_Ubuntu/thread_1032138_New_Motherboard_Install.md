---
title: "New Motherboard Install"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Quarkrad on 2009-01-06
I'm about to buy a new Intel (Intel Dual Core E2160) based motherboard (MSI P4M900M3-L) that has a VIA® P4M900 Chipset.  I will dual boot with winXP but with Ubuntu installed first.  I know with windows I install the OS followed by the chipset drivers and then the apps, What is the procedure with Linux/Ubuntu? I put the live CD in and do a fresh install - do I (I assume so) have to worry about the chipset drivers?

---

### Post by fenian on 2009-01-06
If you are planning on dual booting Ubuntu and Windows I would definately install Windows first it will be far less painful.If you install Windows second it will install the MBR and mess up grub essentially locking you out of Ubuntu this is fixable but kind of a pain.

---

### Post by Elfy on 2009-01-06
The chipset drivers should be dealt with without help - certainly the driver cd will only be good for the xp install. 

Install xp first or you will need to reinstall grub as soon as xp installs.

Assuming you have an empty hdd - partition it before hand with the livecd partitioner - leave an empty space at the front for windows to use will make life easier.

---

