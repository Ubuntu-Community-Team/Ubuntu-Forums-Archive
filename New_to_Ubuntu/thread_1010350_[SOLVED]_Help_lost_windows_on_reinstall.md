---
title: "[SOLVED] Help lost windows on reinstall"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by lift_test on 2008-12-13
Have just done a clean install of Ibex over Hardy, despite XP being detected it does not show up on the boot (grub) menu.  I haven't done anything obviously silly like reformating the hard disk.  XP is still there and intact just missing from the menu.  Please help!

---

### Post by Michael.Godawski on 2008-12-13
hey lift_test, 
can you post your menu.lst
```
cat /boot/grub/menu.lst
```and also
```
sudo fdisk -l
```just to be sure :p.

---

### Post by lift_test on 2008-12-13
I'm using the laptop at the moment so can't cut/paste but the menu.lst just returned what I see on the boot screen Ibex, recovery and memtest.  fdisk -l returns the 3 win partitins plus the 3 Ubuntu partitions

---

### Post by lift_test on 2008-12-13
Copied menu entrys from menu.lst on the laptop and worked (2n try).  Thanks for the assistance, pointed me in the right direction.

---

