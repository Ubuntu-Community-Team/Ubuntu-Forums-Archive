---
title: "Live USB access to NTFS disk"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by dpsguard on 2009-01-26
Hello Folks,

I really need help here. I have created a USB Live disk and it works on my Dell D630 laptop running vista (with two partitions, a 2GB FAT D:for recovery and remaining NTFS as C:) however hard drive does not get mounted. I can only see USB keys or DVD drive.

Here is fdisk -l output:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14594   117220824   d2  Unknown

Disk /dev/sdb: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 8192 * 512 = 4194304 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         248     1015280    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 255, 32) logical=(247, 223, 32)



sda1 is hard drive while sdb1 is the 1GB memory stick.

I tried to manually mount hard drive via following:

mkdir /mnt/disk
mount -t ntfs-3g /dev/sda1 /mnt/disk

but since fdisk does not list the filesystem as NTFS, so I get this error.


# mount -t ntfs-3g /dev/sda1 /mnt/disk
mount: mounting /dev/sda1 on /mnt/disk failed: Invalid argument
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

NTFS support is installed and I can not figure out the reason of my drive not being detected. 

Please help.

Thanks

---

### Post by dpsguard on 2009-01-27
Guys,

Can someone help me please?

Much appreciate

---

### Post by LowSky on 2009-01-27
you need a program called NTFS-3G to enable viewing the NTFS partition,
its in the repos. he program need to be run before you can mount

---

### Post by dpsguard on 2009-01-27
Thanks but NTFS-3g is already installed. It is standard on all new releases.

---

