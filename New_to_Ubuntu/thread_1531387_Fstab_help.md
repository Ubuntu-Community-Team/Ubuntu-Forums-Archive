---
title: "Fstab help"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by mrphud on 2010-07-14
Hey all,

I need help with my fstab file. I am trying to mount a second hard drive on startup but it is formatted as NTFS and keeps giving me an error. This is what I added to the fstab that gave me an error.

```
/dev/sdb1       /media/My_Computer      auto    rw,user,auto,noexec       0       0

```

So here is the info:

```
sudo fdisk -l
```

to get

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008377f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29178   234371072   83  Linux
/dev/sda2           29179       30402     9825281    5  Extended
/dev/sda5           29179       30402     9825280   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe4b12756

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f435f47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

The drive I want to mount is sdb1.
Thanks for the help.

By the way. How do I mark a post as solved?

Thanks

---

### Post by cariboo on 2010-07-15
It probably would be better to specify the partition type, instead of using auto eg: ntfs

```
/dev/sdb1       /media/My_Computer      ntfs    rw,user,auto,noexec       0       0
```

---

### Post by mrphud on 2010-07-15
That did it. Thank you for the help.

---

