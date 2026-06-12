---
title: "GParted Help"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-07-31
Hey guys,

I'm wanting to get root access to use GParted to create a new partition on my external hard drive. When I run GParted, the partition options aren't highlighted for me. And when I run GParted from Terminal, I get this message:

*Since GParted is a powerful tool capable of destroying partition tables and vast amounts of data, only root may run it.*

I've been searching and searching on this, but cannot find a solution that works for me. So if anyone knows how I can give GParted root access, or how I can get root access, then I would really appreciate the help.

Thanks.

---

### Post by SuperSonic4 on 2009-07-31
gksu launches GUI apps as root

```
gksu gparted
```

---

### Post by TeoBigusGeekus on 2009-07-31
```
gksudo gparted
```
type password, press enter, done!

---

### Post by h8uthemost on 2009-07-31
Thank you guys, but the partition options are still not available to me in GParted. I typed in gksudo gparted, then when it asked my pass I gave it. But when GParted popped up, I selected my external, hit the Partition tab, but still the only three options that are available are:

Unmount
Manage Flags
Information

Anyone happen to know why this is?  Thanks.

---

### Post by TeoBigusGeekus on 2009-07-31
Try to unmount it first. You can't do any changes on it if it's mounted.

---

### Post by credobyte on 2009-07-31
You can't touch mounted partitions - the best option would be to boot from your Live CD and do all the stuff from there.
Also, gparted is available from [COLOR=Gray]System / Administration / Partition Editor[/COLOR] ( no need to use terminal and gksudo ).

---

### Post by h8uthemost on 2009-07-31
Unmnounting it certainly is what the problem was. Thank you guys. I appreciate the help.

---

