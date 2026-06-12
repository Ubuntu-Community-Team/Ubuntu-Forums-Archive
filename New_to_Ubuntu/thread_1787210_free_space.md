---
title: "free space"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by Wayneedelen on 2011-06-20
How can I make use of this free space? I have 35g available but I'm not sure how to get use of it.
Please see the image.

Thanks,
Wayne

---

### Post by jemofthewest on 2011-06-20
You need to mount it to use it.  First, make a new directory: (note: caps mean don't quote, something to figure out on your own)

```
sudo mkdir /mnt/DIRECTORYNAME
```You need to find out what the name of the partition is.  Should be in the output of:

```
sudo fdisk -l
```Look for a listing around the size your looking for (30gb) and replace the name of it with HD* below. 

Then, mount it with:

```
sudo mount /dev/HD* /mnt/DIRECTORYNAME
```
Then just access it from the mount point (/mnt/DIRECTORYNAME).

Hope this helps!

Note: This is a temporary solution.  If you want to make it happen all the time on startup, it'll be good to learn about fstab.  See link below:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by sffvba[e0rt on 2011-06-20
Hmmm... the easier way to mount the 35GB to make it useable is in the very same application you where using when you made the screen shot.  Click on the 35GB partition and then click on mount...  Not sure you can make it mount every time from boot from 
there though...


404

---

### Post by SoFl W on 2011-06-20
It  looks like "/" is only 4 gigs, I would make the 35 gigs the "/home" partition.
Unfortunately I have had a long day, and I am sure if I explained it, I would screw it up for the poster.

---

### Post by psusi on 2011-06-20
Boot from the livecd and use gparted to resize the existing partition to use the free space.

---

### Post by wildmanne39 on 2011-06-21
Hi, here is a guide for resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by -kg- on 2011-06-21
What I'm seeing from the graphics is that the 35 GB is not a partition at all, but free space.  Did you delete a partition from that space?

Sda5 and sda6 seem to be the two partitions you are operating from, with sda5 as "/" and sda6 as swap, both contained within an Extended partition.

If you want to do use the space for Ubuntu, you will first need to expand the Extended partition into that free space, then extend sda5 into it.  In this configuration, I don't know what the designator will be for the Extended partition, but it will be something between sda1 and sda4.  This must be done using Gparted from a Live CD or USB, since you can't perform operations on mounted partitions.

For further information on partitioning operations, read at the link in my signature block.

---

