---
title: "root file system not defined"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by anico on 2009-05-08
Hello! I'm trying to install ubuntu on a friend's computer that just got a brand new hard-drive. Whenever i try to install ubuntu it will say in the partition section "root file system not defined" ..it will not allow me to select anything in that menu..what can i do? I've looked for similar threads but i cannot understand the right procedure! thank you so much

---

### Post by mcduck on 2009-05-08
Sounds like you are using the manual partitioning option? You'll have to select the partition you wish to use for Ubuntu, and set it's mount point to "/".

---

### Post by anico on 2009-05-08
that's the problem.. i'm not selecting manual or anything.. on step 4 of the installation only that error comes up. There's never a choice for manual. :confused:

---

### Post by shadowlands on 2009-05-08
> **anico said:**
> that's the problem.. i'm not selecting manual or anything.. on step 4 of the installation only that error comes up. There's never a choice for manual. :confused:

Hey I was not ask that question either. I have a new hard drive and havig a heck of a time getting ubuntu to work.

---

### Post by ACupOfCoffee on 2009-05-08
Hard drive connected properly?

---

### Post by taurus on 2009-05-08
Open a terminal, Applications -> Accessories -> Terminal, and post the output of this command.

```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by anico on 2009-05-08
ok i tried sudo fdisk -l (lower case l)  and nothing came up.. i tried sudo fdisk -1 (one) and this showed up.. i know you specified the lower case l but nothing appeared in terminal.
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by taurus on 2009-05-08
Go into the BIOS and see if the system even detects that new harddrive.

If it does, then turn on the AHCI and see what is the output from a terminal after you boot Ubuntu LiveCD.

```
sudo fdisk -l
```

---

