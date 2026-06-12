---
title: "resizing partitions in 9.10"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by albert s on 2010-01-10
hi, Im trying to resize partitions on my friends laptop,
he has installed 9.10 with 45G for /home
1G for swap
and about 5G for /
Im trying to expand the / partition.
I have used Gparted from the liveCD to try and change these, but as swap is between /home and / I cannot change size of /
can i reinstall and change the partition order and NOT reformat /home ?
would this save the files on /home and just reinstall to / ?
thanks for your help.
I have backed up the files just in case.

---

### Post by raymondh on 2010-01-10
> **albert s said:**
> 
can i reinstall and change the partition order and NOT reformat /home ?
would this save the files on /home and just reinstall to / ?
thanks for your help.
I have backed up the files just in case.

Yes.  

You format and select mountpoint for root (/).  You format and select filesystem for SWAP.  **You select mountpoint for /home but _DO NOT FORMAT_**.  Also, use the same username and password (case sensitive) as the original.

There could be another way.  It might just have to be creating an empty space, moving partitions around ... and getting that empty space beside / so you can extend root.  Could you post a screenshot of gparted?

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


Raymond

---

### Post by sahabcse on 2010-01-10
Try to use LVM for partition then we can able to extend the size of the partition

---

### Post by albert s on 2010-01-10
here is a screenshot, as you can see Ive shrunk sda2, but i cant make sda4 any bigger cause swap is in the way.

---

