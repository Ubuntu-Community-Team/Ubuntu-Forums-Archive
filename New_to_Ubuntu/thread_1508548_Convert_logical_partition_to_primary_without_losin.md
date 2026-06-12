---
title: "Convert logical partition to primary without losing data"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by BugBuster on 2010-06-13
Hi this is the geometry of my hard-drive,
```
$sudo sfdisk -d /dev/sda

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 41945652, Id= 7, bootable
/dev/sda2 : start= 41945776, size=446446289, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 41945778, size=335549592, Id= 7
/dev/sda6 : start=377495433, size= 89931807, Id=83
/dev/sda7 : start=467427303, size= 20964762, Id=83

```

```

$sudo fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed12a1aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       30401   223223144+   f  W95 Ext'd (LBA)
/dev/sda5            2612       23498   167774796    7  HPFS/NTFS
/dev/sda6           23499       29096    44965903+  83  Linux
/dev/sda7           29097       30401    10482381   83  Linux

```

Here I want to convert the 160GB partition '/dev/sda5' which is in an extended partition to a primary partition and keep sda6 and sda7 in an extended partition as it is.

Here is a similar post that has a solution as well;

[http://ubuntuforums.org/showthread.php?t=1008458](http://ubuntuforums.org/showthread.php?t=1008458)

I want someone here to help me adapt this solution to my drive geometry.

---

### Post by oldfred on 2010-06-13
I have never done it but have seen one or two links. The one you have by caljohnsmith is a good  example.

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

# The partition table is located at sectors 447--512 on the drive.
# A sector = 512 bytes.
Here is the specification of the partition table format:
[http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3](http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3)

---

