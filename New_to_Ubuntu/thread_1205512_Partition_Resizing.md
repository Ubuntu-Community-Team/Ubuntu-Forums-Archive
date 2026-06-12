---
title: "Partition Resizing"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by riph72 on 2009-07-06
Hello all,
 
Suppose I have a HDD with Windows installed (single partition, using 100% of HDD), using 25% of partition space, but the files are scattered over the first 75% of the HDD.  Assume that all files are defrag'd.
 
During the Ubuntu install, if I request that Ubuntu uses the upper 50% of the HDD, is the partition tool capable of moving files in the 50%-75% "area" to the 0%-50% "area", or would they just be lost?
 
I'm also wondering what the answer would be when using the Partition Editor (I think that's what it's called) following installation?
 
Regards,
Richard.

---

### Post by diablo75 on 2009-07-06
Ubuntu will remove all the data that's in the way over to the free space areas of the first partition to make space for the new ext3/4 and swap partitions needed for Linux.  Just do a guided resize, tell it how much space you want to use up from the Windows NTFS partition, and that's it.  You won't lose your data.

---

### Post by Zack McCool on 2009-07-06
No.  The partitioner will only shrink down a partition's contiguous free space at the end of the partition.  If there are files there, it will not do it.

You need to follow a few steps in Windows before undergoing this process.  First, turn off the swap file (if at all possible), then disable system restore (temporarily, turn both back on later), the defrag your disk's free space.  Once this is done, shut down, and boot to the LiveCD and tell it to resize the partition.  It will not delete files, and it also doesn't move any.  Once this is done, you can go ahead and install Ubuntu, and you'll have a dual-boot.

Now you can log back into Windows, turn System Restore and swap back on, and then never use Windows again...   ;)

---

### Post by zeroseven0183 on 2009-07-06
> **Zack McCool said:**
> and then never use Windows again... ;)
 
... which can solve a lot of problems.
 
Cool!

---

### Post by diablo75 on 2009-07-06
> **Zack McCool said:**
> No.  The partitioner will only shrink down a partition's contiguous free space at the end of the partition.  If there are files there, it will not do it.

You need to follow a few steps in Windows before undergoing this process.  First, turn off the swap file (if at all possible), then disable system restore (temporarily, turn both back on later), the defrag your disk's free space.  Once this is done, shut down, and boot to the LiveCD and tell it to resize the partition.  It will not delete files, and it also doesn't move any.  Once this is done, you can go ahead and install Ubuntu, and you'll have a dual-boot.

Now you can log back into Windows, turn System Restore and swap back on, and then never use Windows again...   ;)

I've never had to do this and know for a fact that the partition WILL move data if it needs to.  

A hard drive is made up of thousands of sectors, each one sort of like a page in a book.  Like a book, each page is numbered, but unlike most books, the beginning and ending of each page points to other pages, so it knows what sectors lead to what other sectors in order to reconstruct large files that require multiple sectors.  If these markers didn't exist, check-disk programs that fix errors would have a hard time putting things back together if data were corrupted due to an abrupt interruption while writing or moving data around.  So to resize or shrink a partition down that has data scattered about, it just moves pages near the end of the book more towards the beginning where there is no data being stored, and updates all the pointers at the beginning and ends.  This goes a lot faster when things are defragged and files are contiguous across several pages instead of scattered about randomly.

If you've defragged the drive that should be enough prep work you need to do before shrinking a partition down.  Disabling the swap is not necessary either; it's just a file on the hard drive like any other file.  And I **wouldn't** disable system restore either because it would probably purge your previous restore data.  Just defrag, and then install.  You'll be fine.

---

### Post by riph72 on 2009-07-06
Thanks for the replies, so I'll not risk losing data then... (or didn't risk losing it, more accurately)
 
Does this apply to using Ubuntu's Partition Editor also, i.e. the one available via Administration panel (not installed by default though)?
 
Regards,
Richard.

---

### Post by diablo75 on 2009-07-06
> **Zack McCool said:**
> It will not delete files, and it also doesn't move any.

Just to clarify, he is right, but only if you select "Use largest contiguous free space".  There is another option just above this one that will let you set the size of the partitions to what ever you want.

---

### Post by diablo75 on 2009-07-06
> **riph72 said:**
> Thanks for the replies, so I'll not risk losing data then... (or didn't risk losing it, more accurately)
 
Does this apply to using Ubuntu's Partition Editor also, i.e. the one available via Administration panel (not installed by default though)?
 
Regards,
Richard.

It's not the best (or rather, not the most feature rich).  Download a [gParted]("http://gparted.sourceforge.net/") iso file and burn it to CD, then boot from it to get your fingers dirty.  It's an easy to use and powerful partition editor.

---

### Post by riph72 on 2009-07-06
> **diablo75 said:**
> Just defrag, and then install. You'll be fine.
 That's exactly what I did actually.  I know there were no files in the upper 20% of my HDD (i.e. the Ubuntu partitions-to be) following the defrag, although I can't say for sure that Windows didn't put a file back there between shutting down Defrag and shutting down Windows.
 
It sounds from all the responses that I was ok though  :)

---

### Post by Cheesemill on 2009-07-06
> **diablo75 said:**
> It's not the best (or rather, not the most feature rich).

Really? Ubuntu uses gparted as it's partition editor.

---

### Post by diablo75 on 2009-07-06
> **Cheesemill said:**
> Really? Ubuntu uses gparted as it's partition editor.

Right but there are features left out, or inaccessible because the system is running while you're using it.  For example, you couldn't resize the root partition while the system was running.  I've also noticed other features and partition types (for creation) grayed out and unavailable under a running environment.  So I'm just saying that what you get in Ubuntu is more like a Lite version of gParted, and if you want the whole shebang to use a Live CD instead.  Just what I've experienced/witnessed...

---

### Post by frunns on 2009-07-06
Uuuh... It's not a "Lite" version? It's just GParted on a running system?

---

### Post by carml on 2009-07-06
There's also a full release of Gparted: the Gparted Live CD,which can be used like Gparted when called from a Live cd of Ubuntu.

---

### Post by frunns on 2009-07-06
> **carml said:**
> There's also a full release of Gparted: the Gparted Live CD,which can be used like Gparted when called from a Live cd of Ubuntu.

Well, yeah. But GParted is still GParted, nothing "lite" about it.

---

