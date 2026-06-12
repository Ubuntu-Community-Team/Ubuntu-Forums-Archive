---
title: "Can't detect Linux native volume"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by ralphs1 on 2009-08-30
I have a Ubuntu 9.04 boot CD.
If I plug the hard drive from my Bauhn PVR into an external USB drive Ubuntu cannot detect it.
Ubuntu detects other, non Linux, USB portable drives successfully.

I can see the drive in Windows using DiskInternals Linux Reader 1.1, which reports it as being a Linux native volume. Properties are:
File System: Linux native
Active Partition: Not Active
Image File: --none--
Start Sector: 63
Total Sectors 488392002
Type: MBR Partition

I can save files from it using the Linux Reader, but it is very slow.
Any ideas what I should be looking for?
Thanks.

---

### Post by nhasian on 2009-08-30
while the drive is plugged in, what is the output for:

```
sudo fdisk -l
```

---

### Post by ralphs1 on 2009-08-31
There are some other HPFS/NTFS disks before these three disks.
The first one here is an internal hard disk and the third one is a USB portable hard drive.

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf60af60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2d943a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   83  Linux

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
81 heads, 63 sectors/track, 45941 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0x90f43881

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       45942   117220792+   c  W95 FAT32 (LBA)

---

