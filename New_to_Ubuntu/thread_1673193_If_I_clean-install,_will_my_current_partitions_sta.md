---
title: "If I clean-install, will my current partitions stay the same?"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by watchpocket on 2011-01-22
I've recently decided to forego upgrading from Karmic to Lucid via the Update Manager.

I'm going to avoid the headaches I think that will cause by doing a clean-install of Lucid (after backing-up everything as it is now in Karmic, and using the "my-packages" commands).

I currently have a 1,000 GB hard disk.  /dev/sda1 is 15 GB mounted at / .

/dev/sda2 is an 8 GB swap space, and /dev/sda3 is 977 GB and mounted at /home .

My question:  if I do a clean-install, will those partitions automatically stay as they are?

Or do I have to re-create and specify this stuff -- the size of each partition, which partitions are mounted where, etc.  If so, would GParted be the logical tool to use for this?

---

### Post by Quackers on 2011-01-22
If you use the same partitions with the same mount points you'll be fine. You may even be able to use the same /home partition that you already have. It may depend on compatibility between the old and new systems, but people do that all the time (just don't format the /home partition, but use /home as the mount point for the new install).

---

### Post by Gone fishing on 2011-01-22
You can keep all the old partitions - just select the right option (specify partitions manually) when it comes to partitioning - you will need to format the root partition (a tick box I think) and don't format the /home partition.

Why the 8GB swap?

---

### Post by watchpocket on 2011-01-31
> **Gone fishing said:**
> Why the 8GB swap?

Maybe ask over at the System 76 forum?

Their "Wild Dog Performance" desktop machine came that way. 

Is there something odd about that?

 Is this considered way more that one would ordinarily need?

---

### Post by JKyleOKC on 2011-01-31
The 8 GB swap is because you have 8 GB of RAM; to hibernate, the system copies all of RAM to the swap area. If you never hibernate, the swap partition's size can be drastically reduced, since with so much RAM swap will probably never come into play...

---

