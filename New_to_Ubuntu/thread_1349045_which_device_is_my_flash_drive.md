---
title: "which device is my flash drive?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by AlphaWhelp on 2009-12-07
I'm looking for where in the /dev/ directory I can find the file for my flash drive.  dmesg isn't really helpful, I was told for something that looks like sdb: sdb1 however I can find this piece of text even when I pull all the usb devices out of the computer.  If I know the volume label of my flash drive, is there any way I can ask dmesg to filter just the device with a specific label?

---

### Post by jbrown96 on 2009-12-07
The utility fdisk can help you. ```
sudo fdisk -l
``` will list all your devices and the paritions on them. I don't haven anything but my internal hard drive connected; it reports > 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e5f1410

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         851     6835626   83  Linux
/dev/sda2             852       19457   149452695    5  Extended
/dev/sda5            1703       19457   142617006   83  Linux
/dev/sda6             852        1702     6835594+  83  Linux

Partition table entries are not in disk order


The first line will help you the most. It lists the size of the device. Usually flash drives only have one partition.

---

### Post by bodhi.zazen on 2009-12-07
> **AlphaWhelp said:**
> I'm looking for where in the /dev/ directory I can find the file for my flash drive.  dmesg isn't really helpful, I was told for something that looks like sdb: sdb1 however I can find this piece of text even when I pull all the usb devices out of the computer.  If I know the volume label of my flash drive, is there any way I can ask dmesg to filter just the device with a specific label?

This may help you as well :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by MadHatter21 on 2009-12-07
Your flash drive might be mounted in media. /media I know that mine are.

Madhatter21

---

### Post by Miljet on 2009-12-07
Insert the flash drive. When it shows up on your Desktop, right click on it and select properties.Then click on the Volume tab and it will show you the mount point.

I hope that is what you were asking.

---

