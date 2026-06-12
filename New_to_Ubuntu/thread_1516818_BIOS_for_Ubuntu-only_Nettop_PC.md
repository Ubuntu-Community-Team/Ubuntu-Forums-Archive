---
title: "BIOS for Ubuntu-only Nettop PC"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Ionic-user on 2010-06-24
I'm a Ubuntu newbie, a total one, and I still use my faithful old PowerMac. I'm starting out on the Linux, Open Source path with a separate machine, an Asrock Ion 330HT. As soon as I started it up I slipped the Lucid Lynx LiveCD in and everything went perfectly, the nettop functions very well. However, I'm now wondering if I've made a fundemental error in not setting the BIOS first, using the CD that came with the machine. Initially, I took it that all the drivers and BIOS stuff on it was for Windows (which I don't want anything to do with) only, since only these systems were mentioned and there was nothing about Linux at all. Am I right in supposing that and can I let sleeping dogs lie, or must I go back and do the whole installation process again? I presume there must be a minimum of BIOS in the firmware or the machine wouldn't work at all.

Any help with this very basic question much appreciated, particularly from users of this type of machine.

---

### Post by solar george on 2010-06-24
The BIOS is unrelated to the drivers disk which you got (and correctly assumed was just for windows) and will be pre-setup on a chip on the motherboard as without it nothing else on the machine could function correctly.

---

### Post by cascade9 on 2010-06-24
BIOS = basic input/output system. For all intents, you can think of the BIOS as 'boot firmware', and it is not OS specific. 

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

In every case I've run across, you dont need a driver CD to play with BIOS settings. In the BIOS you can normally do things like specify boot order, configure drives, IDE and SATA channels, turn on/off serial and parallel ports, set the power saving modes, set RAM timings, etc. 

Normally you have to hit 'del' or one of the function keys to enter the BIOS (you do this when the machine 1st starts, if you get as far as GRUB its gone to far). 

All the drivers of the CD will be windows drivers.

---

### Post by Ionic-user on 2010-06-24
Thanks for that, Solar George and Cascade 9; you've set my mind to rest.

---

