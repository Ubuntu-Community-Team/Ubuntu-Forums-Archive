---
title: "Having trouble installing Ubuntu"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Space-Wolf on 2010-10-15
This is extremely frustrating.  Basically I already have Windows 7 on the computer and I left 150 gigs of free space for Ubuntu.  I boot up the Ubuntu installer using USB and I try to use the partitioning tool to select the free space but it doesn't let me and when I click install it just says, "no root file system is defined".  This is such a step down from both Mint and older Ubuntu's where there was a simple option of "use largest continous free space".

---

### Post by Space-Wolf on 2010-10-15
Alright looks like I figured it out.  But it made me manually create swap unlike Mint, I have 2 gigs of RAM and I made a 4 gig swap partition, will that be enough?

---

### Post by jespdj on 2010-10-15
That's more than enough swap space.

---

### Post by cariboo on 2010-10-15
I saw somewhere in the documentation, that if you use suspend you should set swap to the same amount as ram plus 100Mb, so 4Gb isn't needed

---

### Post by thebarisaxkid on 2010-10-16
> **Space-Wolf said:**
> Alright looks like I figured it out.  But it made me manually create swap unlike Mint, I have 2 gigs of RAM and I made a 4 gig swap partition, will that be enough?

I have the same trouble.  What exactly did you do besides create the swap partition?

---

### Post by AndyM3 on 2010-10-16
> **thebarisaxkid said:**
> I have the same trouble.  What exactly did you do besides create the swap partition?

You probably need to create all partitions by yourself. I recommend you do so anyway to create a separate /home partition.
If you do, I'd say make a root (/) partition anywhere from 10 to 50 GB, a swap partition of 150% your RAM size (e.g. if you have 2GB RAM, create a 3GB swap) and fill the rest with the /home partition.
Hope this helps. :D

---

### Post by thebarisaxkid on 2010-10-16
I have a vista partition+ plus a dell utility partition.  This means in order to have / and /home seperate, (with swap is a primary) I would need to make an extended partition with these two partitions as logical, right? And I would install the OS in the '/' partition?

Also, what format do i use? (sorry, noob question)

---

