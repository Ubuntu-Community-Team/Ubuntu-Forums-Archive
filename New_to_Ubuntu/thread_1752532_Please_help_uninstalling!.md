---
title: "Please help uninstalling!"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by kjjj11223344 on 2011-05-07
I recently wanted to try out Ubuntu and I love it (version 11.04). My original plan was to install it on a different partition from Windows 7, but I accidentally clicked to install alongside Windows (like WUXI) does. I want to delete this linux installation so I can dool boot it with Windows but with Ubuntu on a separate partition not on the same Windows partition. Unfortunately, I do not see the option to uninstall Ubuntu under add/remove programs because I did not use the WUXI installer, and I simply can not delete the partition because this would delete my windows also. Is there any way to uninstall Ubuntu without messing up my windows partition?

---

### Post by garvinrick4 on 2011-05-07
While in Ubuntu open a terminal and run this:
```
sudo fdisk -l
``` (lower case L)

Post outcome here:

---

### Post by kjjj11223344 on 2011-05-07
> **garvinrick4 said:**
> While in Ubuntu open a terminal and run this:
```
sudo fdisk -l
``` (lower case L)

Post outcome here:
Here are my results:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac507bb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       33194   266524816    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           33194      115075   657705600    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4          115075      121602    52427777    5  Extended
/dev/sda5          115075      120560    44057600   83  Linux
/dev/sda6          120560      121602     8369152   82  Linux swap / Solaris

---

### Post by garvinrick4 on 2011-05-07
Ubuntu is on a seperate partition, sda5 is your Ubuntu linux install. (not a Wubi install)
Do you want to know how big the partition is.
```
sudo parted -l
``` (lower case L)

---

### Post by garvinrick4 on 2011-05-07
Your grub menu:
```
grep menuentry /boot/grub/grub.cfg
```
Enjoy your Ubuntu
There is a post installation guide in my signature and a .pdf book.

---

### Post by kjjj11223344 on 2011-05-07
> **garvinrick4 said:**
> Your grub menu:
```
grep menuentry /boot/grub/grub.cfg
```
Enjoy your Ubuntu
There is a post installation guide in my signature and a .pdf book.
Okay thanks for the help, I appreciate it.

---

