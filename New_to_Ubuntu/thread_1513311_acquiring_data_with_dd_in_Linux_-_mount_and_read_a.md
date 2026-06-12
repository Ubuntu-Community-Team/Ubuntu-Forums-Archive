---
title: "acquiring data with dd in Linux - mount and read a drive"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Gina IN on 2010-06-19
Good morning.  I'm trying to complete classwork.  My assignment is to acquire data with dd in linux.  I'm trying to create a mount point for the USB drive.  The instructions are:

To create a mount point for the USB, make a directory in /mnt by typing mkdir /mnt/sda5.  I don't have a sda5 listed when I used fdisk -l.

To mount the target drive partition, type mount -f v/fat /dev/sda5 /mnt/sda

I only have sda1 and sda2.  Here's what I got when I used fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8d64c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18238   146492384+   7  HPFS/NTFS
/dev/sda2           18238       19457     9794560    7  HPFS/NTFS

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders
Units = cylinders of 529 * 512 = 270848 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       14805     3911744    c  W95 FAT32 (LBA)

Can anyone help me?  I'm new to Ubuntu and linux.  Thank you.

---

### Post by cariboo on 2010-06-19
You can find the device label by plugging in the device, then opening a terminal and typing:

```
dmesg | tail -n5
```

the above command prints out the last 5 lines of dmesg. The result should look something like this:

```
dmesg | tail -n5
[ 8065.554205] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8065.556014] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8065.556023]  sdc: **sdc1**
[ 8065.558993] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 8065.558999] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

As you can see from the above output that my device is /dev/sdc1, depending on how many hard drives you have yours may be different.

Just as an aside, the forum Code of Conduct states that we are happy to help you with your homework, but don't expect us to do it for you.

---

