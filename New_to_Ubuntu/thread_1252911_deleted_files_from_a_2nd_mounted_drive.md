---
title: "deleted files from a 2nd mounted drive"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by airliner_737 on 2009-08-29
I deleted some images from my 2ndary hard drive in error today and I am trying to salvage them.  Is there a way to get them back?  I looked in the trash... seems it only keeps the files deleted from the primary drive?  Or is it size dependent?

---

### Post by Liolikas on 2009-08-29
Check freespace with:
df -h
If second drive have more freespace than normal means files gone. Restore possible but depends of disk format how to do it. If still no freespace then:
ls -a /second/drive
And you may see folder like .trash and cd into it and you may see your files with ls.

---

### Post by ayenack on 2009-08-29
This may help.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Despite its name it doesn't only recover photos it recovers all sorts of files. Might be in the repo's but not sure.

---

### Post by ayenack on 2009-08-29
confusingly you can install PhotRec by installing TestDisk like this. They come together apparently.

**sudo apt-get install testdisk**

Then typing **sudo photorec** at the command line.

You get the advantage of having TestDisk installed also which is used to recover/repair broken partitions/drives etc. I use it it's very good. If you ever need to use TestDisk type **sudo testdisk** at the command line.

BTW. You need to use sudo or be root to run TestDisk/PhotoRec.

---

