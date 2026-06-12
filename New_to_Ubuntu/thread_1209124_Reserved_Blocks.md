---
title: "Reserved Blocks"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by neverett on 2009-07-09
I was wondering if it would be safe to resize my /home partition.  I have 891.3 GiB total for my /home partition.  I have 891.1 GiB free but only 845.8 GiB available.  I'm assuming this is because a percentage is reserved to prevent you from filling the partition too full.  Is there any way I can change the percentage of space to be blocked off?  Any help is appreciated.

/ = 19.7 GiB ext3
/home = 891.3 GiB ext3

Running 9.04 also.

---

### Post by kidders on 2009-07-11
Hi there,

The unavailable disk space is around the 5% mark, which is the default reserved block percentage for Ext3. Reserving disk space in /home is pointless, because most systems won't use it ... even if all your filesystems are full.

You can use tune2fs to change the reserved block count.

I hope that helps.

**Edit:**
Sorry ... I forgot to answer your question about resizing your /home filesystem. That's not something I would recommend without backing everything (ie not just /home) up first.

---

