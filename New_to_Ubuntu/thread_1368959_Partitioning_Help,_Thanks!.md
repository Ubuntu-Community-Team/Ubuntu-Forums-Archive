---
title: "Partitioning Help, Thanks!"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by phatlarry on 2009-12-31
So i just created a seperate partition and installed the lastest version of ubuntu. Been about 3 years since using linux so i'm a tad bit rusty. 

After creating the new partition and installing ubuntu i realized i didn't give the patition enough room.  I then booted to windows, shrank the volume by 10gigs then booted back to ubuntu.

I am now trying to add the unallocated space (just before the extended partition that ubuntu is on) to my logical partition inside of the extended partition that ubuntu is on.


Screenshot of Gparted:
[http://img685.imageshack.us/img685/263/gparted.png](http://img685.imageshack.us/img685/263/gparted.png)

Help would be aprpeciated. Both partitions are empty so i can format them as needed. Just need to figure out how to get the unallocated space inside the extended partition so that i can add it to the Logical partition.

---

### Post by diablo75 on 2009-12-31
While Gparted is great, it's not very useful when you're running it off of the hard drive you intend to make changes to.

There is a Gparted ISO you can download and burn to make a LiveCD to boot from. 

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

The most recent version has a bug (as the link above says) but an alternate link to the next previous version is also there.  Use that to resize your ext3 partition.

---

### Post by danastasio on 2009-12-31
Use the liveCD that you used to install the OS. Then to go System>Administration>Partition Editor. You can use that version of Gparted to edit the partition properly.

---

### Post by bodhi.zazen on 2009-12-31
> **phatlarry said:**
> So i just created a seperate partition and installed the lastest version of ubuntu. Been about 3 years since using linux so i'm a tad bit rusty. 

After creating the new partition and installing ubuntu i realized i didn't give the patition enough room.  I then booted to windows, shrank the volume by 10gigs then booted back to ubuntu.

I am now trying to add the unallocated space (just before the extended partition that ubuntu is on) to my logical partition inside of the extended partition that ubuntu is on.


Screenshot of Gparted:
[http://img685.imageshack.us/img685/263/gparted.png](http://img685.imageshack.us/img685/263/gparted.png)

Help would be aprpeciated. Both partitions are empty so i can format them as needed. Just need to figure out how to get the unallocated space inside the extended partition so that i can add it to the Logical partition.

You need to manage your partitions from a live CD as you can not resize a partition that is in use (so you can not resize your ubuntu partition while you are booted into Ubuntu)

---

