---
title: "Partition problem"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by adobrakic on 2009-08-15
I have an Acer Aspire 6930 laptop, which came with Vista installed. It also came with two separate partitions, and I want to install Ubuntu on the second one, which has around 100gb, which you can see [here](http://img20.imageshack.us/img20/5549/screenshotdnf.png) (sda3). What I don't understand is why it doesn't let me choose that portion of my hard drive. If I'm not mistaken, previously there was an option to use the "largest unused space." Anyone got anything for me?

Thank you.

---

### Post by sideaway on 2009-08-15
Specify partitions manually. You should be able to pick exactly where to install Ubuntu.

Note: Careful no to wipe vista. Partition editing can be potentially fatal to your files. Also keep in mind you'll need a swap file. and you may wish to keep / and home on seperate partitions. Makes reinstallation/switching distros easier.

---

### Post by adobrakic on 2009-08-15
I'm not really sure how I can create a swap, /, or home :p
any websites that show me how?

---

### Post by sideaway on 2009-08-15
Ubuntu documentation has lots of information. Hopefully this page can get you started:

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Have a browse around the documents, there's a lot of helpful information.

---

### Post by Tclarkie on 2009-08-15
LFS, download the book, i think its in the 3rd chapter

---

### Post by adobrakic on 2009-08-15
> **sideaway said:**
> Ubuntu documentation has lots of information. Hopefully this page can get you started:

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Have a browse around the documents, there's a lot of helpful information.

Thanks for the link, but I'm not really understanding it. [Here's](http://img232.imageshack.us/img232/2312/screenshotdevsdagparted.png) what my HDD looks in GParted. The tutorial has me start off by creating a partition for swap, but I can't do that because I already have four partitions, I can't create another one.

> LFS, download the book, i think its in the 3rd chapter 

Thanks, I'll check it out.

---

### Post by sideaway on 2009-08-15
Resize sda3 so it's slightly smaller. The use the space saved to create a swap partition.

---

### Post by Twittery on 2009-08-15
After booting from live cd follow the instructions and when you reach the partition table check the box for specify the partiton manually ( Create a custom layer) . After clicking next delete the /dev/sda3 partition and format it into ext3 . And there you are . (There is quite no need for a /home partition though)

---

### Post by Bartender on 2009-08-15
While it's been a wonder to watch the entire Ubuntu experience get better and better, this is one area where they have for some inexplicable reason gone the other way.  The installer doesn't tell you if the partitions are primary or extended.
I have an Acer 5920 laptop that's dual-booted.  But there were some hiccups along the way.
  
The #1 obstacle to dual-booting my Acer (I will assume yours is the same) was that it came with 4 primary partitions.  That's why the Ubuntu installer is giving you limited options.  

I screwed around with mine until I foobar'ed Vista so it wouldn't boot.  Fortunately, the very first thing I'd done with the new laptop was burn the recovery DVD's.  So I popped in the recovery DVD's and followed the steps.

The recovery DVD's erased the Acer-installed recovery partitions.  When they were done, there was just one big Vista partition.  Whoo-hoo!

I used the Vista partitioner to shoulder Vista aside, then used a GParted LiveCD to create an extended partition out of the free space, then installed Ubuntu.

A guy I was talking with on a different forum who had a 5920 came up with a different solution.  He used a GParted LiveCD to wipe the drive, then he created a primary partition, formatted as NTFS.  He only used the first half of the drive.  When he popped in the first Acer recovery DVD, it recognized and installed to the NTFS partition, leaving the rest of the drive alone!  From there it was easy to install Ubuntu to the free space.

I realize my advice sounds a bit like jumping out of a perfectly good plane, but it worked for me.  If I bought another Acer with four primaries I'd do what the other guy did - wipe the drive and create the NTFS partition.

After burning the recovry DVD's of course :)

---

