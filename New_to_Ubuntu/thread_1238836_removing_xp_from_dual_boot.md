---
title: "removing xp from dual boot"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by misswham on 2009-08-12
I have installed vbox with windows as guest.  i am truly happy with it and i want to shrink the xp part of my harddrive to almost nothing, opening up more harddrive space for ubuntu 8.04.  Is there a way i can do this without messing up my ubuntu part and also is there a way I can increase the harddrive space on my xp on vbox also without reinstalling it?

---

### Post by raymondh on 2009-08-12
> **misswham said:**
> I have installed vbox with windows as guest.  i am truly happy with it and i want to shrink the xp part of my harddrive to almost nothing, opening up more harddrive space for ubuntu 8.04.  Is there a way i can do this without messing up my ubuntu part and also is there a way I can increase the harddrive space on my xp on vbox also without reinstalling it?

You can use gparted from the liveCD to shrink XP and grow Ubuntu (I'm guessing here ... you have Ubuntu root (/) and swap as logical partitions inside an extended)

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Make sure you have back-ups of your files.  Whenever you do partitioning work, there are NO guarantees.

Good luck and Happy Ubuntu-ing.

EDIT: When using gparted from the liveCd, it ought to unmount all partitions. However, just to be sure, rt. click on each partition and if given the option to unmount, do so.  For swap, select swapoff.  Also, you can download the latest [gparted]("http://gparted.sourceforge.net/") and use it, instead of the liveCD's version.

---

### Post by misswham on 2009-08-12
is there a way to make vbox bigger on harddrive?  I have the xp set to 7mbs and I would like to enlarge it to 20mbs.  Is this possible without messing anything up?

---

