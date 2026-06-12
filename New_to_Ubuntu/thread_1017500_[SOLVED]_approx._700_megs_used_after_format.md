---
title: "[SOLVED] approx. 700 megs used after format"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-21
I was told some stuff did not look rite (for my two storage drives) in my fstab. So I booted from a live CD and deleted the partition on each drive and created new ones for each drive. Then formatted them using ext3. Thing is, directly after format the partition manager said that there was about 700 megs used on both of these drives. what the heck is going on here?

---

### Post by Paqman on 2008-12-21
All filesystems have a certain amount of overhead. You'll never have o% used on any freshly formatted volume. How big are these drives?

---

### Post by pshootr on 2008-12-21
> **Paqman said:**
> All filesystems have a certain amount of overhead. You'll never have o% used on any freshly formatted volume. How big are these drives?

They are both 40 gig drives. I did fdisk -1 just now, and I get this.

[sudo] password for pshootr:

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4982    40017883+  83  Linux
pshootr@LinuxFS:~$


Notice it says sdb1 has invalid partition table. What the heck? Also sdc1 says Device boot. This only a storage drive. I used partition manager after booting from livecd, and all seemed to go ok. But now I get this s^&*.

---

