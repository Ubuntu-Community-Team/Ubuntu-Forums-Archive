---
title: "Swap - is there a best location?  Best size?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by cwmoser on 2010-05-28
I have 64-bit Ubuntu 9.04 Jaunty and 6GB RAM.

I use Clonezilla and Gparted for hard disk cloning and Partition editing.  Last night I increased the size of my /swap parition (/dev/sd2) to 8GB and moved it to the end of the Hard Drive.

My Hard Drive is 500GB and I like to leave unpartitioned space for upgrades, testing, etc.  I also shrunk my root / partition to 30GB - and still only using 7GB.

So, is there a better place to put /swap than at the end of the hard drive or is this as good as any?

How about my swap size -- now 8GB?

Carl

---

### Post by SlidingHorn on 2010-05-28
I'm no expert in this area, but I don't believe it's much of an issue where the swap partition is placed.  8GB should be more than you'll ever need

---

### Post by germanix on 2010-05-28
The rule of thumb is to have your swap twice the size of your Ram. So if you have 4GB ram you will need 8GB for Swap. I was originally told that Swap should be at the end, but lately I have read that it is better at the front. I think it probably does not make any big difference in the end but I assume placing it at the front will be better if you want to make your home partition smaller in the future then the Swap will not be in your way.

---

### Post by uRock on 2010-05-28
Unless you are doing some super sized work on your system I don't see the need for a huge swap partition. I very rarely use swap for anything. Even when I am running a VirtualBox I still do not go into swap. I have 2GB RAM and 2GB swap.

I have read that swap is faster when it is at the front of the hard drive, but I have had mine in the front, back and now in the middle and I haven't seen any difference in the few times I have actually used that much memory.

---

### Post by philinux on 2010-05-28
The old rule of thumb was for the days when ram was expensive.

If you have 6 gig of ram then the most swap you would need is 6 gig. This is for hibernating etc. assuming at the time of hibernate most of the ram is in use, doubtful I suspect. 
If you don't hibernate then less would suffice. In fact if you never hibernate or suspend then with 6 gig of ram you dont need any swap.
[https://help.ubuntu.com/community/SwapFaq#How much swap do I need?](https://help.ubuntu.com/community/SwapFaq#How much swap do I need?)

---

### Post by HermanAB on 2010-05-28
Howdy,

You need /swap to be twice the size of the RAM if you want to use Suspend and Hibernate.

---

### Post by philinux on 2010-05-28
> **HermanAB said:**
> Howdy,

You need /swap to be twice the size of the RAM if you want to use Suspend and Hibernate.

Please see the link in post #6. ;)

---

### Post by Ozymandias_117 on 2010-05-28
I think the only thing that would effect how fast your swap is   would be to put it on a separate hard drive.

---

### Post by kansasnoob on 2010-05-28
> **philinux said:**
> The old rule of thumb was for the days when ram was expensive.

If you have 6 gig of ram then the most swap you would need is 6 gig. This is for hibernating etc. assuming at the time of hibernate most of the ram is in use, doubtful I suspect. 
If you don't hibernate then less would suffice. In fact if you never hibernate or suspend then with 6 gig of ram you dont need any swap.
[https://help.ubuntu.com/community/SwapFaq#How much swap do I need?](https://help.ubuntu.com/community/SwapFaq#How much swap do I need?)

+1! My basic rule is, up to 2GB of RAM I double that for SWAP size, anything over 2GB I create the SWAP just slightly over the amount of RAM, eg: RAM=6GB / make SWAP=6.1GB.

I generally partition with 2 or 3 primary partitions at the beginning of the disc, then one extended partition w/SWAP at the very end:

[ATTACH]158566[/ATTACH]

Some other great ideas and scenarios:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

The reason I like to have SWAP at the very end of the extended partition is that resizing or moving SWAP will usually change it's UUID which plunges you into UUID hell! You may find that SWAP no longer "mounts" at startup and you have to jump through these hoops:

[ATTACH]158565[/ATTACH]

---

### Post by Penguin Guy on 2010-05-28
I've never seen Linux run out of RAM and I don't use hibernation, so I have no swap partition.

---

### Post by -humanaut- on 2010-05-28
I generally keep my swap (5GB excessive amount of space sure but if you end up in swap hell you'll be damn glad you have it) as the first extended partition after my /(boot) and /(root) on older computers I always keep it near the front generally directly after boot so it can be accessed as quickly as possible.

---

