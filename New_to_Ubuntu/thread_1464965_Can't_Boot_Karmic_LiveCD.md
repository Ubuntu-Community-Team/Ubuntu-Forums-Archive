---
title: "Can't Boot Karmic LiveCD"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by mulluysavage on 2010-04-28
New DVD RW drive.

New CMOS battery.

Re-loaded GRUB

***

On attempt to boot from HD: "NON-SYSTEM DISK ERROR. INSERT SYSTEM DISK AND PRESS ENTER" (not verbatim)

Will not boot Ubuntu 9.10 Live CD

Will boot Parted Magic

Will boot Xubuntu 8.04 LTS


I'm thinking something is up with my boot sector - like, it's physically messed up. I'm thinking about cloning my OS partition to a new HD and installing GRUB there and trying that.

Totally puzzled by the fact that it won't boot the 9.10 live cd, which it did before, and I installed from. I don't know, maybe it's scratched.

---

### Post by cariboo on 2010-04-29
Have you tried starting in safe-graphics mode? To do so, press F4 at the menu screen, the select try or install.

---

### Post by madjr on 2010-04-29
well just wait for lucid, probably cd got bad

---

### Post by D3jan on 2010-04-29
i have the same problem , and i change in BIOS , sata controler to AHCI , default was IDE

---

### Post by Steven_S on 2010-04-29
I'm a bit confused... is the problem that you are unable to boot from HD, or that you are unable to boot from LiveCD? 

If it is the latter, and other LiveCD's work fine (as I understand from your post), you need to test if the .iso you have and the disk are good. Instructions for that are here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

---

