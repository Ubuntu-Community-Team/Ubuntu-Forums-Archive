---
title: "Grub"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by sharks on 2011-05-02
So, I got Windows 7, Mac, Ubuntu installed. It's listing both windows & Ubuntu on the list, but wouldn't show Mac OS X on the grub menu.

How do I add it? :D
```
~$ sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf92af92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1364    10956298+   7  HPFS/NTFS
/dev/sda2            1365        9730    67199864+   f  W95 Ext'd (LBA)
/dev/sda5            1365        2716    10859908+   7  HPFS/NTFS
/dev/sda6            3920        3952      265041   82  Linux swap / Solaris
/dev/sda7            3953        5864    15358108+   7  HPFS/NTFS
/dev/sda8            5866        7777    15358108+   7  HPFS/NTFS
/dev/sda9            7778        9730    15687441    7  HPFS/NTFS
/dev/sda10           2717        3919     9663066   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x652d1f0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       39026   313476313+   7  HPFS/NTFS
/dev/sdb2           46937       60801   111370612+   f  W95 Ext'd (LBA)
/dev/sdb3           39027       46936    63537075   af  HFS / HFS+
/dev/sdb5           46937       51191    34178256    7  HPFS/NTFS
/dev/sdb6           51192       60801    77192293+   7  HPFS/NTFS

Partition table entries are not in disk order

```
That's my list.. I just want to add MAC OS X to the grub, help please? thanks!

---

### Post by wilee-nilee on 2011-05-02
Not sure if it is more likely to get you fixed if possible, but you might report yourself to be moved to the apple part of the forum.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

