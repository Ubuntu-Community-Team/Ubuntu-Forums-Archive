---
title: "Renaming second HD, and nautilus showing things that aren't there"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by dannytatom on 2008-12-24
I'm not sure if this is the right section to post this, so feel free to move it.

**Question 1)**  The things I highlighted red (in the attached image) aren't there, but are being shown.  I don't even know what they are, but I know that clicking them does nothing and looking inside my computer all I see are the things not highlighted.  How can I find out what they are and/or get rid of 'em?

**Question 2)**  My 2nd HD, "80.0 GB Media," is mounted in /media/media.  How can I rename the Icon/Places menu/whatever else so that instead of it being referred to as "80.0 GB Media" it'll just be "Media"

Thanks. :O

---

### Post by Xiong Chiamiov on 2008-12-24
Those are both side-effects of using HAL and Nautilus to manage your devices.  I don't think that you can change that, although someone more familiar with the interface may be able to tell you how to.

---

### Post by dannytatom on 2008-12-24
Hm, well I don't want to get rid of nautilus. :(

Are there any alternatives to HAL?

---

### Post by newbee70 on 2008-12-24
> **dannytatom said:**
> I'm not sure if this is the right section to post this, so feel free to move it.

**Question 1)**  The things I highlighted red (in the attached image) aren't there, but are being shown.  I don't even know what they are, but I know that clicking them does nothing and looking inside my computer all I see are the things not highlighted.  How can I find out what they are and/or get rid of 'em?

**Question 2)**  My 2nd HD, "80.0 GB Media," is mounted in /media/media.  How can I rename the Icon/Places menu/whatever else so that instead of it being referred to as "80.0 GB Media" it'll just be "Media"

Thanks. :O

** I don't know who wrote this but it worked for me **



Rename USB Drive

This guide is for editing FAT16/FAT32, NTFS, ext2/ext3, JFS, ReiserFS, and XFS filesystem partition labels. 

There are 6 programs used to label a partition - the program used depends on the partition's filesystem type:

    *      For FAT16 and FAT32 partitions, use mtools.
    *      For NTFS partitions, use ntfsprogs.
    *      For ext2 or ext3 partitions, use e2label.
    *      For JFS partitions, use jfs_tune.
    *      For ReiserFS (v3) partitions, use reiserfstune.
    *      For XFS partitions, use xfs_admin 

Labeled devices that automount will be mounted in the /media directory using their label as the mount point, /media/<label>. ex: /media/my_external .
IconsPage/warning.png When creating labels, be sure that the new mount point (based on the label) does not already exist since hal's automount function creates the directory when it mounts the device.

This guide is primarily for external drives such as USB hard drives, USB flash drives, and flash memory cards. You can label internal disks, but to change their mount points, use MoveMountpointHowto which uses the file called Fstab. 
By default, external drives automount at /media/disk then /media/disk-1 and so on. This is not very helpful when trying to find the drive you are looking for, especially if you have multiple devices plugged in. 

GNOMETerminal.png For help with the terminal, see UsingTheTerminal.

Plug in your USB device and list your partitions with:

sudo fdisk -l

You can also list your mounted devices and their descriptions with:

mount

For the rest of this tutorial we will use the following:

    *      <device> = your device /dev/sdxy, ex: /dev/sdb1
    *      <label> = your desired (new) label, ex: my_external 




Based on Install the Labeling Program

the package names listed above for each filesystem type, install the correct package for your partition:

sudo apt-get install <package>

Here are all the different ones:

    *

       sudo apt-get install mtools
       sudo apt-get install ntfsprogs
       sudo apt-get install e2fsprogs
       sudo apt-get install jfsutils
       sudo apt-get install reiserfsprogs
       sudo apt-get install xfsprogs

or install the appropriate package from Synaptic. 



Changing the Label

FAT16 and FAT32

These filesystems are most often found on USB thumb drives, flash cards (like for a camera or cell phone), and older external USB hard drives.
Check the current label

sudo mlabel -i <device> -s ::

ex:    *    sudo mlabel -i /dev/sdb1 -s ::

Note that we're using the special "::" drive which allows us to specify the device descriptor on the command line; otherwise we'd have to edit ~/.mtoolsrc to assign a drive letter.

If you get a message like this:

Total number of sectors (7831520) not a multiple of sectors per track (63)!

You can easily ignore the check by running this command:

echo mtools_skip_check=1 >> ~/.mtoolsrc

Change the label

sudo mlabel -i <device> ::<label>

ex:

    *

       sudo mlabel -i /dev/sdb1 ::my_external

