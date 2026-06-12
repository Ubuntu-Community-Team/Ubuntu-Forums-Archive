---
title: "Can't access drive?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Paul T. on 2009-03-15
Hi,

Due to disk space, I've installed Ubuntu on my secondary hard drive 'D', now in Ubuntu I can 'mount' and access all my files on 'C' drive, but can't see or access anything on my 'D' drive, which is annoying as all my music and video files are on there.
Is there any way for me to resolve this?

---

### Post by bumanie on 2009-03-15
Can you please post the output of  terminal command> sudo fdisk -lThis will provide a list of your hard drives and partitions.

---

### Post by Paul T. on 2009-03-15
> **bumanie said:**
> Can you please post the output of  terminal commandThis will provide a list of your hard drives and partitions.



Here's the output:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9e8a9e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4121584

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS

---

### Post by ajgreeny on 2009-03-15
Well, I'm sorry to tell you that you don't have ubuntu installed anywhere according to the output you showed.  Both disks are NTFS, therefore probably windows. Can you tell us exactly what you did to install ubuntu; perhaps you used wubi, which adds ubuntu rather like a program installed in windows.  If that is the case, you will need someone else to sort out your problem as I have absolutely no experience of wubi, and am not even sure if ubuntu shows as a separate partition in the *fdisk* command when installed that way.

PS, did you run the *fdisk* command using the live CD or your "installed" ubuntu?

---

### Post by Paul T. on 2009-03-16
> **ajgreeny said:**
> Well, I'm sorry to tell you that you don't have ubuntu installed anywhere according to the output you showed.  Both disks are NTFS, therefore probably windows. Can you tell us exactly what you did to install ubuntu; perhaps you used wubi, which adds ubuntu rather like a program installed in windows.  If that is the case, you will need someone else to sort out your problem as I have absolutely no experience of wubi, and am not even sure if ubuntu shows as a separate partition in the *fdisk* command when installed that way.

PS, did you run the *fdisk* command using the live CD or your "installed" ubuntu?

Yes I used Wubi to install Ubuntu onto my existing Windows based pc with ntfs partitioning.
I ran fdisk via terminal window within Ubuntu.

---

