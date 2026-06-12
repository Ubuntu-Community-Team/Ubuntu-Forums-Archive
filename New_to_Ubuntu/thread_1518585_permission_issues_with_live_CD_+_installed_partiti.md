---
title: "permission issues with live CD + installed partition"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by tadcan on 2010-06-26
I made a mess of my partitions and want to reinstall ubuntu. My problem is that when I put in the live CD and navigate to my files I don't have permission to copy them to an external drive. 

What is the best way around this. Fix Grub so I can get in there. Use some command line kung-fu to change permissions. Something else.

---

### Post by nhasian on 2010-06-26
press alt-f2 and then enter:

```
gksu nautilus
```

that will let you copy files with super user privileges

---

### Post by tadcan on 2010-06-28
Thanks, that worked

---

