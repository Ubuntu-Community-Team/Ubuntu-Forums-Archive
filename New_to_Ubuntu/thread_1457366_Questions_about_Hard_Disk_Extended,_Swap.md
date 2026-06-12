---
title: "Questions about Hard Disk Extended, Swap"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by sheepdog9090 on 2010-04-18
Looking at my Hard disk through the Palimpset Disk Utility, I see several items.

 total disk space - 160GB
|
| 154GB File System
|
| 6.2 GB Extended
     |
     | 6.2 GB Swap Space


What is the difference between the Extended and the swap? Any help is appreciated.

---

### Post by WinterRain on 2010-04-18
Both 6.2gb partitions are actually 1 partition. A partition can have to labels. For more on partitions see [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by J V on 2010-04-18
The DOS partition (What almost every computer comes with) can only hold a maximum of 4 primary partitions. 

To get around this, some clever people made extended partitions: A primary partition capable of carrying several other partitions underneath it. Your swap is *inside* the extended partition.

Swap is linux virtual memory: It is used when your computer runs out of real memory.

Honestly, you shouldn't need 6.2 gigs of swap space.

I would suggest that on your next install, you give about 1 or 2 gigs to swap, and install everything inside an extended partition rather than one primary, those primaries are fairly valuable in terms of file system.

---

### Post by sheepdog9090 on 2010-04-18
Thank you for your help.

---

### Post by quadproc on 2010-04-18
> **J V said:**
> ...
Honestly, you shouldn't need 6.2 gigs of swap space.

If you are going to use suspend/hibernate then you need at least as much swap space as you have actual RAM in the system.  If you might increase the amount of RAM in the future then you can save yourself some future work by making the swap space bigger than your ultimate RAM size; then you won't have to undertake the relatively risky operation of resizing your swap partition when you add RAM.

Systems with 8 to 16 GB of RAM are not unusual these days.

quadproc

---

### Post by Paqman on 2010-04-18
6.2GB is a little excessive for swap space, btw. The only time you'd need that much is if you had 6GB of RAM and wanted to be able to hibernate.

---

### Post by Kellemora on 2010-04-19
I would go just the OPPOSITE of what was recommended above, and here's why!

Hard Drive space is CHEAP these days!
When I first started to learn to use Ubuntu, it seems I was steered in the wrong direction at nearly every turn I made, regarding how much space for this or that.

The only RIGHT thing I was told was to keep HOME on a separate partition.

I went through over 15 full installs before I ironed out all the wrinkles, or so I thought.

Come upgrade time and BANG, not enough space to upgrade!
And even setting my partitions to DOUBLE the highest recommended amount, when I went to upgrade to Lucid, BANG, not enough space to upgrade.

Although I can see from the monitor my Swap File has never been used, I still set it at 32 gigs, which is double the highest currently known amount of RAM!

On the old machines, my Boot partitions are all set to 10 gigs now.
And Program Areas I've upped to 50 gigs.
I can't get to my Lucid machine right now, but I believe it was set to 25 or 30 and didn't have enough room to upgrade.
I use a file server, but STILL keep HOME on it's own HUGE partition.

Ubuntu 8.04 LTS Hardy on the machine I'm looking at right now is taking up 10.70 gigs.  This machine was originally set to 10 gigs as being MORE THAN SUFFICIENT and I had to expand that partition.

So, with the Low Cost for Hard Drive space these days, don't cut corners!
It will only cause you more work later on!
No reason to have 400 gigs unallocated or set for use by Home, hi hi.......

TTUL
Gary

---

### Post by sheepdog9090 on 2010-04-19
When time to upgrade to the latest distro (April 29) will I need more space?

---

