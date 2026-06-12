---
title: "help with windows partitions"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by poppingcorn on 2010-11-12
So I recently deleted my windows partition due to me never using windows.  There were two partitions, one for the install which was about 20gb and one that was the windows recovery, about 5gb.  

I would like to reclaim the unused partitions for my ubuntu partition, but I have absolutely no idea where to begin.

---

### Post by Hippytaff on 2010-11-12
There is a partition manager in ubuntu (In system somewhere) or you can use Gparted to resize partitions
[http://en.wikipedia.org/wiki/GParted](http://en.wikipedia.org/wiki/GParted)
 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
 
Edit -> oh and back important stuff up just in case :-)

---

### Post by AngusH on 2010-11-12
Also, you'll have to run that from a live cd because you can't resize mounted partitions.

---

### Post by poppingcorn on 2010-11-12
Ok, Ive had gparted but i cant find anything in it that does what i want, so im thinking i cant.  do i have to create a new partition table and erase everything?

---

### Post by Hippytaff on 2010-11-12
You should be able to resize the ubuntu partition (think theres a slide bar thing) from the live CD using Gparted

---

### Post by coffeecat on 2010-11-12
> **poppingcorn said:**
> Ok, Ive had gparted but i cant find anything in it that does what i want, so im thinking i cant.  do i have to create a new partition table and erase everything?

Don't create a new partition table or you'll lose your Ubuntu.

Boot from the Ubuntu live CD and open Gparted. It sounds as though your Linux partitions may be in an extended partition and you'll need to swapoff the swap partition before you can resize them. Take a screenshot of the Gparted window in the live session and post it; then we can see what's going on.

Yes, you **can** do what you want with Gparted.

---

