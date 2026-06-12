---
title: "Unable to mount usb thumbdrive"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by rojodojo on 2009-01-05
Hello,
I've encountered a problem where whenever I plug in my usb thumbdrive, I'm unable to access it. I've tried formatting the usb stick, but I keep getting the same message:

Unable to mount "1G Removable Volume":

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

sudo fdisk -l gives me this

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16091608

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       18357   147444570    f  W95 Ext'd (LBA)
/dev/sda2   *       18358       19457     8835750    7  HPFS/NTFS
/dev/sda5               2        2551    20482843+   7  HPFS/NTFS
/dev/sda6            2552       16460   111724011    7  HPFS/NTFS
/dev/sda7           18236       18357      979933+  82  Linux swap / Solaris
/dev/sda8           16461       18162    13671283+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000 MB, 1000341504 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d413f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      976864+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 157, 36)

---

If anyone could help me out, that would be great,
thx in advance

Rojodojo

---

### Post by cardinals_fan on 2009-01-05
Well, Google delivered this: [http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo#Partition_has_different_physical.2Flogical_endings.21](http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo#Partition_has_different_physical.2Flogical_endings.21)
> Partition has different physical/logical endings!

If you get the following message, you may need to reformat the flash drive.

```
# fdisk -l /dev/sdb

Disk /dev/sdb: 2029 MB, 2029518848 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         961     1981936    6  FAT16
Partition 1 has different physical/logical endings:
phys=(967, 128, 32) logical=(960, 31, 32)
```
Try reformatting again.

---

