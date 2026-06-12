---
title: "merge ubuntu &amp; swap (both primary) into extended / logical partitions"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by lightgeek on 2010-07-17
Hi,

I have a dual boot on my laptop between XP and Ubuntu with a storage partition.that gives me total of 4 primary partition
-Windows
-Storage
-Ubuntu
-Swap

I now want to add a OSX to my laptop in tripple booth. I did shrink the windows partition and now I realized that all my partitions are primary and cannot create a new one with the space I shrink from windows.

Is it possible to merge ubuntu and its swap into extended/logical partitions so I can create a new primary for Mac OS X?

right now my drive look like

-windows (NTFS)
-free space
-storage(NTFS)
-ubuntu(ext3)
-swap(linux-swap)

please help, I do not want to re-install linux or windows.

---

### Post by oldfred on 2010-07-17
Please do not make duplicate posts.

See
[http://ubuntuforums.org/showthread.php?t=1533085](http://ubuntuforums.org/showthread.php?t=1533085)

---

### Post by mbsullivan on 2010-07-17
A trivial way would be to get rid of the swap partition, use it's (primary) partition for OS X, and use a swap file. I find them much more convenient -- you can resize them, and you don't have to worry about any partitioning nightmares.

To create a swapfile (you can find this elsewhere, too):

(1) create an appropriately sized file
    - sudo dd if=/dev/zero of=/var/swapfile.swap bs=1M count=4096
(2) sudo mkswap /var/swapfile.swap
(3) sudo swapon /var/swapfile.swap
(4) add the following to the bottom of /etc/fstab:
    - /var/swapfile.swap  none  swap  sw  0 0

The name and location of the file is not significant. The size is, but it is arbitrary.

The only problem I've run into is poor hibernation support. I don't know if this would be a problem for you or not.

Mike

---

### Post by lightgeek on 2010-07-17
I never really use ibernation anyway. so What do I have to do to remove the swap partition?

---

### Post by mbsullivan on 2010-07-17
You can probably do it when you're installing Mac OS X. Just install over the swap partition.

If you really want, you can use a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and convert it to free space first, though.

If I'm understanding you right, you just want a primary partition, and you want to consume the rest of the drive... So in this case, your Mac OS X install will take the partition from swap, and consume all of its space + the free space you say you already have, filling the drive. You'll then create your swap file on the Ubuntu drive.

If you don't have enough room on the Ubuntu drive for the swap file, you might want to EXPAND it by an appropriate amount. This is possible with a GParted LiveCD.

Mike

---

