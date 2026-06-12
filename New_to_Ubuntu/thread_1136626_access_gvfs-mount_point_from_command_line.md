---
title: "access gvfs-mount point from command line?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by creperum on 2009-04-25
I have a device (a digital camera) that is mounted with gvfs-mount; typing "gvfs-mount -l" (as suggested [here]("https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/258083/comments/15")) gives
```
Volume(0): Kodak Co. Digital Camera
Mount(0): Kodak Co. Digital Camera -> gphoto2://[usb:008,004]/

``` which looks to me like the camera is mounted at gphoto2://[usb:008,004].  I can open this location in Nautilus just fine, and see the files (photos) in the browser.

My really basic question is, Is it possible to access this from the command line?  Can I copy files from it, list files in it, etc?  If so, <i>where?</i>  I tried "ls gphoto2://[usb:008,004]," but it just said "no such file or directory."  Where does gvfs put its mount points?  Or is it even possible to perform regular file operations on them?

(I couldn't find any reasonable documentation for gvfs on-line or on my system; if anyone can point me towards a tutorial, or even something like a man page, that would be a great start....)

Thanks!

---

### Post by unutbu on 2009-04-25
Thank you for telling me about the "gvfs-mount -l" command! I didn't know about it. Due to the information you told me, I stumbled upon the fact that you can access the filesystem on your camera in the directory ~/.gvfs/. For example

```
cp ~/".gvfs/gphoto2 mount on usb%3A008,002/DCIM/100CANON/IMG_2539.JPG" ~/test
```

You will need to change the "gphoto2 mount on usb%3A008,002/DCIM/100CANON" path to suit your camera.

---

### Post by creperum on 2009-04-26
Hey, thanks, unutbu!  

Where did you find this information out?

---

### Post by unutbu on 2009-04-26
I had read that Samba filesystems are accessible through ~/.gvfs
The command you showed me was called gvfs-mount.
It made me wonder if stuff it listed might also be accessible at ~/.gvfs.

---

### Post by narnie on 2010-02-28
This is an older thread, but can one not just type mount at a command prompt?

I do this with the gvfs volumes from usb drives and can mount and unmount them using gvfs-mount.

If I do run mount from a terminal, then I get all the mounts on the system. This should point you to where it is at.

First place to check is /media/??? where ??? might be something similar to the name of your camera (but not necessarily).

Mount should always find it though, where it was mounted in kernelspace with root or userspace with something like gvfs-mount, pmount, gnome-mount, etc.

what I do to more easily find it is identify the block device name by running:
```
woodnt@toshiba-laptop ~ $ sudo fdisk -l
[sudo] password for woodnt: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc4608ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12641   100000000    7  HPFS/NTFS
/dev/sda3           59465       60802    10739712   17  Hidden HPFS/NTFS
/dev/sda4           12641       59464   376105748    5  Extended
/dev/sda5           12642       19168    52428127+  83  Linux
/dev/sda6           19169       58942   319484623+  83  Linux
/dev/sda7           58943       59464     4192933+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     4095551   17  Hidden HPFS/NTFS
/dev/sdb2             511       60715   483596662+   5  Extended
/dev/sdb5             511        1815    10482381   83  Linux
/dev/sdb6            1816        3120    10482381   83  Linux
/dev/sdb7            3121        3185      522081   83  Linux
/dev/sdb8            3186        3217      257008+  83  Linux
/dev/sdb9            3218       60715   461852653+  83  Linux
```

BTW, if you already know the block dev name (in this example, it is /dev/sdb which is the first usb drive usually), then you can shorten the output with this:


```
woodnt@toshiba-laptop ~ $ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     4095551   17  Hidden HPFS/NTFS
/dev/sdb2             511       60715   483596662+   5  Extended
/dev/sdb5             511        1815    10482381   83  Linux
/dev/sdb6            1816        3120    10482381   83  Linux
/dev/sdb7            3121        3185      522081   83  Linux
/dev/sdb8            3186        3217      257008+  83  Linux
/dev/sdb9            3218       60715   461852653+  83  Linux

```

From the above, identify the partition (by size, is how I usually find it)

Then run a:

```
woodnt@toshiba-laptop ~ $ mount|grep /dev/sdb9
/dev/sdb9 on /media/DATA type xfs (rw,nosuid,nodev,uhelper=devkit)

```

Where it tells me that this xfs partition is mounted on /media/DATA (where data is the Volume Label of the partition, which will likely be the volume label of a USB camera that itself acts like a flash usb drive and behaves similarly, except it will be a vfat partition, likely)

Hope this helps someone,
Narnie

---

