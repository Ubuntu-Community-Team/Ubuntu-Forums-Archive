---
title: "Partition questions"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by jfbooth on 2011-08-16
WUBI install of Ubuntu 11.04.  Using CLASSIC desktop.  Wubi inside XP SP3.

Installed Ubuntu (WUBI) with 1GB of memory on the machine.  Have since doubled that to 2GB.  Am wondering if I am running the correct swap partition.  Here is some partition info:

```
owner@ubuntu:~$ sudo fdisk -l
[sudo] password for owner: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x454c32ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+  de  Dell Utility
/dev/sdb2   *           5        7295    58564957+   7  HPFS/NTFS
owner@ubuntu:~$
```

This is a Dell notebook with a 60GB hard drive.  I believe there is a Dell Diagnostic partition.

I am a Linux beginner.  I am not experienced in dealing with partitions.

1st question:  Do I need to do anything to any partition?

2nd question:  If 1st = yes, what and how?

Thank you in advance.

Edit:  There is a 500GB usb external drive connected to the notebook.

---

### Post by mikewhatever on 2011-08-16
Since you have a wubi install there is no swap partition, which means that the question is void and there is nothing to worry about.
:P

---

### Post by elgordodude on 2011-08-16
No your disks look okay from what I can see here. You may be wondering why there's no "linux" partition, it's because you installed with wubi and thus didn't create a new partition. Also, when dual-booting I prefer FAT32 over ntfs on external drives as its the most flexible filesystem, but this isn't something you need to do, and if it works, and you're not sure what you're doing, don't fix it.

---

### Post by jfbooth on 2011-08-16
> **mikewhatever said:**
> Since you have a wubi install there is no swap partition, which means that the question is void and there is nothing to worry about.
:P

Thank you both for the quick and courteous reply.

I will leave it alone, and mark this thread solved.  Thank you both again.

---

