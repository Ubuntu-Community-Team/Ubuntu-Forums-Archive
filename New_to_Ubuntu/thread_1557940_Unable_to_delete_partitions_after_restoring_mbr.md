---
title: "Unable to delete partitions after restoring mbr"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Sasman20 on 2010-08-21
Hi there
 
I have restored my mbr and now my pc boots straight into windows so I then shut down and ran ubuntu from the cd but it would not let me delete the non windows partition saying i have to unmount any logical drives higher than 5
 
Does anyone have any ideas?

---

### Post by Rubi1200 on 2010-08-21
Hi,
please run Ubuntu from the CD again (in live mode) and post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by gandaran on 2010-08-21
delete them using windows, its easier!

---

### Post by pythagoreanmetronome on 2010-08-21
If you run the live CD and actually try to "install" ubuntu you will get to the point where it asks you where you want to install and if you select custom and then edit your partitions from there you will be able to very easily delete the windows partition and then after that you just cancel the install and take out the live CD and you will have deleted your windows partition.

---

### Post by anewguy on 2010-08-21
It's also quite possible you need to turn swap off.  If there is an existing swap partition the LiveCD will use it.  Open a terminal window and type "swapoff", then go back and try gparted again from the System/Administration menu while running the LiveCD.

Dave ;)

---

