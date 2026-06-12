---
title: "GParted Leaves Unallocated Space"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by blendmaster on 2009-01-15
Hello!

I have an issue when trying to partition my drive with the GParted tool in Ubuntu (this actually occurs with all partitioning methods I've tried so far, so it's probably an issue with my drive).

When trying to partition a logical drive within my extended drive, it seems the partitioner wants to leave some unallocated space before the partition (I've attached an example of this). My question is why is this happening and what can I do to resolve it (I've looked for an answer, but I think it may be an MBR issue).

Thank you!

---

### Post by blendmaster on 2009-01-15
Any ideas?

---

### Post by b0b138 on 2009-01-15
Probably windows fault. I've never had a windows install partition out 100% of a drive. Of coarse, I'm assuming you did most or all of the partitioning from windows.

I would be more concerned with the 20 gig unknown partition and the 5 gig linux swap (WAY to big) than that 5 megs

ps, quick google and found a more technical answer

> During Setup, if you choose to create a partition that uses the remaining space on a disk, you cannot use the maximum space available on the disk.

For example, if you choose to create a 4096-MB partition on a disk that has only 4096 MB available, the actual partition that is created may be 4095 MB or less in size.

CAUSE
Some space at the end of the disk is reserved by Setup in case you later want to upgrade the disk to a dynamic disk. Dynamic disk information is saved at the end of the disk. The amount that is reserved is a minimum of one cylinder, or 1MB, whichever is greater. One cylinder can be up to 8MB, depending on drive geometry and translation.

---

### Post by Shazaam on 2009-01-15
A shot in the dark, a question, and a suggestion.
Shot in the dark-- Did you use Vista to make the partitions?
Question--What is the "Unknown" partition?
Suggestion-- Boot the Ubuntu livcd, start gparted, resize/move the swap partition to fill up the Unallocated space.

---

### Post by blendmaster on 2009-01-15
Thanks for the responses!

Yes, the Extended partition was made in Windows. Don't remember what else was done and what partitioner made the rest of my partitions (I've made a lot of partitions on this drive, most of which are deleted).

The Unknown partition is an OpenSolaris install (apparently GParted still doesn't recognize ZFS).

The 5 GB of Swap was to accommodate 4 GB of RAM. I'm not too understanding of the whole "How much Swap..." issue, but from what I've read, some suggest equal Swap to RAM, others suggest twice as much, and others suggest half as much. I heard the main use of the Swap is for waking up from sleep, but I digress on that. I just gave 5 GB so I could have partitions that were mostly factors of five.

I'll try the Swap fill idea... that may work.

Edit: Moving Swap to the left doesn't work. GParted moves it back during the operation. If I install Ubuntu with the installer, it deletes my Extended partition and places that Unallocated space before the Extended partition. The Logical partitions seem to then not have that trouble. The space is still there, which could be do to what b0b138 suggested. Maybe I'll have to live with the weird partition table.

---

### Post by b0b138 on 2009-01-15
You could try deleting the swap partition, and should then have the whole extended part unallocated. Or it might show 2 unallocated parts, which wouldnt suprise me.  As far as the swap size, 1 gig would be plenty unless you do things that actually use up your 4 gig of ram.

---

### Post by blendmaster on 2009-01-15
> **b0b138 said:**
> You could try deleting the swap partition, and should then have the whole extended part unallocated. Or it might show 2 unallocated parts, which wouldnt suprise me.  As far as the swap size, 1 gig would be plenty unless you do things that actually use up your 4 gig of ram.

Deleting it leaves the whole partition unallocated (as if it is fine). As soon as the first partition is created, the space comes back.

The most interesting thing that I can do is create the Swap I want to use (this problem occurs with any format); this then makes the Unallocated space before the partition. I can format this useless Unallocated partition as anything (say for example, Swap), and then there is no more Unallocated space. However, seeing as such a small Swap space is useless anyway, I try to delete (or move) the actual partition to the right. With it moved, I can try to resize the Swap up to 5 GB (which I may rethink the size once this is figured out). When the partition gets resized, the Unallocated space comes back and the mess starts back up all over again.

This all leads me to believe I've somehow corrupted my partition table. I'm thinking about just living with it, as it isn't too much useable space taken out.

---

