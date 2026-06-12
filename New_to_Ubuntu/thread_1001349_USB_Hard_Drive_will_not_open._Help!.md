---
title: "USB Hard Drive will not open. Help!"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by suomalainen on 2008-12-03
Ubunteros,

I got a 40GB external hard drive that will not open.

Under Windows XP it opens just fine. In Ubuntu 8.04LTS. Not.

The Ubuntu desktop does not show a USB device connected but in Places-->Computer the device is seen. See pic I attached for reference.

This pic also shows error message I get when I double click on the USB drive.

I also ran command in TERMINAL:

sudo fdisk -l

MY RESULTS WERE:

Disk /dev/sdg: 40.0 GB, 40007761920 bytes
255 heads, 32 sectors/track, 9576 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   ?           1        9576    39070035    6  FAT16
Partition 1 does not end on cylinder boundary.

What I can do to get into my harddrive?

Thanks

---

### Post by ajmorris on 2008-12-04
hi there,
you can try ```
sudo mount /dev/sdg1 /mnt/disk -o force
``` (change /mnt/disk to where you want to mount it, but make sure the target folder exists first)

if that does not work, im afraid the partition on the hard disk is corrupt. First, before just formatting the hard disk, you might like to try [TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is a tool that can attempt to recover partitions/data.


AJ

---

### Post by gabril on 2008-12-04
id go with what ajmorris is saying... but im assuming here that the hd is formated in ntfs, thus in the need of a specification of filesystem when mounting... look it up! 

sudo mkdir /media/xhd
sudo mount -fs something /dev/<yourdrive> /media(i always put them here)/xhd

add -o loop if it wants you to!

---

### Post by ajmorris on 2008-12-04
> **gabril said:**
> id go with what ajmorris is saying... but im assuming here that the hd is formated in ntfs, thus in the need of a specification of filesystem when mounting... look it up! 

sudo mkdir /media/xhd
sudo mount -fs something /dev/<yourdrive> /media(i always put them here)/xhd

add -o loop if it wants you to!


the partition is fat16 (see the fdisk -l output earlier posted)  :)
and, you only need to specify the filesystem when mounting, if the mount cannot pick up the filesystem itself, and is specified by -t <type>  not -fs.  And it would not ask for -o loop, as that is for 'loop' devices, most commonly found as images, such as the iso image.


AJ

---

