---
title: "error 17 grub lvm patrition"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by ge0rgi0 on 2009-11-24
HELLO EVERYBODY.. THIS IS MY VERY FIRST POST ON A FORUM EVER

i have a quite complicated setup:  
1 one partition with windows and wubi installed ubuntu
2 after that i created a new partition with gparted , installed lvm  and  transferred my wubi ubuntu installation there.

The problem is that the boot grub menu (grub 0.97)  does not boot from the new partition.

I changed           root  ()/ubuntu/disks      to        root (hd0,1)
[FONT=Verdana]in the   [/FONT] /boot/grub/menu.lst    [FONT=Verdana]file, and still nothing happened

what i think is that the mount point of the new partition is wrong because after typing [FONT=System]fdisc -l[/FONT] i find out the following:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c0d0c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11748    94365778+   7  HPFS/NTFS
/dev/sda2           11752       14338    20780077+  83  Linux
/dev/sda3           14339       14593     2048287+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb006032b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

[/FONT]

---

