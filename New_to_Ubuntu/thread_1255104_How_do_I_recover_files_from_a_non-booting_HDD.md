---
title: "How do I recover files from a non-booting HDD?"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by kdlp313 on 2009-09-01
I've got a 40GB HDD that had Ubuntu 9.04 on it.  It crashed and never booted again.  How can I recover the data off of it?  We're only talking about a few MB's worth of files, here, but they're important.

I'm running Hardy on my current drive and I've tried plugging the old drive in as a slave, but it won't mount.  I've also tried booting with the Ubuntu Desktop CD but I get an 'Error 25'.

My Partition Editor sees the disk, and when I click on 'Information', it warns, 'Couldn't find valid filesystem superblock'.  I should mention that the disk's filesystem was ext3.

Anyone able to help?  I'll need a step-by-step cos I'm rather new to Ubuntu.  Thanks!

---

### Post by anujpathania on 2009-09-01
If it crashed completely then probably I am sorry it may not be possible to recover data at all. Probably you should take it to a recovery professional.

---

### Post by tomBorgia on 2009-09-01
Hi,

Depending on how "crashed" the disk is you may have some luck trying [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to see if you can recover any partition information - If it repairs the partition table correctly you'll be able to mount the disk and read from it.

If you can't recover the partition table at all you'd probably need to use "dd" to copy the data wholsale from the disk then use something like "foremost" to scan for file headers. Which might work.

If dd won't copy anything across then the disk is probably physically damaged and will need the attention of a professional... £££

Good luck!

---

### Post by earthpigg on 2009-09-01
combine dd and testdisk with putting it in the freezer (inside a zip-lock bag) set to max overnight.

the freezer thing wont hurt your chances, but may give it another 2 minutes or 2 hours of use - maybe enough time to dd it.

google 'put dead hard drive in freezer' if you dont believe me :D


grats, you are now a qualified data recovery dude.

---

### Post by tomBorgia on 2009-09-01
> **earthpigg said:**
> combine dd and testdisk with putting it in the freezer set to max overnight.

the freezer thing wont hurt your chances, but may give it another 2 minutes or 2 hours of use - maybe enough time to dd it.

google 'put dead hard drive in freezer' if you dont believe me :D




No. Freaking. Way.

Will try that next time I've got a goner!!! Thanks!

---

### Post by cascade9 on 2009-09-01
I would assume that the drive does appear in the BIOS. If you cant find the drive in BIOS, you have problems. 

Yep, the freezer bag trick can work. Not something to try unless you cant see the drive in BIOS, or the drive starts and runs, but only for a short while. I've run a hdd inside the freezer once. :D

---

### Post by XCan on 2009-09-01
Wow, freezer hehe. I would have thought it would kill especially fluid bearings. :p

---

### Post by kdlp313 on 2009-10-21
Okay, this is taking way too long to solve on my own, and my gut tells me that this disk should be easily recoverable.  Please help!!!

Testdisk can see the partition structure and all my files.  I'm just unfamiliar with Testdisk.  If anyone can assist me, I'd greatly appreciate it.

For further details, refer to this thread:
[http://gparted-forum.surf4.info/viewtopic.php?id=13664](http://gparted-forum.surf4.info/viewtopic.php?id=13664)

---

### Post by Paqman on 2009-10-21
Not sure I can help you kdlp313, but i'd just like to point out that this kind of thing is exactly why it's worth setting up some kind of redundant data storage. Hard drive failures are all too common. For those of you reading this who have data on a hard drive that has no redundancy, start thinking about protecting yourself now.

---

### Post by QLee on 2009-10-21
Since the drive spins up and you see filesystem structure on it, have you tried running a filesystem check (fsck) on the unmounted drive to see if it can recover the superblock for it? Testdisk probably can do that too, once you become familar with it.

---

