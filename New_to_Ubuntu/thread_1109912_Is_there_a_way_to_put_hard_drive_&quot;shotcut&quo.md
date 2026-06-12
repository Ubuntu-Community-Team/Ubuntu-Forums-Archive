---
title: "Is there a way to put hard drive &quot;shotcut&quot; on the desktop?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Friccy on 2009-03-29
Hi!
I have a problem with the Ubuntu 8.10.
Since I have upgraded to it, system is not starting till I keep pressing a key. OK, it will be solved in the next edition!
The hard drives are not accessible! Every time I boot my laptop and want to open a partition it say that it is not mounted. Why? At the second try it opens.
I want to make some "shortcuts" on the desktop for the 2 major partition, to make it accessible easier. How can I do it?

---

### Post by mvalviar on 2009-03-29
** erased ** I got the wrong idea. Sorry.

---

### Post by Elfy on 2009-03-29
Add them with fstab - create a directory in /media for each partition you want to mount

```
sudo mkdir /media/name1 /media/name2
```

Then add each partition to fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

