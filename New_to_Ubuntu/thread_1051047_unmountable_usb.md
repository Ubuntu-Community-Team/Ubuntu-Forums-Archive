---
title: "unmountable usb"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by ibbill on 2009-01-26
I have windows xp on one partition and ubuntu 8.10 on another partition.

Am trying to install ubuntu 8.10 on a usb stick says unmountable and I do not have permission.You are not privileged to mount this drive,

Using the System>Administration>create a USB start up disk. That all being said I want to give this to my daughter who can run it on her computer with out installing linux 8.10 on her computer.

Have gone back into windows and umounted the drive right to see if that would help no luck.

ibbill@ibbill-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4073 32716341 7 HPFS/NTFS
/dev/sda2 4074 6623 20482875 5 Extended
/dev/sda3 6624 8918 18434587+ 7 HPFS/NTFS
/dev/sda4 8919 9725 6482227+ 82 Linux swap / Solaris
/dev/sda5 4074 6623 20482843+ 83 Linux

Disk /dev/sdb: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 * 51 99213 7932992 b W95 FAT32
ibbill@ibbill-desktop:~$

---

### Post by x33a on 2009-01-26
are you mounting it with sudo, and still getting this problem?

---

### Post by ibbill on 2009-01-26
Thanks for the quick reply no I am just double clicking the icon in my computer.

As I do to open xp partition or the file system

How would I use sudo to open it.

---

### Post by x33a on 2009-01-26
afaik, ubuntu automatically mounts a usb-drive when connected.

but, still assuming you have sdb1 as the pen drive (8 gb). 

try this command:

sudo mount /dev/sdb1 /media/pendrive

you can write anything in place of pendrive.

---

### Post by theozzlives on 2009-01-26
Try this to make an Ubuntu 8.10 USB drive, that your daughter can make changes to:

Boot your 8.10 Live CD and go to Applications > Accessories > Terminal. then type the following:
```
wget pendrivelinux.com/downloads/u810/u810.sh
```
Then:
```
chmod +x u810.sh && sh u810.sh
```
Follow the prompts. When you're done boot to USB.
She can also install from that at a later date if she wants.

---

### Post by ibbill on 2009-01-26
X33A thanks for the help. The oddest thing I put this usb pen in my other computer and it mounted just fine go figure.

Thanks for all your help.

---

### Post by ibbill on 2009-01-26
theozzlives   Thanks very much that worked whooooooooosh sure wish I knew what I did lol

Daughter will be very happy now. Think I will partition her laptop and install the new ubuntu in April.

Thanks again Bill

---

