---
title: "Error formating usb hard disk"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by MindController on 2010-08-31
When I format my usb hard drive. I've seen following error
> 
Error creating file system: helper exited with exit code 1: helper failed with:
/dev/sdb is entire device, not just one partition.
Refusing to make a filesystem here!


when i typed fsck
> 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Thx.

---

### Post by BrandyBear on 2010-08-31
Do you have A partition or just pure ubuntu :-K

---

### Post by MindController on 2010-08-31
My laptop is running on window 7 and ubuntu. My ubuntu hard drive has partation. But my usb hard drive hasn't partation. Idk why did u ask for? :D

---

### Post by BrandyBear on 2010-08-31
Why do you need to format your USB hard drive is it because you want it for both ubuntu and Win7? and i asked that because if it was pure ubuntu it wouldent need Partitioning =D

---

### Post by -kg- on 2010-08-31
What method are you using to try to create a partition(s) on your USB drive?  I always prefer to use GParted to create them.

Am I understanding correctly that you have Win 7 and Ubuntu installed on your internal hard drive (sda)?  And that you want to partition your USB hard drive and place a file system on it?  If so...

First step would be to read the information at the "How To Partition" link in my signature block.  This will give you a good grounding in basic Partitioning operations using GParted.

Next, install GParted under Ubuntu (it's in the repositories).  Then launch it from "System/Administration/Gparted" and point it to your hard drive (sdb, right?).  It will tell you what partitions you already have on it (if any).  Take a screen shot of it and post it here, unless you already have the knowledge and can take it from there.

---

### Post by coffeecat on 2010-08-31
The error is because you are trying to create a filesystem in the whole drive, when you should be creating a partition together with a filesystem in the partition. If you describe what you did and how, we might be able to be more specific.

My guess is that you were using fdisk in the terminal to get that error. If so, what was the command you typed? Or, you may find using Gparted easier, as the previous poster recommended.

---

