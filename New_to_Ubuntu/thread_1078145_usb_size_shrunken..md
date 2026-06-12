---
title: "usb size shrunken."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by sathiskumarmsk on 2009-02-23
i have a 4GB USB..but it shows its size as 22mb..i tried to format in LINUX and windows ..but nothing happened..please help me..

---

### Post by x33a on 2009-02-23
post the output of
```
df -h
sudo fdisk -l
```

---

### Post by swoody on 2009-02-23
I had the same problem with my 2GB USB. You may want to try booting from a Live CD (if you have one) with the USB attached. Go through the install steps until you get to the "Partition Disks" Stage, and go to "Manual". Does it show any free space on the USB drive? If it shows Unused space along with the 22mb filesystem on your USB, select the filesystem on there, and select "Expand", and see if that works.

My USB was down to 512kb when I did this, and it worked like a charm! Let me know if it works or not :)

---

### Post by sathiskumarmsk on 2009-02-23
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1004M  2.0M 1002M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1004M  2.0M 1002M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  100K 1004M   1% /var/run
varlock              1004M  4.0K 1004M   1% /var/lock
udev                 1004M  2.8M 1001M   1% /dev
tmpfs                1004M  428K 1004M   1% /dev/shm
rootfs               1004M  508M  497M  51% /
/dev/scd0             4.1G  4.1G     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1004M   12K 1004M   1% /tmp

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64f0cd16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       30400   203230282+   f  W95 Ext'd (LBA)
/dev/sda5            5100       11473    51199123+   7  HPFS/NTFS
/dev/sda6           11474       11537      514048+  83  Linux
/dev/sda7           11538       14087    20482843+  83  Linux
/dev/sda8           14088       14609     4192933+  82  Linux swap / Solaris
/dev/sda9           14610       22258    61440561    7  HPFS/NTFS
/dev/sda10          22259       30400    65400583+   7  HPFS/NTFS

Disk /dev/sdb: 23 MB, 23068672 bytes
255 heads, 63 sectors/track, 2 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081779

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           2       16033+   5  Extended

---

### Post by sathiskumarmsk on 2009-02-23
> **woody86 said:**
> I had the same problem with my 2GB USB. You may want to try booting from a Live CD (if you have one) with the USB attached. Go through the install steps until you get to the "Partition Disks" Stage, and go to "Manual". Does it show any free space on the USB drive? If it shows Unused space along with the 22mb filesystem on your USB, select the filesystem on there, and select "Expand", and see if that works.

My USB was down to 512kb when I did this, and it worked like a charm! Let me know if it works or not :)

The installer encountered an error copying files to the hard disk:

[Errno 28] No space left on device

This is due to there being insufficient disk space for the install to complete on the target partition.  Please run the installer again and select a larger partition to install into.

---

### Post by swoody on 2009-02-23
> **sathiskumarmsk said:**
> The installer encountered an error copying files to the hard disk:

[Errno 28] No space left on device

This is due to there being insufficient disk space for the install to complete on the target partition.  Please run the installer again and select a larger partition to install into.

Did you actually try to install Ubuntu to the USB? I just meant to use the partitioning editor to try and expand the size of the USB, not actually go all the way through and install it. When you're at the Partitioning stage, select "Manual" to go to manual partitioning, and then select the USB drive filesystem, and see if there's any "Unused Space" that is not part of the partition on the USB

---

