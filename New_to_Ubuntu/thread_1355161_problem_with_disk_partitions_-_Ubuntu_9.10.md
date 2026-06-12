---
title: "problem with disk partitions - Ubuntu 9.10"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by pe1800 on 2009-12-14
My setup:

Master HD: 20GB, dedicated to Windows XP

Slave HD: 80GB, 2 x 10GB Windows partitions, remainder given over to 3 partitions (/, /home and swap) for PCLinuxOS.

Problem:

Whereas I prefer Ubuntu to the other OS, the Ubuntu installer or GParted, while it correctly identifies WXP on the master drive, will not recognize any partitions on the slave drive and marks the whole drive as unallocated. 

It makes no differnce whether the portion of that drive not used by Windows partitions (about 55GB)is truly unallocated, occupied by an empty Windows partition or occupied by Linux partitions. 

I want to replace PCLinuxOS (which does recognize all those partitions) with Ubuntu 9.10 but cannot risk it under these conditions.

I wonder why GParted calls these 2 drives sda and sdb. These are not SATA but IDE/ATA drives.

Not surprisingly,with Kubuntu 9.10 and Linux Mint 8  I have experienced the same problem as with Ubuntu 9.10.

I would appreciate some assistance ot comment.

Best regards and thanks! :)

---

### Post by Locke_99GS on 2009-12-14
I just recently had a simlar issue with some HFS+ partitions not being properly detected by parted, even with the proper libraries installed. This didn't concern me, as I didn't care abot the contents of the entire drive, so unfortunately I don't have a solution for you. Sorry.

IDE drives have been lumped in with SATA drives for a while now. It confused me too, when my hd? drives suddenly became sd?. Fedora shows them all as sd?, similarily.

---

### Post by pe1800 on 2009-12-14
Thank you! At least, it shows we are not alone. Perhaps, the Ubuntu people will now take note of it. Provide a fix?

---

### Post by bodhi.zazen on 2009-12-14
Note: I fixed the title for  you (I presume you mean 9.10)

---

### Post by cariboo on 2009-12-14
I recently had a similar problem, I found If you mount the drive before starting the installation, it will be detected properly and the partitioner will ask if it can unmount the disk before continuing. It's not the way it should be, but at least it works.

---

### Post by pe1800 on 2009-12-14
Well, thank you!

Yes, 9.19, that was a typo. Saw it myself when it was too late.

I will certainly try that, mount the drive first.

Thank you all again!

---

### Post by pe1800 on 2009-12-14
Thank you. I made sure all partitions on the slave drive were mounted. Unfortunately, it made no difference, GParted detected none of them.

I wish there was some way......I really like Ubuntu.

Does a moderator look at these posts.......I mean someone who's part of the Ubuntu organization?

---

### Post by Yvan300 on 2009-12-14
Not all the time, but what you should do is check and see if this is a bug on launchpad and file a bug report. Check the instructions provided on the forums.

---

### Post by oldfred on 2009-12-15
I have had issues with Ubuntu not seeing a NTFS partition because it was not cleanly shutdown and required check disk to be run. Since the NTFS partitions are not part of the operating system you have to manually run the check disk routine in windows.

---

### Post by Marvin666 on 2009-12-15
On the slave, which ones are the logical partitions?

---

