---
title: "Partition help!!!"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by jfalco on 2009-03-16
I'm trying to redo my partitions and here is what I am starting with:

[IMG]http://lh4.ggpht.com/_1WImETN1vto/Sb5naSPMPrI/AAAAAAAAAY0/UuGL2hdknb0/s800/GParted.png[/IMG]

Currently all my movies are setting on sda1 
I store a TON of movies and I want to created a seperate partition for /home and any others you guys think I might need.

?-Why can't I shrink my root partition? I tried unmounting it from the LiveCD and then shrinking it and it wouldn't let me. 

If everyone could just let me know how you would set up this HD I'd really apprciate it. Thanks!

Sys. info:

Ubuntu
  Release 8.10
  Kernel Linux 2.6.27-11-generic
  GNOME 2.24.1

Hardware
  Memory: 2.9 GB DDR-2
  CPU: Intel Core2 Duo T6400 @ 2GHz

HD
  ATA Hitachi HTS54322
  232.88 GB

---

### Post by FrostDust on 2009-03-16
I don't see a boot partition there; do you mean your root partition, sda5, which I assume is bootable?

Edit: Are you trying to shrink sda4 instead? That's a container for logical partitions sda5 and sda6. Shrink sda5 first, then sda4, then grow sda1 into the empty space.

---

### Post by jfalco on 2009-03-16
sorry meant root. :D

---

### Post by taurus on 2009-03-16
When you open gparted from Ubuntu LiveCD, you probably need to unmount swap partition, /dev/sda6, as well.  Just highlight /dev/sda6 and click the right button of your mouse and click swapoff.  Now, if you want to create a separate /home, you have to shrink /dev/sda5 to create another logical partition with that new space.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jfalco on 2009-03-16
What would be your guys recommendations fro partitions, should I have a separate /boot, etc. and what sizes?

---

### Post by prshah on 2009-03-16
> **jfalco said:**
> 
?-Why can't I shrink my root partition? I tried unmounting it from the LiveCD and then shrinking it and it wouldn't let me. 


Your root partition is part of an extended partition. To make any changes to it, you have to unmount all partitions in the extended partition (sda5, sda6). You can "unmount" sda5 by right clicking it and choosing "Unmount", and "swapoff" sda6 by rightclicking it and choosing "Swapoff". 

You will be able to resize root only if all the "key" icons disappear.

---

### Post by mikechant on 2009-03-16
> Why can't I shrink my boot partition? I tried unmounting it from the LiveCD and then shrinking it and it wouldn't let me. 

This is a bit odd. If you are running from the LiveCD no partitions should be mounted except the 'swap' partition sda6.

Anyhow, you should unmount any mounted partitions, in the case of the swap partition by right clicking on it and selecting 'swapoff'. You should not have any 'lock' symbols displayed.

Once you've done that, you should be able to shrink sda5. If you want to expand sda1, then you need to resize sda5 by moving its start point towards its end point (should be obvious what this means when you get the resize screen in gparted). Once you've done this you will have space between the start of sda4 and the start of sda5and can resize sda4 so it starts at the same place as sda5. Now you'll have a gap between the end of sda1 and the start of sda4 and in this space you can expand sda1 maybe leaving 20G at the end and then use the remaining space to create what will be sda2 for use as /home.
This would give you the following:
sda1 - primary partition containing your movies etc., now expanded to take up the space freed from sda5 minus what you want for /home
sda2 - primary partition for use as your new /home partition (at least 10Gb)
sda4 - extended partition containing sda5 and sda6
sda5 - logical partition containing your root file system, shrunk to required size (10-20Gb probably)
sda6 - logical swap partition

The usual warnings: partition resize can take a long time (hours) and should *not* be interrupted; any valuable data should be backed up first. You may need to edit /etc/fstab from the live CD (sudo gedit /etc/fstab from terminal) to get your system to boot after these changes - the fstab file by default does not identify partitions as sda5 etc. but uses a partition identifier called the UUID, and the UUID of sda5 may change due to the resize/move. If this is the case, the blkid command (sudo blkid) will give you the new UUID. You could do a blkid command before and after your changes and compare the result, and then you will know if this is an issue or not. 

After this, you will still need to actually move /home to use its new partition; I think there are lots of threads explaing this already.

---

### Post by FrostDust on 2009-03-16
> **jfalco said:**
> What would be your guys recommendations fro partitions, should I have a separate /boot, etc. and what sizes?

I'd recommend 15-30 for root (this includes /temp), I guess 10 or more for /home, depending on the size of files.  a seperate 1 gig /boot is usefull if you're gonna install more than one Linux OS.

---

### Post by prshah on 2009-03-19
> **mikechant said:**
> If you are running from the LiveCD no partitions should be mounted except the 'swap' partition sda6.

Actually, since swap is part of the extended partition, just enabling swap "locks" all the other (logical) partitions in the extended partition. The other partitions may not actually be mounted, but cannot modified nevertheless.

Mounting any one "logical" partition will lock the entire extended partition for changes.

---

