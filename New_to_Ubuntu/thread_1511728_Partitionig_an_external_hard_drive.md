---
title: "Partitionig an external hard drive"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-06-17
-
The hard drive which I wish to partition is plugged into a laptop which is running XP.
I have loaded Ubuntu 10.4 from a live CD
I have opened  gparted and it has found the existing two partitions on the laptops internal hard drive /dev/sda1 and 2.

And I can see /dev/sdb which is 1.8 Terabytes and currently formatted in FAT 32.

I want to finsih up with 4 partitions of about equal size and with at least two of them formatted in ext 3.

AND I don't want to screw up the existing internal hard drive.

So, Please, gently. gently  :D

Sandy

---

### Post by drascus on 2010-06-17
I use the gparted boot CD personally for partitioning my drives. it should allow you to resize partition and format the drive in any extension you like. I am no sure exactly what your asking in your question I can only say read all the documentation and be careful. And as always back everything up.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Sandy.1 on 2010-06-17
Well I went ahead, carefully.


I appeared to have instructed dev/sdb1 from 1.82 Tera down to 439.45 GB and create a new operation /dev/sdb2 of 500 GB.

Set it running and the error message came up after about 30 seconds.

Happily everything seems to have failed safely and I am now back looking at /dev/sdb1 filling the device at 1.82 TeraB

Now going to try formatting /dev/sdb/1 as ext3.

That operation hs now been running without failing for about ten minutes. I have no idea how long it is going to take !!!

Sandy

---

### Post by Sandy.1 on 2010-06-17
The good news is that I appear to have made great progress.

Limiting mu use of Gparted to one operation at a time has been very successful and I now have my 1.8 TB external hard drive sliced up into 3 standard partitions and an extended partition which is also split up four ways.

I started with an empty hard drive but I see on the Gparted screen that all of my partitions have some USED space. In each case to 1 or 2 %.

Is there a simple explanation of this?

Sandy

---

### Post by bumanie on 2010-06-17
The space taken up is called data structures. It basically is put aside so that the operating system can keep track of where all your files and directories etc. are stored so it knows where to go and retrieve them when the are needed. In unix/linux the data structures are called inodes - you can read about them [here]("http://en.wikipedia.org/wiki/Inode")

---

