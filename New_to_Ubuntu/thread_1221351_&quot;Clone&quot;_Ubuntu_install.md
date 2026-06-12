---
title: "&quot;Clone&quot; Ubuntu install"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by skymera on 2009-07-23
Just got a new hard drive and i'd like to move my Ubuntu to it.

Preferably without reinstalling or losing anything. It's only a 10GB partition, is this possible?

My new hard drive reads at 105MB/s, which should be better at loading Ubuntu :)

---

### Post by nmaster on 2009-07-23
try using this.
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+recovery](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+recovery)

you could install ubuntu onto the new hard drive and then extract the tar you made to the new drive.

---

### Post by lukeiamyourfather on 2009-07-23
Don't do this without some research or someone else confirming it, but you should be able to do this with the dd command. For example.

```
dd if=/dev/sda of=/dev/sdb
```

That would clone sda disk to sdb block for block, also works with partitions, etc. I've not tried this before but have seen it suggested in several posts about disk cloning. Cheers!

---

### Post by rbc on 2009-07-23
Clonezilla is a good option, but I always use dd, as the previous post mentions. Just make sure you know which drive is which. Reserving the order, especially with a brand new empty hard drive would be a disaster

---

### Post by louieb on 2009-07-23
Have put in larger drives in a couple of times in the last few months.  

I hook both drives up either internal (fast) or with a USB (slow) enclosure. Using Gparted on a live CD (I use a [SystemRescueCd]("http://www.sysresccd.org/Main_Page"))  then just copy and paste the partitions from one drive to the other.

The advantage of using Gparted is the partitions can be resized and rearranged as you copy them to the new drive.  Works with both Linux and Windows installs. (Windows will want to run chkdsk). 

Not really a disadvantage but you do have to put boot-loader (Grub) code back in the MBR when done. (takes a minute or 2) 

[GPARTED DOCUMENTATION - COPYING]("http://gparted.sourceforge.net/larry/move/move.htm")

---

### Post by aysiu on 2009-07-23
If you use dd, don't forget to do it from a live CD, and don't forget to use *sudo* ```
sudo dd if=/dev/sda of=/dev/sdb
```

---

### Post by skymera on 2009-07-25
Ok, I've yet ti try this.

Thanks for replies :)

---

