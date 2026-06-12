---
title: "Nothing happens when mounting Volume (could mount pendrive/CD/DVD)"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by 0z0 on 2009-03-09
i searched the forum but none seem to be similar (or i didnt find), when trying to mount ntfs volume nothing happens.

any help would be much appreciated, thanks.

i am dual booting windows xp sp3 with ubuntu 8.0.4 without any problems.

output of

```
sudo fdisk -l
```

is

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd201d201

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2434    19551073+   7  HPFS/NTFS
/dev/sda2            2435        4865    19527007+   f  W95 Ext'd (LBA)
/dev/sda5            2435        4593    17342136   83  Linux
/dev/sda6            4594        4865     2184808+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dbaaf39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2        6496    52171056    7  HPFS/NTFS
/dev/sdb6            6497       12871    51207156    7  HPFS/NTFS
/dev/sdb7           12872       19246    51207156    7  HPFS/NTFS
/dev/sdb8           19247       25621    51207156    7  HPFS/NTFS
/dev/sdb9           25622       31996    51207156    7  HPFS/NTFS
/dev/sdb10          31997       38371    51207156    7  HPFS/NTFS
/dev/sdb11          38372       44746    51207156    7  HPFS/NTFS
/dev/sdb12          44747       51121    51207156    7  HPFS/NTFS
/dev/sdb13          51122       56221    40965718+   7  HPFS/NTFS
/dev/sdb14          56222       60801    36788818+   7  HPFS/NTFS

```

ok i can now mount using terminal commands ntfs-3g.So solved now :)

---

### Post by cariboo on 2009-03-09
What happens when you manually mount your first Windows partition?

```
sudo mount /dev/sda1 /mnt
```

When double-clicking a drive in Natilus, does the partition get mounted in /media?

Jim

---

