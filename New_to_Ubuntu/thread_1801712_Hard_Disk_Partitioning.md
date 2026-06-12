---
title: "Hard Disk Partitioning"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by NormArchNo3 on 2011-07-11
I'm having hard disk troubles. It seems that my hard disk was already partitioned. Since I'm using Wubi, it seems that Windows and Ubuntu can share a partition, so I'm trying to get expand my current partition to get more space, as I'm running out. I'm using the disk partitioner in Windows Control Panel. About 202 GB are labeled as 'free space.' I can't press the 'expand partition' button, as it is greyed out. Can anyone help?

Thanks!

---

### Post by Neoncamouflage on 2011-07-11
Not sure how to do it in Windows, but I had free space on mine as well. Boot up an Ubuntu LiveCD, run from the CD, do not install, and run GParted. Just reformat the free space to NTFS, I believe that's what it's called, something similar if not that. And then merge your windows partition with it.

---

### Post by wildmanne39 on 2011-07-11
> **NormArchNo3 said:**
> I'm having hard disk troubles. It seems that my hard disk was already partitioned. Since I'm using Wubi, it seems that Windows and Ubuntu can share a partition, so I'm trying to get expand my current partition to get more space, as I'm running out. I'm using the disk partitioner in Windows Control Panel. About 202 GB are labeled as 'free space.' I can't press the 'expand partition' button, as it is greyed out. Can anyone help?

Thanks!Hi, here is a link that will help you resize your partition.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by Mark Phelps on 2011-07-11
If you're running Win7, and you have Wubi installed in the Win7 OS partition, do NOT, repeat NOT, use GParted to expand the Win7 OS partition.  Instead, use the Win7 Disk Management utility to do that.

If that does not work, then there is something else in play.  Maybe there is a Recovery partition blocking the expansion?

Look at all the "drives" in Win7 Disk Management to ensure there is not another partition in the way.

---

### Post by charliewhizbeez on 2011-07-11
> **Mark Phelps said:**
> If you're running Win7, and you have Wubi installed in the Win7 OS partition, do NOT, repeat NOT, use GParted to expand the Win7 OS partition.  Instead, use the Win7 Disk Management utility to do that.

If that does not work, then there is something else in play.  Maybe there is a Recovery partition blocking the expansion?

Look at all the "drives" in Win7 Disk Management to ensure there is not another partition in the way.

Yes.  Exactly.  Windows wants it done it's way.  Any other way makes windows cranky.

---

### Post by wildmanne39 on 2011-07-11
> **charliewhizbeez said:**
> Yes.  Exactly.  Windows wants it done it's way.  Any other way makes windows cranky.
Hi, did you try that link I gave you? it is for resizing wubi partitions.

---

