---
title: "Renaming FAT32 Partition Through Ubuntu 8.04"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Vaedrah on 2009-01-16
I have an Acer Aspire 5920 notebook that I converted from Vista to Ubuntu 8.04 and left a partition at sda1 using about 10 GB of Fat32. I would like to share this partition with Sun xVM VirtualBox and this works OK, but I really wish I had chosen a different name to associate with the sda1 partition.

I have read most of the forum posts on file renames (often batch) but the syntax doesn't seem to apply. I have tried

sudo mv /media/oldname /media/newname

(I also tried rename .... but didn't have the proper syntax I guess).

when the sda1 drive is mounted and I get "drive is busy" as an error message. If I unmount sda1 the error message is "no drive found". I tried partition manager and this doesn't help either.

It is my own fault of course not to have chosen a more interesting name when I converted the machine but surely there is a way that works to convert a fat32 start partition from one descriptive name to another? The /media/oldname reference to sda1 comes up when I mount the fat32 drive but it refuses any attempt to be renamed (so far). It seems that I can't even make a link to the file (and give the link a better name!).

I am not familiar with syntax so if anyone has suggestions please don't assume I will be able to fill in any left out steps (I admittedly am only a dabbler!). Thanks in advance.

---

### Post by taurus on 2009-01-16
If you mount that fat32/vfat partition from /etc/fstab, then you can change the mount point in there also.

```
gksudo gedit /etc/fstab
```
Don't forget to create the new mount point if you decide to make a change in /etc/fstab.

---

### Post by unutbu on 2009-01-16
I believe the package you need is called "mtools", and the program to use is called "mlabel": See

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Edit: Or listen to taurus :)

---

### Post by Vaedrah on 2009-01-16
Thank you Taurus

The syntax you suggests returned

# /dev/sda1
UUID=C98F-1011  /windows        vfat    utf8,umask=007,gid=46 0       1

Perhaps I should clarify. Perhaps I should use the word "label" to refer to the partition. This is not a USB drive as unutbu's web link seems to reference; instead it is a partition on the notebooks main hard drive, e.g. sda1 = fat32, sda2 = ext3, sda3 = swap. I am quite happy with the partition name being sda1 but I want it's label "oldname" that shows up under /media/ or on the desktop to be something different from "oldname" - like "vesuvius" or "plato" etc. - in other words just a label that appears on the screen and can then be found on XP running in a VM (VirtualBox at the moment). My problem is in changing the label to a "newname", not that sda1 is any concern. 

I'll read the USB info further in case it case any clues.

---

### Post by GooblyWoobly on 2009-01-16
Let me clarify...
There are two cases:
1. You have an entry for the FAT filesystem in the /etc/fstab file. If that is the case, the label of the filesystem does not matter. It will be mounted where it was told to be mounted in the fstab table. Check the /etc/fstab to see if this is the case (i.e. you have an entry for the /dev/sda1 in /etc/fstab file).

2. You do not have an entry for the FAT filesystem in /etc/fstab. In this case, the filesystem is not automatically mounted, but only mounted when you click on it (or mount it manually). In this case, the filesystem is mounted at /media/<label> directory. You can first unmount it, then change the filesystem label using the mtools as mentioned in one previous post, and then remount it, and it should not show up under /media/<newlabel>.

FYI, mtools, and other filesystem tools don't care if it's a USB drive or a local hard drive. A filesystem is something that's inside a hard-drive, and is oblivious of the type of connectivity. For example, you can take the laptop's internal hard drive out, put it in a USB casing, and connect over USB, and the FAT drive will still show up at /media/<label>

Hope this clarifies it.

---

### Post by Vaedrah on 2009-01-16
Hi GooblyWoobly

I read the tutorial and used

echo mtools_skip_check=1 >> ~/.mtoolsrc

to remove the error message as they suggested

then

sudo mlabel -i /dev/sda1 ::Vaedra

as per their syntax

(Option 2. was current - the partition shows up in /media when clicked otherwise in /oldname)

I ran the commands in the terminal and the name is NOT CHANGED! I had hoped the example would have changed "oldlabel" ot "Vaedra" but nope!

No error messages appeared. Perhaps external USB drives are different from partitions?

Is there another approach I can try? Would reformatting the fat32 partition allow a new label?

---

### Post by GooblyWoobly on 2009-01-16
Well, I'm not too familiar with mtools. However, if you do not mind losing all the data on that partition, you can reformat it, and apply a lable. You can do that by:

ATTENTION!! If you do this command, you are going to lose all the data on /dev/sda1 partition.!!

```

sudo mkfs.vfat -n <newlable> /dev/sda1
```

Remember to unmount this before running it.

---

### Post by Vaedrah on 2009-01-16
[CENTER]**Problem Solved!**[/CENTER]

Thank you GooblyWoobly

I unmounted the partition and used

sudo mkfs.vfat -n Vaedra /dev/sda1

and it worked! The contents disappeared (no worries) but this time the label changed to "Vaedra"

So perhaps the only way to change a **_partition_** label is to reformat it :)

Thanks also to unutbu and taurus for your suggestions - I have learned a lot from the exercise!

---

### Post by GooblyWoobly on 2009-01-16
You are welcome. I have two things to ask from you in return :-).

1. Please mark the thread title with [SOLVED]. This helps other people in finding a solution.
2. Spend time in these forums when you get time and help someone else as you learn. They power of Community is in helping each other.

Enjoy!!

> **Vaedrah said:**
> [CENTER]**Problem Solved!**[/CENTER]

Thank you GooblyWoobly

I unmounted the partition and used

sudo mkfs.vfat -n Vaedra /dev/sda1

and it worked! The contents disappeared (no worries) but this time the label changed to "Vaedra"

So perhaps the only way to change a **_partition_** label is to reformat it :)

Thanks also to unutbu and taurus for your suggestions - I have learned a lot from the exercise!

---

### Post by Vaedrah on 2009-01-16
I couldn't agree more GooblyWoobly

---

