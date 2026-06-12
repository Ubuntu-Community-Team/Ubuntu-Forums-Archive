---
title: "New machine, new install, new user, no hdd recognized"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by jipsoc on 2010-11-18
I had a new machine (Intel i7) built specifically to install Ubuntu 9.10.  I cant get past the Ubuntu install.
 
Downloaded the CD successfully, can run from the CD, On install it ends at recognizing the HDD (1TB) no choice to add (greyed).  I have scoured the forums and found a tip to **sudo apt-get -y remove dmraid** and that did not solve issue.  
 
I attempted to look at the bios and am not sure the disk was recognized there either.
 
Before I get carried away trying multiple tips should I use something like gparted live from boot disk to partition the disk independently then try to install Ubuntu?  Trying to move ahead cautiously but at the same time there is no data at risk here.  Time crunch is more concerning...

---

### Post by jrev on 2010-11-18
I think the best you can do is check first how is your hard disk.
The way to do it is there :
[http://ubuntuforums.org/showthread.php?p=10131542#post10131542](http://ubuntuforums.org/showthread.php?p=10131542#post10131542)
Hope it helps :p

---

### Post by Mark Phelps on 2010-11-18
Using GParted from the Ubuntu CD will certainly show you if the hard disk is recognized by your BIOS, because if that doesn't see it, GParted won't see it either.

---

### Post by mike555 on 2010-11-18
perhaps the HD is not formated right .............. I would use the live cd and gparted to format it , then partition it .

---

