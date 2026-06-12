---
title: "Ubuntu file system"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by edm2468 on 2009-06-27
I need a good beginner URL explaining the Ubuntu file system and common commands to probe it 
 
 
TIA,
 
edm2468
 
In MS Wiindows (my background) they refer to drives C:, D:, E:, etc. Ubuntu (and Linux in general) appear to use "\dev\hda" and \"dev\hdb" instead, but I'm not sure. Hence the request in this thread.

---

### Post by QIII on 2009-06-27
> **edm2468 said:**
> 
In MS Wiindows (my background) they refer to drives C:, D:, E:, etc. Ubuntu (and Linux in general) appear to use "\dev\hda" and \"dev\hdb" instead, but I'm not sure. Hence the request in this thread.

Be sure.  That is the way it is.

But I'm not sure what you mean by "probe it".

This is probably the sort of thing to get you started:

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by durand on 2009-06-27
/dev/hda is a block device, ie, it represents the actual drive. (It should technically be sda, rather than hda on newer linux distros) The partitions would be represented by /dev/sda1, etc. In linux, a partition isn't "mounted" unless it is asked to be, either by a script or by you double clicking on the partition in Computer. The closest to C:, D: etc would probably be the folders in /media. That is where the partitions are mounted to. It's hard to find analogies with windows really because it works very differently. In linux, you can mount a partition to any folder so instead of using a folder in /media, you could use /home/user/Partition, or whatever. I guess C: is the same as / and every other partition and folder is inside this, either physically or virtually in the case of mounts.

---

### Post by SunnyRabbiera on 2009-06-27
Its actually very simple:

HDA = Usually the primary hard disk/ partition
HDB, C, etc = usually secondary drives, DVD drive, CD drive, Externals, etc.
Then you get numerical with the drive identifications, HDA1 usually means primary partition, while others indicate home and swap.
This all depends on how you set it up though.
Also there is SDA, B C etc to consider but mostly its the same basic thing.

As for directories again very simple:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

/usr/bin and /usr/lib is almost like program files in windows, home is like documents and settings.

---

### Post by QIII on 2009-06-27
hda1, as posted above, represents a partition on a particular drive.

Numerical references for the drives themselves are zero-based.

hd0, hd1 ... (or sdX for newer drives (SATA/SCSI))

And there is a "My Computer" equivalent for navigating through your files.

The "Vista" icon represents the other physical drive I have in dual boot configuration.  I double click it in Nautilus to mount it and navigate around it, too.

---

