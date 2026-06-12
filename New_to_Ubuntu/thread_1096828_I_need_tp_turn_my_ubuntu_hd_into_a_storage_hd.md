---
title: "I need tp turn my ubuntu hd into a storage hd"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by skywalkrNCSU on 2009-03-15
Hey guys, I have ubuntu installed on my external hard drive but my girl friend needs an external hard drive for storage and instead of buying a new one I figured I could just give her mine and then eventually put ubuntu on an internal hard drive.  How can I delete ubuntu and then make it so my external hd is now a storage device?

Thanks for the help!

---

### Post by taurus on 2009-03-15
Boot with Ubuntu LiveCD.  Then use gparted (System -> Administration -> Partition Editor) and remove all the partition on your external drive.  Now, create a new one that takes up all the space on the drive and format it to either ntfs or fat32.

---

### Post by skywalkrNCSU on 2009-03-15
> **taurus said:**
> Boot with Ubuntu LiveCD.  Then use gparted (System -> Administration -> Partition Editor) and remove all the partition on your external drive.  Now, create a new one that takes up all the space on the drive and format it to either ntfs or fat32.

thanks a lot!  I will try that right away

---

### Post by skywalkrNCSU on 2009-03-15
I am having a problem creating a new partition.  I delete the old one, go to create a new one, and when I hit apply it gives me an error and I can't even tell what the error is.

Any ideas?

---

### Post by taurus on 2009-03-15
Did you remember to unmount the swap partition first?  Highlight the swap partition and click the right button then swapoff to unmount it.  

Otherwise, post a screenshot of your external drive.

---

