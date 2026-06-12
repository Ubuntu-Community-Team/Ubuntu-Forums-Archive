---
title: "Hard disk with possible bad blocks :("
date: 2009-03-09
forum: New to Ubuntu
---

### Post by mr-woof on 2009-03-09
I'm dual booting between xp and ubuntu 8.10 at the moment, i saw an error message last night in the xp management snap in about some bad block on one of my disks. 

Now i'm spending a lot more time in ubuntu, i've a few questions :)

1) How can i monitor this in ubuntu, logs etc?
2) Does the ext3 file system moan the the disk has bad blocks?

Thanks all

---

### Post by albandy on 2009-03-09
Windows can't see linux partitions without a driver, so I think there's no problem with ext filesystems.
Maybe a bad shutdown can cause this.

In Linux
see /var/log/messages
if a I/O error apears from a hd device probably it's phisically damaged.

---

### Post by mr-woof on 2009-03-09
The disk is just a ntfs disk that both operating systems can see, i've had a look in /var/log and i can't see any i/o logs

Is there any others i should be looking for ?

---

### Post by albandy on 2009-03-10
do a chkdsk in windows of your ntfs disk

---

