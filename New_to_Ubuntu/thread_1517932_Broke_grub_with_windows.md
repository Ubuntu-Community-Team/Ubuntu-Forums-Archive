---
title: "Broke grub with windows"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by darkeye123 on 2010-06-25
hey guys,

In one of my finest moments, I decided to try and install windows to a flash drive, however, about halfway through, the install failed and I was forced to reboot. However, it overwrote grub because it wanted to access the flash drive on reboot. Now i'm stuck because it wont allow me to boot off the hard drive, since the MBR was overwritten.

Right now I'm posting from the ubuntu live cd, 10.04. I'll post my fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1046     8399128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1046       12637    93107542+   7  HPFS/NTFS
/dev/sda3           12638       24322    93853697    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           12638       23841    89991168   83  Linux
/dev/sda6           23842       24320     3847536    b  W95 FAT32
ubuntu@ubuntu:~$ 

```Is there some way to restore grub based on this config?

sda1 is the recovery partition, sda2 is the main windows partition, and sda3/4/5 are for ubuntu I believe.

Thanks :D

---

### Post by oldfred on 2010-06-25
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It looks like your install is in sda5 and you will want to install to sda, so no changes required.
Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

