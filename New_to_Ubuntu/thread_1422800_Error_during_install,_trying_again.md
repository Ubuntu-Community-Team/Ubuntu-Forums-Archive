---
title: "Error during install, trying again"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Choragos on 2010-03-05
I was trying to pop 9.10 on my laptop which is also running windows 7.  In retrospect I (a) should have used the windows installer that's available or (b) run a check of the CD I was using.  Anyway, the installation died AFTER making the partitions.  Now, while trying to install Ubuntu (on a new CD), my partitioning options become complicated.  It thinks 9.10 is already on there, so it's trying to partition my windows side in half.  So I have

/sda1, /sda2,/sda3, which are all fine and dandy, but now
/sda5 is the broken Ubuntu.  I'm not competent enough to specify my partitions manually on my own.  Is there a way to just overwrite this partition (they're all the right size)?  It didn't install enough of Ubuntu the first time for me to be able to boot to it and try to repair.  Windows can't see the new partition (at least without help).

From another forum, it sounds like I need to pick /sda5 in the manual section, use it as ext4, format it, and mount it from /     Is this correct?  Then what?

Thanks a bunch!

---

### Post by jerrrys on 2010-03-05
make it easy on yourself.  just make it free space and when you install ubuntu (guided install) it will detect the free space and install there.

---

### Post by Choragos on 2010-03-06
Easy on myself?  How un-sporting!

Thanks!

---

