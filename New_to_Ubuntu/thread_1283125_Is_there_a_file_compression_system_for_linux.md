---
title: "Is there a file compression system for linux?"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by hopelessone on 2009-10-05
Hi,

I want to store files of approx size: 10~20Gig on a hard disk with no operating system on it only large files..

I remember in the old days you could compress a HDD in FAT to double it's capacity...

Does linux have a compression file system?

i.e double 1TB to 2TB...

Thanks,

---

### Post by 3rdalbum on 2009-10-05
SquashFS. I can't remember how to create a SquashFS image, so you'll have to look it up.

Some sorts of files will not compress very well. Back in the old days nobody ever had audio, video, or well-compressed image files on their hard disks; with plain text you can achieve good compression gains, but today's already-compressed content doesn't compress down at all. If you've got multi-gigabyte files, then chances are that they are the types of files that can't be further compressed.

---

### Post by mikeyphi on 2009-10-05
Have a look at fusecompress - available through synaptic

---

### Post by freak42 on 2009-10-05
> **hopelessone said:**
> 

I remember in the old days you could compress a HDD in FAT to double it's capacity...


Sorry for my useless post. But it is impossible to generally double a HD's capacity (after all you could then add another layer of double compression in your compressed FS, then you'd have quadruple capacity and so on, it'd be a perpetuum mobile of the information type)


sorry again (see [this]("http://xkcd.com/386/"))

---

