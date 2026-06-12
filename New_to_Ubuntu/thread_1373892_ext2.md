---
title: "ext2"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Drenriza on 2010-01-06
Is their anyone that know where you can read about the features in ext2 and ext3?

i have searched on google, and i dont know if its just me but i cant find any talk about features.

thanks on advance:KS

---

### Post by Nuzgal on 2010-01-06
[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by Drenriza on 2010-01-06
I also been on wikipedia but it doesn't say much about the features.

Like i saw elsewhere that ext2 can read windows material, stuff like that.

---

### Post by 3rdalbum on 2010-01-06
> **Drenriza said:**
> I also been on wikipedia but it doesn't say much about the features.

Like i saw elsewhere that ext2 can read windows material, stuff like that.

No - a filesystem is just an arrangement of files on a disk. Ext2 can't read Windows disks any more than the English language is a good story :-)

What I think you might have read is that there is an Ext2 driver for Windows, so you can use Ext2/3-formatted drives on Windows.

Both Linux and Windows can read and write Fat32 and NTFS, which are the two main Windows filesystem formats.

Don't bother using Ext2. Use Ext3 or Ext4; the former is backwards-compatible with the Ext2 Windows driver anyway.

---

