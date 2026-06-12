---
title: "Need assistance merging partitions"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Nato99 on 2009-01-18
I initially set up my laptop as a dual boot but soon realized that there was no need for Windows and would like to take the hard disk space used but Windows and make it available to Ubuntu. I've tried doing this with Gnome Partition Editor with no luck. The space used by Windows shows up as a separate hard drive that I can't access.

Here's a screen shot of what I'm getting

---

### Post by Moop on 2009-01-18
You can't do it while the hdd is mounted so you will need to use a live cd of Ubuntu or Gparted.

---

### Post by mrbiggbrain on 2009-01-18
so is this after your attempted merge...i see that the once was linux windows disk, now is ext3,

what are u trying to do exactly?

im sure if you had windows you had a NTFS drive, you must have taken that to EXT3?

you have an exstended partion, and you can not treat it as a regualr one, if you want to use the freespace from removeing an exstended partiiton you need to delete, or resize it.

---

### Post by Nato99 on 2009-01-18
> You can't do it while the hdd is mounted so you will need to use a live cd of Ubuntu or Gparted.

That makes sense! I'll give it a try
Thanks

---

### Post by b4b4_j4g4 on 2009-01-18
> The space used by Windows shows up as a separate hard drive that I can't access.

Hmm. I assume you don't have 2 hard disks in your box,
Looking at the screenshot you posted, I also assume that /dev/hda2 was originally your win partition.

Maybe you wanted to do this:
1.
```
sudo umount /media/windows
```
2.
Using gparted erase /dev/hda2
3.
Using gparted resize /dev/hda1 and /dev/hda6 (just move the border of the partition to the left)

---

