---
title: "mounting devices"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-07-12
Hi,

I am an absolute beginner, so I apologize if this question is really stupid. I could not find an answer to my question in most of the documentations that i read.

Suppose I attach a pen drive or some kind of external device to the computer and it does not mount automatically, then is there some way I can tell the OS that I have attached a device at X location and ask it to mount it to Y mount point?

Thanks

---

### Post by egalvan on 2010-07-12
First off, there are no "really stupid questions" here in the Absolute Beginner's".

Next...

Are you talking about the pen-drive not being mounted? 
Or not being detected?

When I use certain pen-drives, they are detected, but not mounted.
Going to "Places" will show them.
Clicking on the drive has always resulted in them being auto-mounted.

If they are not being detected at all, that is another matter.

---

### Post by JustinR on 2010-07-12
Hi LittleGyko!

Most USB flash drives are recognized automatically and mounted. But if not - go to System > Administration > Disk Utility. It should show up there and click mount drive.

If that doesn't help don't hesitate to post back!

---

### Post by LittleGyko on 2010-07-12
thanks to both of you. in my case, it was my camera card which was not being detected. but then after some time it got detected by itself. 

justin, as you suggested it was there in disk utility.

in the mean time, i was trying to do some reading about mounting and found a nice article, which said the following:

1. use lsusb to find out whether your computer has detected the device
2. use dmesg to find where ...i dont know the correct terms to use here....the device is ex /dev/sdb
3. use mount to mount the file system

however, when i use mount , i get an error saying i need to specify the file system type.how can i detect the file system type, when the device is not yet mounted?

gyko

---

### Post by JustinR on 2010-07-12
Usually camera card filesystems are FAT32. Use "sudo mount -t fat32" and see if that helps. If it doesn't it could mean your memory card is corrupt, in that case I would use photorec to recover pictures off the card.

---

### Post by LittleGyko on 2010-07-12
it gives an error "unknown filesystem fat32 maybe you mean vfat"

---

### Post by LittleGyko on 2010-07-12
dmesg | tail
[14538.084491] sd 16:0:0:0: [sdb] 3994624 512-byte logical blocks: (2.04 GB/1.90 GiB)
[14538.085238] sd 16:0:0:0: [sdb] Write Protect is on
[14538.085241] sd 16:0:0:0: [sdb] Mode Sense: 03 00 80 00
[14538.085244] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[14538.087625] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[14538.087631]  sdb: sdb1
[14538.090748] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[14538.090753] sd 16:0:0:0: [sdb] Attached SCSI removable disk
[14672.403951] FAT: invalid media value (0x01)
[14672.403955] VFS: Can't find a valid FAT filesystem on dev sdb.

It says its neither fat32 nor vfat!! what to do in such cases?

---

### Post by nothingspecial on 2010-07-12
You need to create or use an existing mount point eg

```
sudo mkdir /media/camera
```

Then you need to find out which your card is and what file system it is

```
sudo fdisk -l
```

You should be able to tell from the size of it.

Then

```
sudo mount -t vfat /dev/sd?? /media/camera
```

Change /dev/sd?? to the information you found out using the fdisk command and vfat for the appropriate file system.

---

### Post by TechBeastie on 2010-07-12
For future reference, parted and/or gparted should also be able to identify the filesystem type of unmounted volumes.  Gparted (the graphical version of parted) may or may not be installed on your system, but parted almost certainly should be.  (Be careful when using these utilities though, since they're both full-blown partition managers, and hence can be used to completely destroy the logical structure of one's disks).  

Also note that the syntax of the mount command is rather nasty, and (in my experience) requires that the filesystem type be specified before anything else.  Thus, a typical mount call for a flash drive might look something like this:
mount -t <type> /dev/sdb1  /media/<create an empty folder here to use as a mountpoint>

---

### Post by LittleGyko on 2010-07-12
this is really surprising. fdisk did not seem to work earlier. thanks a lot. this seems to sort out all my problems.

---

### Post by LittleGyko on 2010-07-12
I tried using parted but giving "print" only prints the mounted partitions. could you please tell me how to use it to detect unmounted devices? thanks

---

