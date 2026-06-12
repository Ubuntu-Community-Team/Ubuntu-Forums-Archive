---
title: "Mounting individual directory from ntfs"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by WU8V on 2009-07-22
I have a dual boot system between Jaunty and XP. 

I have restored some of my old HD to the XP side (NTFS) but would like to access it on the Jaunty side.

I can mount the entire partition, but I would prefer to mount to just my DATA area on the NTFS side.

If this involves typing in the directory structure, what does Linux do with the multi word directories? (Like Documents and Settings)?

Is there a way to mount just the Data directory (and its subdirectories)?

I have looked through the man pages, but did not recognize in the mount command what I was trying to do.

Thanks and regards,
Kurt

---

### Post by roccivic on 2009-07-22
What difference does it make to you if a whole partition is mounted or just a directory?
As far as I know, you can't do what you want. However you can mount the whole partition somewhere and then soft-link to a certain directory in it. Check out:
```
man ln
```
and
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

