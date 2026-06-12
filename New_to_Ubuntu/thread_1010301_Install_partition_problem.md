---
title: "Install partition problem"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by theoldgit on 2008-12-13
I have just tried to install Ubuntu 8.10 and failed miserably.
Using the windows Vista partition tool i created an unallocated area of the HDD in which to install Ubuntu. When I came to install and get to the partition section I chose "use the maximum free space" (or something like that, cant remember the correct words). It then shows a before and after diagram which has Ubuntu using 100% of the drive and NO Vista. I need to keep Vista so this a no-go for me.
Any Ideas?

---

### Post by Michael.Godawski on 2008-12-13
hi theoldgit, 
first make a back-up of your important vista files, before even thinking about partitioning :p

then have a look at aysiu's guide:
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

perhaps you can use the guided resize option.

---

### Post by taurus on 2008-12-13
From the LiveCD, use gparted (System -> Administration) and create a partition out of that unallocated space.  Then, format it to ext3.  Then install Ubuntu and when you get to the partition part, tell the installer to use that new partition.

---

### Post by logos34 on 2008-12-13
run this in a terminal:

sudo fdisk -l 

what does it show?

If you really did overwrite vista, you can probably recover it using TestDisk.  

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
(>"Recovering an accidentally deleted NTFS partition")

---

### Post by theoldgit on 2008-12-13
I was not going to re-partition my drive as thats already donr. I have plenty of free space.
I selected "Guided - use the largest continuous free space"
As you can see the largest continuous free space is not being used, rather the whole disk is.

[[IMG]http://img87.imageshack.us/img87/4525/partitionlo0.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=partitionlo0.jpg)

---

### Post by taurus on 2008-12-13
Why don't you use gparted from the LiveCD and create two more partitions:  one for / (format it as ext3) and a smaller one for swap (format it as swap).  Then when you get to that partition part again, pick the Manual option and tell the installer to mount the new ext3 partition to / and it knows what to do with the swap partition.

---

### Post by theoldgit on 2008-12-13
OK Ill try that. From what i remember going manual would not allow me to change anything, which seemed a little strange. Anyway as its midnight here I'll try in the morning when my head is clear. Thanks for your help so far

---

### Post by lift_test on 2008-12-13
I always favour using the Alternate CD.  This gives you the option of manually allocating space.  This is fine but you must check beforehand in Vista which partitions are which.  If you are unsure abort the install and recheck.

---

### Post by richaoj on 2008-12-13
I had the same problem - this is actually a bug in the ubiquity installer where the little picture SHOWS ubuntu taking up the entire disk, but is not actually taking up the entire disk.  Like someone said, backup whenever you mess with partitions, choose the "use largest contiguous free space" option, and go for it.  

Link to bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/289663](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/289663)

Again, the picture is not accurate and ubuntu will not take up the entire drive.  

OJR

---