NTFS

This filesystem is most often found on external USB and firewire hard drives or other Windows formatted disks.
Check the current label

sudo ntfslabel <device>

ex:    *       sudo ntfslabel /dev/sdb1

Change the label

Note: 128 characters maximum.

sudo ntfslabel <device> <label>

ex:    *       sudo ntfslabel /dev/sdb1 my_external

Ubuntu caches the drive's label so to see full affects of the change it is not enough just to umount and mount it again, the you should umount, remove, put back, mount again.

ext2 and ext3

These filesystems are most often found on linux formatted drives.
Check the current label

sudo e2label <device>

ex:    *       sudo e2label /dev/sdb1

Change the label

Note: 16 characters maximum.

sudo e2label <device> <label>

ex:    *       sudo e2label /dev/sdb1 my_external

JFS

These filesystems are most often found on IBM and some linux formatted disks.
Check the current label

sudo jfs_tune -l <device>

ex:    *       sudo jfs_tune /dev/sdb1

Change the label

Note: 16 characters maximum.

sudo jfs_tune -L <label> <device>

ex:    *       sudo jfs_tune -L my_external /dev/sdb1

ReiserFS (v3)

This filesystem is most often found on linux formatted disks.

Note: this could work with ReiserFS 4 too, I have not tried.
Change the label

Note: 16 characters maximum.

sudo reiserfstune -l <label> <device>

ex:    *       sudo reiserfstune -l my_external /dev/sdb1

XFS

This filesystem is most often found on UNIX formatted disks.
Check the current label

xfs_admin -l <device>

ex:    *       xfs_admin -l /dev/sdb1

Change the label

Note: 12 characters maximum.

sudo xfs_admin -L <label> <device>

ex:    *       xfs_admin -l my_external /dev/sdb1

Verify the Change

Now for the easiest part: unplug the drive, wait a second, then plug it back in. It should appear on your desktop with the new label and have its new mount point.

---

### Post by mapes12 on 2008-12-24
Q1: Have you got a card reader attached somewhere on your system?

Q2: Create a separate directory on your system similar to this ```
sudo mkdir /home/danny/Desktop/HDD2
```I call my second drive HDD2. Call it whatever you like and set the path to where ever you want it.
Then mount it ```
sudo mount /dev/sdb1 /home/danny/Desktop/HDD2
```to access it. Mine is sdb1. To find out what yours is called ```
sudo fdisk -l
``` If you want to have the drive permanently mounted all the time from boot up you will need to add a line to your /etc/fstab file.

---

### Post by dannytatom on 2008-12-24
> **mapes12 said:**
> Q1: Have you got a card reader attached somewhere on your system?

Not that I'm aware of, no  I bought it from a friend and he doesnt seem to think so, either.  





> **mapes12 said:**
> 
Q2: Create a separate directory on your system similar to this ```
sudo mkdir /home/danny/Desktop/HDD2
```I call my second drive HDD2. Call it whatever you like and set the path to where ever you want it.
Then mount it ```
sudo mount /dev/sdb1 /home/danny/Desktop/HDD2
```to access it. Mine is sdb1. To find out what yours is called ```
sudo fdisk -l
``` If you want to have the drive permanently mounted all the time from boot up you will need to add a line to your /etc/fstab file.

Alright, so I got it mounted.  Is there a way to remove the "80.0 GB Media" shortcut from my desktop and places menu (in nautilus)?

**Edit:** Also, the Places menu from the panel lists it as "80.0 GB Media" instead of "Media," though in nautilus it lists both(I added "Media" as a bookmark, "80.0 GB Media" is there by default)

---

### Post by dannytatom on 2008-12-26
Hmmm, bump. ;o

---

### Post by dannytatom on 2008-12-27
Anybody? D:

---

### Post by mapes12 on 2008-12-28
Post the output to ```
cat /etc/fstab
```

---

### Post by dannytatom on 2008-12-28
```

danny@anon:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc              proc         defaults                    0  0  
# /dev/sda1
UUID=5fa345f2-0434-4672-8091-4ea79c4f0701  /                  ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=1485ed84-9d57-4034-9e15-6ae5dc55a939  none               swap         sw                          0  0  
/dev/scd1                                  /media/cdrom2      udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /home/danny/Media  ext2         errors=remount-ro,user      0  0  

```

---

### Post by dannytatom on 2009-01-04
Eh, bump?

My 2nd HD died, so I no longer need help with that.  Still have a ton of unknown stuff listed in my places menu, though.

---

