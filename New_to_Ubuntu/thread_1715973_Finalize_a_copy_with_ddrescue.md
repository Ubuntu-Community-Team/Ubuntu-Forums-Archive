---
title: "Finalize a copy with ddrescue"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by yo252yo on 2011-03-27
Hey
My external hard drive has fallen on the floor and since then crashes when I try to open some files. Therefore I bought a 1To harddrive to copy what could be saved of the 1To harddrive with ddrescue. At the end of the
sudo ddrescue -B -n /dev/sdc /dev/sdb rescued.log
process, I discovered that the old hard drive is actually bigger by 2Mo, which causes ddrescue to run out of space (even though there was lot of empty space on it). The logfile looks like this :
# Rescue Logfile. Created by GNU ddrescue version 1.11
# current_pos  current_status
0xE8E0AF0400     ?
#      pos        size  status
0x00000000  0xE8E0AF0400  +
0xE8E0AF0400  0x002C5C00  ?
which suggest that the copy went great. But now the copy is not finalized : the new hard drive doesn't appear in the explorer, it looks unpartitionned in gparted... Is there any way I could finalize the copy and get away with what I was able to copy ? It took days :s
Thank you in advance

---

### Post by yo252yo on 2011-03-27
Hey, a little update :  it seems that ddrescue copied the partition table of the old disc, creating a partition on the new disc bigger than the disc itself. I tried to change the partition table with fdisk but it doesnt work. ntfsfix and fsck doesn't seem to be working either.

---

### Post by Hedgehog1 on 2011-03-28
I dug through my ddrescue documentation when you first posted, and I could not find a way to copy to a smaller drive or 'finalize' either.

Fixing the partition map to match the (slightly) smaller drive is possible.  If you change your desorption of the thread to something like 'Partition Map on Rescue Drive is wrong' you might attract the folks who know that stuff.



***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-28
Actually - here is a possible solution for you:

> DiskInternals Partition Recovery is an advanced software tool, which is intended for all users, who need to recover some data or lost partitions. You deleted a file or your boot record, master boot record or partitions are damaged? You are at a loss for solutions here? This program will be a magic wand to make the whole situation go your way.

DiskInternals Partition Recovery is designed as a step-by-step wizard and requires no special skills to understand how it works.

...

You can download a full-featured trial version of DiskInternals Partition Recovery for free.

[**partition-recovery**]("http://www.diskinternals.com/partition-recovery/")

It is Windows software - but I have a feeling that is not an issue for you. :D

***The Hedge***

:KS

---

### Post by yo252yo on 2011-03-31
Hey
Thank you for your help and sorry about the delay. The software you advized me seems pretty good (but I guess I'll have to find a way around the fact that you cannot actualy save file without paying), but I'm missing another harddrive to copy all those things on, unless I erase the new one, which seems a shame considering it already has all the date. I've tried to run testdisk, which also tells me that the hard drive is too small for the partition :s

---

