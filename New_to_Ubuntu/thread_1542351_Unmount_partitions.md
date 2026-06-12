---
title: "Unmount partitions?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Ranavalona on 2010-07-30
So, I figured I'd try Ubuntu out, and during the install, it tells me to unmount a partition labeled /dev/sda. So I ignored that, figuring I wouldn't mess with it. (total newbie at this) On the next page, it says that /dev/sda1 is Windows Vista, which I don't use, and /dev/sda2 is WIndows 7, which I do. What would happen if I unmounted the partition? Does that help the install in some way?

---

### Post by Zorgoth on 2010-07-30
/dev/sda is not a partition but the hard drive.

Partitions have numbers at the end.

There should not be any problems with the installation as long as there is some free unpartitioned space to install Ubuntu in.  What exactly was the message you got?

---

### Post by Mark Phelps on 2010-07-30
> **Ranavalona said:**
> So, I figured I'd try Ubuntu out, and during the install, it tells me to unmount a partition labeled /dev/sda. So I ignored that, figuring I wouldn't mess with it. (total newbie at this) On the next page, it says that /dev/sda1 is Windows Vista, which I don't use, and /dev/sda2 is WIndows 7, which I do. What would happen if I unmounted the partition? Does that help the install in some way?

Whatever you do, do NOT allow the Ubuntu installer to shrink either the Vista or the Win7 partition to make room for Ubuntu.  Doing so runs the risk of rendering the shrunk partition unbootable.

Instead, use the Vista/Win7 Disk Management tool to shrink the appropriate partition to make room for Ubuntu, and leave the new space as unallocated.  Then, boot from the Ubuntu CD and choose the "user largest free space" option to allow it to partition that space and install itself.

---

### Post by nishant.singh28 on 2010-07-30
You could also use gparted to free up space....as long as you leave enough space on the Windows drive free. My experience has been better with Gparted than Windoze Partition manager because although it takes longer, gpartd does a more thorough job of it. So just use gparted if the Windoze partition manager doesn't work(on a fragmented drive, it actually won't) to free up space.

---

