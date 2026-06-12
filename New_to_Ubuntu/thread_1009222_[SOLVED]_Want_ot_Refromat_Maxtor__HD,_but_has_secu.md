---
title: "[SOLVED] Want ot Refromat Maxtor  HD, but has security lock"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jybeard on 2008-12-12
I want to completely reformat my Maxtor 320GB HD and dedicate it to Linux.  What format do I use? NTFS, Ext3, Fat32?  I have gparted but I get an error when I try to partition the drive.  Please help.

fdisk results

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a1cd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120865   970848081   83  Linux
/dev/sda2          120866      121601     5911920    5  Extended
/dev/sda5          120866      121601     5911888+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           38909       38913       40162+   b  W95 FAT32
/dev/sdb2               1       38908   312528478+  83  Linux

---

### Post by LowSky on 2008-12-12
to reparttion you need to un mount the drive, very simple to do from gparted just right click  on the partition and click on unmonunt, best choice for linux is EXT3 or EXT2. If you are going ot share it with Windows computers use FAT32 or NTFS

---

### Post by tomtom1982 on 2008-12-12
If you want to format your HDD, it has to be mounted.

Please make sure that it is mounted.

And if you only want to use it with linux, you should choose the ext3-Format.

---

### Post by LowSky on 2008-12-12
> **tomtom1982 said:**
> If you want to format your HDD, it has to be mounted.

Please make sure that it is mounted.
 

From gparted a mounted hard drive cannot be formated. It will have nice little lock icon next to it if its mounted. unmounting it will get rid of the lock and it can be formated. I just did this last week.

---

### Post by Duck2006 on 2008-12-12
> **tomtom1982 said:**
> If you want to format your HDD, it has to be mounted.

Please make sure that it is mounted.

And if you only want to use it with linux, you should choose the ext3-Format.

When you format a hard drive with gparted it has to be unmounted.

Some info on gparted.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

If you are having trouble with formatting the drive with the live cd of ubuntu then try the live cd of gparted or parted magic.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

