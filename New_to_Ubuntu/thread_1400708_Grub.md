---
title: "Grub"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by ezrayst on 2010-02-07
Help! This is very urgent! 

I dual-booted W7 and Ubuntu 9.10
However, there is an error which says something like "error and not genuine"
Then, I tried to solve the problem by reinstalling Ubuntu

I was silly and i delete the partition through W7 first and then this message comes up when I start my computer:

GRUB loading.
error: no such partition
grub rescue>

I would like to continue with W7 and if possible, re-dual-boot ubuntu...
someone please help me!

---

### Post by Techsnap on 2010-02-07
Boot from your Windows 7 disc, Select Repair, Click command line and enter the following commands:

```
bootrec.exe /fixboot
```

and 

```
bootrec.exe /fixmbr
```

Also you posted this in the wrong area of the forum, reported to be moved.

---

### Post by overdrank on 2010-02-07
Hi and welcome, Moved to Absolute Beginner Talk

---

