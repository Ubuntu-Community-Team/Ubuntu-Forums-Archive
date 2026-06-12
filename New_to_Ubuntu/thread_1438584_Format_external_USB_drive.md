---
title: "Format external USB drive"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by NutmegCT on 2010-03-25
Good morning all.

I have a USB 320G external drive, currently set up on a WinXP machine as 3 partitions:

1.  NTFS 154G
2.  NTFS  156G
3.  NTFS  18G

I want to delete the data in each partition.  In my DOS and Windows days, the choice was Format.

I open Palimpsest, see all my logical and physical drives, unmount them, choose the external drive and see on the right:

320GB Hard Disk

I choose the first partition and see on the right:

Partition:  The attributes of the partition can be edited or deleted ...  Partition Label (blank), Type (HPFS,NTFS, with lots of other choices in the menu), bootable, and a Delete button.

But I see no "format" button or choice.  Palimpsest is described in many posts and websites as being used to Format a drive (among many other uses).  But I find no "format" anywhere in the app.

Could someone please tell me how to accomplish my task?  I don't want to choose Delete, as (I assume) I'm deleting the partition, not just the data.  Back in the old DOS days, you choose the Partition (the drive), then Format (or Quick Format).

Thanks.
Tom
Ubuntu 9.1 updated this morning.

---

### Post by byStanderone on 2010-03-25
...check if ntfsprogs is installed in your system, if not do install it. am using gparted when it comes to drives, you can install it, too, thru synaptic manager.

---

### Post by NutmegCT on 2010-03-25
> **byStanderone said:**
> ...check if ntfsprogs is installed in your system, if not do install it. am using gparted when it comes to drives, you can install it, too, thru synaptic manager.

Thanks Standerone.  I'd be happy to get ntfsprogs, but how do I get Palimpsest to format the drive?

Thanks.
Tom

---

### Post by byStanderone on 2010-03-25
...sorry bout palimsest, am not using it.

---

### Post by NutmegCT on 2010-03-25
OK - it wasn't quite as user friendly as I hoped, but I figured it out.  In Palimpsest, you choose the drive, then choose Delete.  When the drive is deleted, you can then choose it and Create, and choose the file system you want, and the size you want.

Interesting aspect of Palimpsest is that when you Create and Format, the window closes immediately, even tho' the action is still proceeding.  If you try to access the drive before the format has finished (even tho' you don't know it hasn't finished), you get several types of errors.

Anyway - SOLVED!
Thanks.
Tom

---

