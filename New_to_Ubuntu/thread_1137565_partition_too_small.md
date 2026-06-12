---
title: "partition too small"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-25
I accidently made my partition too small for my 64 bit ubuntu install. It said something about side by side install so I figured that it would give enough space, but I guess not. It keeps telling me that I don't have enough room to do much of anything. Can I make it bigger? My HD is not even close to full just that partition.

---

### Post by Noel96 on 2009-04-25
Hi,

If you boot from the LiveCD, you will be able to run GParted under Administration | Parition Editor (I think). This will allow you to resize your partitions. 

Resizing partitions can take a long time. Last time I did it, it took about 2 hours for the computer to systematically work through the drive. 

Good luck,
Noel

---

### Post by WatchingThePain on 2009-04-25
Hi,
gparted can be used for that [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by AndyCooll on 2009-04-25
Two options spring to mind:
1. Re-install Ubuntu and as you do select the "Manual" option at the partitioning stage. You can then manually choose the size of your Ubuntu partition.
2. Insert the Live CD, reboot and try re-sizing the partition using the Partition Editor (System > Administration) that is installed on the Live CD. Backup your home folder first if you have any important data.

:cool:

---

