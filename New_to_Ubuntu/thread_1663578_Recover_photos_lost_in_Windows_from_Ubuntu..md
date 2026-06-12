---
title: "Recover photos lost in Windows from Ubuntu."
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Krissi_Litz on 2011-01-09
A few months ago I installed Ubuntu in place of Windows, I did not back up my photos, and it got BSOD and now Windows cannot be reached. Ubuntu works fine, but I'm really worried about my photos which were from 5 years+. Since I can't access Windows where the photos are, are they still there, if yes, how do I retrieve them? 

I also heard that I can just take the hard drive out and put it in a new computer and install "getbackdata" and everything should work, is that true?
:confused:
(Absolute beginner)

---

### Post by jcolyn on 2011-01-09
If you installed over the Windows partition then your photos are lost. However if the Windows partition is still there you should be able to get them back.

In the Ubuntu terminal type ```
sudo fdisk -l
``` (that's a lower case L) and see if you have a Windows ntfs partition. If so type ```
sudo grub-update
``` then reboot and see if you get a grub menu letting you boot into Windows.

If data has been written over 3 or more times getting the data back is next to impossible. If you have been using Ubuntu most if not all data probably has been written over..

---

### Post by bodhi.zazen on 2011-01-09
first, stop using the partition, you should boot a live CD and STOP using your hard drive.

From the live CD, try testdisk and photorec.

The are in the repos can can be installed on the live CD.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

In the future, make backups, and make backups before you edit your partitions or install an OS.

---

