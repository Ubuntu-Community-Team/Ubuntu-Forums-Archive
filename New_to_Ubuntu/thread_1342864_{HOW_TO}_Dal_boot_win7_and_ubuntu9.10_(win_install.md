---
title: "{HOW TO} Dal boot win7 and ubuntu9.10 (win installed 1st)"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Borko4vp on 2009-12-01
ok here`s the thing! i`ve been using win7 for a while.... so i decided to try linux(ubuntu9.10)!I made new ext3 partition downloaded and burned Ubuntu....start instalation and when it came to partitioning... BANG! it says THERE IS NO OS ON THIS COMPUTER and there is no SIDE BY SIDE INSTALL WITH WIN option(which i saw somewhere in tutorial),and the only options i can use r USE ENTIRE DISC and MANUAL PARTITIONING(which i tryed and still there r no my partitions visible there, only NEW PARTITION TABLE button)!!

any help whould be usefull!ty in advance!

btw: sry my bad english!

---

### Post by Mark Phelps on 2009-12-02
yr english is good enuf for me to understand ...

Since 9.10 defaults to Ext4, my guess would be that it doesn't see the Ext3 partition because it wants an Ext4 partition.

You didn't say how you formatted the Ext3 partition, but if I were you, I'd download the GParted LiveCD from distrowatch, burn a CD from it, boot from it, and use the Partition Editor to remove the Ext3 partition and replace it with Ext4.

Then reboot using the Ubuntu CD and see if it sees the Ext4 partition in manual partitioning.  IF it doesn't, you have other problems.

---

### Post by Locke_99GS on 2009-12-02
The Ubuntu installer (Ubiquity??) can handle the partitioning just fine, and does most of what gparted does. (I believe it used parted as a back-end) 

In the manual partitioner, there should have been a large partition there already, slice off a section of this and format to ext3 or ext4, and make another small slice (a few hundred meg or so) for swap space. (Swap space is optional if you have lots of RAM) Mark the ext partition you will be creating to be used as "/" and continue with the install. Grub2 should detect Win7 when it gets to that point, and sort everything out for you.

---

