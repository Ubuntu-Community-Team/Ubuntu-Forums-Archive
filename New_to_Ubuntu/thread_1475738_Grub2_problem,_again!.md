---
title: "Grub2 problem, again!"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Paul T. on 2010-05-07
Hi,

after upgrading to 10.04 I lost the ability to boot into XP, just got a blank screen. I eventually solved the problem by re-installing XP MBR, then re-installing Grub. Things have been fine now for past few days, however today I installed the first updates for 10.04 and now I'm back with the above problem, why??

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10d99b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11151    89570376    7  HPFS/NTFS
/dev/sda2           11152       30401   154625625    f  W95 Ext'd (LBA)
/dev/sda5           11152       30136   152496981   83  Linux
/dev/sda6           30137       30401     2128581   82  Linux swap / Solaris

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4121584

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS
paul@paul-desktop:~$

---

