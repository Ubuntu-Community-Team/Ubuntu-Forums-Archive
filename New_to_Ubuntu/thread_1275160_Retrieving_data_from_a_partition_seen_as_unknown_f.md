---
title: "Retrieving data from a partition seen as unknown file type"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by pognonec on 2009-09-25
I already posted this, but I guess I was not clear, since I did not get a solution. I am trying again, with other words:

My HD crashed. Using ddrescue, I got my crashed disk transfered to an empty (and larger) ext3 partition on an external HD (sdb1). But following ddrescue, the ext3 partition of the receiving partition is now gone. Instead, gparted sees it as an "unknown file system".

$ sudo fdisk -ls /dev/sdb1 gives the following, indicating that my crashed data is there:

```
philippe@Ubuntu:~$ sudo fdisk -ls /dev/sdb1
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: ignoring extra data in partition table 7
Warning: invalid flag 0x1f10 of partition table 7 will be corrected by w(rite)

Disk /dev/sdb1: 185.8 GB, 185899521024 bytes
255 heads, 63 sectors/track, 22600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1          27      216846   de  Dell Utility
/dev/sdb1p2              28        1333    10485760    7  HPFS/NTFS
/dev/sdb1p3   *        1333        6061    37975586    7  HPFS/NTFS
/dev/sdb1p4            6062       19458   107604011    f  W95 Ext'd (LBA)
/dev/sdb1p5           19131       19458     2620416   dd  Unknown
/dev/sdb1p6            6062       18594   100671291   83  Linux
/dev/sdb1p7   ?      242591      344140   815687134   55  EZ-Drive

Partition table entries are not in disk order
```

MY QUESTION IS:
How can I have access to these data, knowing the partition they are on is of "unknown file type"?

Thanx!

---

### Post by hailtothethief on 2009-09-25
If you know what type of filesystem the old data was on, you could try to force a mount using its filesystem type.

Run the following as root:

```
mkdir /mnt/crashed
mount -t fstype /dev/sdb1p5 /mnt/crashed
```

If it worked your data should show up in /mnt/crashed. **You will have to replace fstype with the old filesystem type** (likely to be vfat, ext3, or ntfs)

---

### Post by solitaire on 2009-09-25
get "Testdisk" from the repositories. It can scan the "unknown" partition and try and recover it.

---

### Post by pognonec on 2009-09-26
hailtothethief, thank you for your answer. Unfortunately, that did not make it:
```
philippe@Ubuntu:~$ sudo mount -t ext3 /dev/sdb1p5 /mnt/crashed
[sudo] password for philippe: 
mount: special device /dev/sdb1p5 does not exist
``` 

Solitaire, your suggestion of trying "Testdisk was the good one: that solved my problem. Thank you SO much! what a pleasure to see my data reappearing :-)
This Testdisk is really a very nice and useful piece of software.

---

