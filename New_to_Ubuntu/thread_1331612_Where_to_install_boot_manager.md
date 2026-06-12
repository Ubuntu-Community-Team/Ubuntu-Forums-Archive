---
title: "Where to install boot manager?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by BT1 on 2009-11-19
When I install the boot manager in text mode, should I install it on "(hd0)" or "/sda1"?

---

### Post by teward on 2009-11-19
install to (hd0).

---

### Post by Hospadar on 2009-11-19
Just a little technical note, they are (most likely) the same thing.
grub tends to use the (hd0) notation since that notation represents a little more accurately what grub is getting from your bios (i.e., your hardware), while udev (the linux kernel module that handles hardware setup at boot time, or when stuff gets plugged in, like a usb drive), creates devices named like sda1.

Typically, udev will set (hd0) to sda, (hd1) to sdb, etc, and the first partition of hd0, (hd0,0) will be sda1, the second partition will be sda2, etc.

A couple things to notice, there will be a device sda, as well as sda1, sda2, etc (however many partitions are on the drive).  sda1, sda2 allow software to get at just a certain partition, while sda allows software to get at the whole drive (for example a program which manages partitions, like gparted, would open sda).

Sooo, the practical upshot of all this is, if you're wondering, "which hard drive is (hd0), or vice-versa?", typically the (hd#) and the /dev/sd[a-z] will correspond, i.e. (hd0)=sda, (hd1)=sdb, etc.  The same goes for partitions on a drive, (hd0,0) = sda1, (hd0,1) sda2, (hd1,0) = sdb1.

---

