---
title: "Dual boot install -- miniscule partition"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Efros on 2009-04-27
Ok, I tried to install a dual boot system today with my pre-existing XP SP3 machine. Installation from the Desktop 9.04 AMD64 disk went smoothly and quickly, unfortunately the installation was on a 2Gb partition with a 170MB swap, tagged onto the end of the XP boot disk. This last bit I expected, I did however expect the installer to make a bigger partition for Ubuntu. 

Anyway I thought no problem, boot the install disk, fire up partition manager resize the XP partition, move the Linux partition, resize it and move and resize the swap partition. Did this and it booted fine, however linux only sees the original partition size and not the new one, what gives?

---

### Post by NESFreak on 2009-04-27
> **Efros said:**
> Ok, I tried to install a dual boot system today with my pre-existing XP SP3 machine. Installation from the Desktop 9.04 AMD64 disk went smoothly and quickly, unfortunately the installation was on a 2Gb partition with a 170MB swap, tagged onto the end of the XP boot disk. This last bit I expected, I did however expect the installer to make a bigger partition for Ubuntu. 

Anyway I thought no problem, boot the install disk, fire up partition manager resize the XP partition, move the Linux partition, resize it and move and resize the swap partition. Did this and it booted fine, however linux only sees the original partition size and not the new one, what gives?

could you post the results of
```
sudo fdisk -l
```

---

### Post by Efros on 2009-04-27
will do tomorrow when I get at the machine again!

---

### Post by Efros on 2009-04-28
```
Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80ac1a3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6373    51191091    7  HPFS/NTFS
/dev/sda2            6374       12188    46708987+   f  W95 Ext'd (LBA)
/dev/sda5            6374       11992    45134586   83  Linux
/dev/sda6           11993       12188     1574338+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5e92315

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        6567       15017    67882657+   7  HPFS/NTFS
/dev/sdc2               2        6566    52733362+   f  W95 Ext'd (LBA)
/dev/sdc5               2         305     2441848+  83  Linux

Partition table entries are not in disk order

```

sudo fdisk -l output

---

### Post by Efros on 2009-04-28
Forget it I realized that Ubuntu had placed the boot partition in /dev/sdc5, not /dev/sda5 which is the partition I extended. Weird.

---

