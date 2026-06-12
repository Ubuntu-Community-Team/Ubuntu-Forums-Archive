---
title: "Storing files on bootable USB"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by macabrem on 2009-10-13
If I have a bootable USB flash drive with Ubuntu Netbook Remix on it, can I store other files on the drive (4GB drive, the remix only takes about 1GB)? 


Or, will the drive not boot up if I try to boot live or restore my system?

---

### Post by mac9416 on 2009-10-13
If you use the [USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") tool, you can store other files with the live USB install.

---

### Post by pastalavista on 2009-10-13
You might also partition the flash drive with gparted into two partitions with 1GB for the OS and 3 gigs for storage... since the USB creator won't work with .img files.

---

### Post by lavinog on 2009-10-13
> **macabrem said:**
> If I have a bootable USB flash drive with Ubuntu Netbook Remix on it, can I store other files on the drive (4GB drive, the remix only takes about 1GB)? 


Or, will the drive not boot up if I try to boot live or restore my system?

You should be able to store files on the drive as long as you are not overwriting the existing files.

---

### Post by tea for one on 2009-10-13
> **macabrem said:**
> If I have a bootable USB flash drive with Ubuntu Netbook Remix on it, can I store other files on the drive (4GB drive, the remix only takes about 1GB)? 


Or, will the drive not boot up if I try to boot live or restore my system?

If you used the Ubuntu USB creator software to make a bootable USB device, then you will be able to use any free space as a storage device (via both Windows and Linux)

With reference to your second question:-
"Or, will the drive not boot up if I try to boot live or restore my system?", I am not sure what you want to do? Please elaborate.

For example:-

You will still be able to use the USB device equivalent to a "live" CD even if you have used some free space to store other data.

You will also be able to install from a "live" USB device to a traditional HD installation and any other files saved on the USB device will remain on the device for future access.

---

### Post by bodhi.zazen on 2009-10-13
> **pastalavista said:**
> You might also partition the flash drive with gparted into two partitions with 1GB for the OS and 3 gigs for storage... since the USB creator won't work with .img files.

+1

This allows one to keep the OS in a 1 Gb partition and keep the data separate.

> **lavinog said:**
> You should be able to store files on the drive as long as you are not overwriting the existing files.

This will work, but if you ever need to re-install an OS it is messy. Sometimes it is easier to reformat the 1 Gb partition and start fresh.

---

### Post by mac9416 on 2009-10-13
> [QUOTE]You should be able to store files on the drive as long as you are not overwriting the existing files.

This will work, but if you ever need to re-install an OS it is messy. Sometimes it is easier to reformat the 1 Gb partition and start fresh.[/QUOTE]

Then again, you could just put your data into its own folder, then you would always know which files are for the live system and could remove them before installing a new OS.

---

