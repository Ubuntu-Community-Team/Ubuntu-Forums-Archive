---
title: "windows vista does not recognise my ubuntu usb hard drive"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by tim183 on 2009-03-09
I backed up all my photos, music and documents onto an external usb hard drive in Ubuntu 8.10.

I then installed Vista onto the same machine. When I plug the USB hard drive into the computer the notification bubble in vista says found new hardware etc, however when I open My Computer only the internal drive and CD Drive are listed...

Is it an issue with the different file systems the OS's use?

---

### Post by tad1073 on 2009-03-09
Windows can not read ext3 file format

---

### Post by tim183 on 2009-03-09
right....

so what are my options?

Could I plug the USB into another Ubuntu machine and allow sharing on the drive, then access it over the wireless network and copy onto the Windows machine?

---

### Post by halitech on 2009-03-09
did you format the drive in Ubuntu or did you just plug it in the first time and start copying files over to it? In Ubuntu, open a terminal (with the drive attached) and post the output of
```
sudo fdisk -l
``` (that's an l not the number 1)

What make is the usb drive?

---

### Post by tim183 on 2009-03-09
I formatted it in Ubuntu.

Its a Fujitsu 2.5" internal drive in an external case, connects via USB.

---

### Post by Ocxic on 2009-03-09
there is a ext2/3 driver for windows that you can download, I've used it before. that should let you get your data off the drive.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by halitech on 2009-03-09
> **Ocxic said:**
> there is a ext2/3 driver for windows that you can download, I've used it before. that should let you get your data off the drive.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

+1

I've used the driver before and it works fine. I would also recommend once you have the data off that you reformat in windows to NTFS or FAT32 as Linux can read that easier then windows can read ext3

---

### Post by egalvan on 2009-03-09
> **Ocxic said:**
> there is a ext2/3 driver for windows that you can download, I've used it before. that should let you get your data off the drive.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Sadly, the current version does not support large inodes,
which current kernels seem to prefer.

Perhaps if the developers received more support...

Quote from their FAQ...

[B]Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. [/B]


Here are two more ext2 driver for Windows.
I have not used them... anybody with any experience with them?

[http://sourceforge.net/forum/forum.php?forum_id=831109](http://sourceforge.net/forum/forum.php?forum_id=831109)

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

ErnestG

---

### Post by itisbasi on 2009-03-10
Why not use a Live CD to backup the data from the ext2/3 formatted drive?

---

### Post by tim183 on 2009-03-11
I tried the Live CD option last night, however the folders on the Ubuntu USB drive were randomly locked. When I checked permissions it said USER 1000 was the admin. Hence I couldnt copy them onto the Vista internal drive.

any suggestions?

---

### Post by rasmus91 on 2009-03-11
> Windows can not read ext3 file format

Windows and anything that has anything to do with linux doesn't seem to play along nicely

---

### Post by kelvin spratt on 2009-03-11
you need parted magic live cd to move your files and reformat with no problems you won't get any permission problems.

---

### Post by The Cog on 2009-03-11
> **tim183 said:**
> I tried the Live CD option last night, however the folders on the Ubuntu USB drive were randomly locked. When I checked permissions it said USER 1000 was the admin. Hence I couldnt copy them onto the Vista internal drive.

any suggestions?

Use the command **gksu nautilus** to launch nautilus (the file explorer) with full root priviledges. Then you should be able to copy them.

---

