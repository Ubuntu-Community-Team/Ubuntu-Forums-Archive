---
title: "how do I actually use Gparted???"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by RotorRick on 2011-04-19
I want to change the size of my Ubuntu partition, someone suggested Gparted which I then installed. I'm looking around the program though, and I have no clue about how to adjust the size...there's icons and pulldowns, but the closest was "create partition table" which claims it'll wipe out all info on my HD to do so (good thing it warned me!).

So how do I actually do this?

Thanks!:D

---

### Post by GWBouge on 2011-04-19
I might be wrong, but I'm not sure if you can change partition sizes with GParted while you're actually using the disk (at least, it won't let me, either).  Boot from a LiveCD and use GParted from there, and you should be able to Right-Click on the partition -> Resize/Move.  Also note, people recommend that if you're changing an NTFS partition to make room/take up the space left over, use the Windows tool to do that.

And, as always, **back up important data** before making changes to the filesystem!

---

### Post by Megaptera on 2011-04-19
Always backup your docs, photos etc to external media before changing partitions - just in case!

Guide to GParted with screenshots: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by ikt on 2011-04-19
> **GWBouge said:**
> I might be wrong, but I'm not sure if you can change partition sizes with GParted while you're actually using the disk (at least, it won't let me, either).  Boot from a LiveCD and use GParted from there, and you should be able to Right-Click on the partition -> Resize/Move.  Also note, people recommend that if you're changing an NTFS partition to make room/take up the space left over, use the Windows tool to do that.

And, as always, **back up important data** before making changes to the filesystem!

Indeed, you'll need to unmount the filesystem to resize it.

You'll need to learn a little about partitioning first, then Gparted will make complete sense.

Partitioning information: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Gparted guide: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Have fun, and yeah, backup backup backup (backup)

---

