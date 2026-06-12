---
title: "Need help with some simple partitioning"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by ttimm68 on 2011-01-02
I am dual booting Windows Vista and The newest version of Ubuntu. I have been using Ubuntu for a few weeks and I wanted to add some unallocated space to my Ubuntu partition. I was messing around in gparted on my ubuntu live cd and I added the unallocated space to the "extended" partition. I want that space (which is about 9.5 GB) to be in my ubuntu partition. I will attach a screenshot which I hope will allow you to help me better.

---

### Post by marrabld on 2011-01-02
I think you problem is that you need it to be contiguous space.

I believe you need to delete your swap space, then you 9Gb partition.  resize the one you wan't but leave enough for your swap.  then you create the swap in the area that is left.  

Make sure you make you swap file as big as your RAM if you wan't hibernation to work (if you can get it to work)

---

### Post by ttimm68 on 2011-01-03
Thanks

---

### Post by Bucky Ball on 2011-01-03
Whoa. Hold it. Well, you have some major issues in that case because you need free space beside your Ubuntu partition but deleting /swap is not going to do much.

You cannot shift the entire extended partition and the partitions in it and you can have no more than four partitions on a disk (up to 99 in an extended partition though, that's why we have them). 

So, I hope you are seeing what I am say. To put free space next to your Ubuntu partition for it to 'Expand partition' into, you are going to have to delete extended partition and partitions in it.

In other words:

Get rid of extended partition and everything in it;
Expand the Ubuntu partition as much as you like;
Add an extended partition and /swap.

---

### Post by ttimm68 on 2011-01-03
> **Bucky Ball said:**
> Whoa. Hold it. Well, you have some major issues in that case because you need free space beside your Ubuntu partition but deleting /swap is not going to do much.

You cannot shift the entire extended partition and the partitions in it and you can have no more than four partitions on a disk (up to 99 in an extended partition though, that's why we have them). 

So, I hope you are seeing what I am say. To put free space next to your Ubuntu partition for it to 'Expand partition' into, you are going to have to delete extended partition and partitions in it.

In other words:

Get rid of extended partition and everything in it;
Expand the Ubuntu partition as much as you like;
Add an extended partition and /swap.

What I did was delete all partitions below (or to he right of) Ubuntu and then added the space to Ubuntu and made a 2 Gig swap. What I didn't do is create an extended partition, do I need that? The machine seems to be working fine.

---

### Post by Bucky Ball on 2011-01-03
No, you don't need an extended partition. BUT, as I mentioned, the partition limit on any one physical drive is four (so if you wanted to add another partition you would need to delete one and make an extended to put your fifth partition in (hope that makes sense!). 

What I omitted to mention (sorry) is that a /home partition is always wise. In the rare circumstance you need to re-install the OS, you don't have to then back up everything from the / partition (which in your case now contains your /home also. 

Wise but not essential. You are looking good to go. ;)

---

