---
title: "Can't boot on XP machine"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Muni2 on 2009-04-15
I am new to Linux and have been trying to download Ubuntu without success. I have XP installed on this computer with no partition and 55G of space available. I have also defragged this drive.

My machine:
Pentium D 2.66G
504MG RAM
75G IDE hard Drive
Intel 82865G Graphic Controller

I have tried using the Wubi installation with several different downloads and it won't boot up. I have also downloaded the LiveCD from Ubuntu and I cannot get it to boot off the CD. Any help would be appreciated.

---

### Post by supersonicdarky on 2009-04-15
If you mean the computer ignores the cd, it may be a boot order issue.

---

### Post by |Mitch| on 2009-04-15
set the cd as boot first in the bios and then reboot with the cd in the drive

Before XP loads it should say to hit delete(whatever key) to enter set-up, do that and change the boot order to look for the cd-rom first. Save & exit, I recommend leaving it like that. 

Reboot with the Ubuntu disk in the drive and set-up partitions as desired...

---

### Post by Muni2 on 2009-04-15
I hit F8 and selected boot from CD, but it still boots from XP. The CD drive is working and recognized.

---

### Post by |Mitch| on 2009-04-15
Was the cd in the drive when you rebooted? If it was, you canceled & exited instead of saved & exited when leaving the bios.

---

