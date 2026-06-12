---
title: "Add More Space To Partition in Ubuntu Server"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by xAnarChisTx on 2009-01-22
Hey everyone.  I have looked all over the place, and I cannot find the answer to my question.  How do I go about adding more space to the partition in Ubuntu Server?

The was that it is set up is that only 30GB is set up for Ubuntu server, but the hard drive has 196GB available.  How do I take some of the 196 available, and use it in the current Ubuntu Server partition, to expand from 30GB?

I have tried to use gparted, but all I get for a response is:

(gparted:899): Gtk-WARNING **: cannot open display:

Which I can only assume it is because it is command-based, and not graphical.

Can someone please help me on my situation?

Thanks!

---

### Post by theozzlives on 2009-01-22
get the gParted Live CD

---

### Post by jerome1232 on 2009-01-22
Hopefully this guide will get you working with fdisk and ext2/3 tools for manipulation partitions and filesystems from the command-line.

--edit-- forgot to paste the link!
[http://www.linux.com/articles/32002](http://www.linux.com/articles/32002)

---

### Post by xAnarChisTx on 2009-01-22
Wow, that was fast!  Now, the thing is, I don't want any of the original partition to be deleted.  Will this process delete any of the information on the 30GB if I increase it?

---

### Post by xAnarChisTx on 2009-01-22
Another thing.  The type of file system I am trying to get space from is labeled as 'fuseblk'.  How would I be able to take some of the space from 'fuseblk', and make it into 'ext3' for me to add to the current partition?

---

### Post by DezSP on 2009-01-22
Growing partitions is usually painless, but you should **always** back up valuable data before attempting any sort of re-partitioning. If there is another partition in the way, you will either need to delete or shrink it to make room for the other partition to grow. This is all fairly straightforward using gParted, I suggest you do it all from their own LiveCD.

---

### Post by jerome1232 on 2009-01-22
> **DezSP said:**
> Growing partitions is usually painless, but you should **always** back up valuable data before attempting any sort of re-partitioning. If there is another partition in the way, you will either need to delete or shrink it to make room for the other partition to grow. This is all fairly straightforward using gParted, I suggest you do it all from their own LiveCD.

I think you would be best off using gparted as well if you aren't already very familiar with working with partitions. fdisk gives you to much control if your unsure of what your doing.

---

### Post by xAnarChisTx on 2009-01-23
Another thing that I forgot to mention.  I am not physically near the Linux server, and at least my only method of access is through a terminal. (I am about 500 miles away from the actual server.)

I would like to attempt to do this remotely through the use of fdisk, and would kindly ask for assistance on how to do so.  I have looked over the link that jerome1232 has posted, and I understand the use of it, but need further assistance on what I need to do to shrink the 'fuseblk' partition in order for the 'ext3' partition to grow.  Would that be with the use of fdisk, or other programs as well?

---

### Post by handydan918 on 2009-01-23
> **xAnarChisTx said:**
> Another thing that I forgot to mention.  I am not physically near the Linux server, and at least my only method of access is through a terminal. (I am about 500 miles away from the actual server.)

I would like to attempt to do this remotely through the use of fdisk, and would kindly ask for assistance on how to do so.  I have looked over the link that jerome1232 has posted, and I understand the use of it, but need further assistance on what I need to do to shrink the 'fuseblk' partition in order for the 'ext3' partition to grow.  Would that be with the use of fdisk, or other programs as well?

While you're waiting for jerome to get back with you, may I suggest...
Do the fdisk operations on a local test machine to make sure of your syntax, etc.

500 miles can be a long drive just to load a cd....

---

### Post by louieb on 2009-01-23
Might want to report this thread and have it moved to the [server platform ]("http://ubuntuforums.org/forumdisplay.php?f=339")section of the forum. 
A partition of type** fuseblk** is formated with the **NTFS** file system so you will need to use **ntfs-tools **to shrink and move it around. As **jerome1232** there are tools like fdisk and sfdisk that you can use to manipulate the partition table and grow the ext3 file system.   

Depending on how the disk is currently partitioned in may or may not be possible to take space from the NTFS partition and add it to the ext3 partition. In fact it may not even be on the same hard drive. In that case its only possible if  you convert the server to use LVM.  Good Luck.

---

