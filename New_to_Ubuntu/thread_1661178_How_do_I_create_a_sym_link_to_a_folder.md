---
title: "How do I create a sym link to a folder?"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by gatorbrit on 2011-01-06
I have 2 hard disks.  Disk 1 has my home folder on it, disk two has my data and dropbox folder.

I'd like to create a symbolic link in the home folder to the dropbox folder.  I was trying this:

ln /media/Secondharddisk/Dropbox /home/myname/Dropbox

But not having much luck.  Any suggestions?

---

### Post by seawolf167 on 2011-01-06
Add a -s switch

```
ln **-s **/media/Secondharddisk/Dropbox /home/myname/Dropbox
```

---

### Post by sisco311 on 2011-01-06
By default, ln tries to create a hard link. You have to specify that you want a symlink.
```
ln -s -T /media/Secondharddisk/Dropbox /home/myname/Dropbox
```

---

### Post by gatorbrit on 2011-01-06
Thanks! That did it.

---

### Post by sisco311 on 2011-01-06
> **gatorbrit said:**
> Thanks! That did it.

Cool!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

