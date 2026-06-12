---
title: "Ned info about how to clone a HD"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by s1baker on 2011-03-30
Hi,
I have Ubuntu 10.10 ( 32 bit ) on a 30 Gig Hard drive, and now i have only a few gigs of space left. I bought another 160 Gig HD and I want to clone the 30 Gig over to the 160 Gig HD. I have some questions about cloning.

1) Should I use clonezilla for this?
2) here are some things I have on my 30 Gig hard drive, and I am wondering if they will be cloned along with the Ubuntu OS:
.   a) VirtualBox ( by Oracle )
.   b) Wine  ( has several Windows XP programs in it )
.   c) DOS emulator ( called 'dosemu', has some old DOS programs in it ) 

  Will clonezilla clone all of these things also?

3) if I do a disk to disk clone from the 30 gig to the 160 gig hard drive, will I need to do any thing extra for the Ubuntu OS to recognise the full 160 Gig space, or will it automatically know to expand my partition sizes to get the full 160 gigs?

thanks

---

### Post by rbc on 2011-03-30
First of all, get the most recent version of Clonezilla. The older versions, in my experience, didn’t like grub2. Yes, Clonezilla will copy over all the applications. It will not expand the partition for you. You’re going to end up with a 30 GB partition on the 160 GB drive, with remaining free space. Just boot any Live CD and use GParted to expand the partition.
Or
Boot a Live CD and use dd command, instead of Clonezilla. Shout if you want to go that route and need help

---

### Post by Jerry N on 2011-03-30
I've used Clonezilla a couple of times to clone a Windows install to a bigger drive.  It worked perfectly.  The last one was on an HP laptop (an older one with XP and 3 partitions) to move from an 80gb drive to a 320gb drive so I would have room to install Ubuntu 10.04.

Jerry

---

### Post by s1baker on 2011-03-30
Is the 'live Cd' the cd I used to install Ubuntu 10.10 to the HD originally? and is gparted used after the clone is done to expand the cloned size from 30 gigs to 160?

---

### Post by rbc on 2011-03-30
Yes, and yes

---

