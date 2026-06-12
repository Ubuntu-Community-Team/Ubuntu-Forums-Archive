---
title: "4kb sectors -&gt; format to 512?"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by RHTizzy on 2010-12-01
I have a 2TB WD20EURS which formats to 4096B sector size using gparted, but I want to use the disk in a PVR running linux 2.6.12 which can't handle 4kB sectors. Is it possible to format the drive to 512B sectors?

---

### Post by cariboo on 2010-12-01
That's an awful old kernel, If it's possible to update the kernel just for security reason I would.

You can partition the hard drive the way you want, from the command line:

```
sudo fdisk -u /dev/sdX
```

where /dev/sdX is the hard drive, start the partion at sector # 64 and then set it to the size you want. I did it this way on my WD 1Tb hard drive:

```
Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18ca643d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121602   976762552   83  Linux
```

---

