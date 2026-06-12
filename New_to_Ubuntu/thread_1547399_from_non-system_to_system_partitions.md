---
title: "from non-system to system partitions"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by mancocapa on 2010-08-06
does anyone here know how to move disk space from non-system partitions to system partitions?

I have absolutely no idea how to go about this

Help is appreciated thank you

I

---

### Post by S.R on 2010-08-06
Use GParted off the live CD. 

Be advised the loss of data is possible.

---

### Post by cody1233 on 2010-08-06
Or if you have an internet connection you can download gparted

loss of data is also possible...

---

### Post by Mark Phelps on 2010-08-07
> **mancocapa said:**
> does anyone here know how to move disk space from non-system partitions to system partitions? 

Using such terms leads me to suspect you're asking about MS Windows partitions.  If that is so, that is a different situation than if you're talking about Linux partitions.

The latter work find with GParted; the former, especially if they're Vista or Win7 OS partitions, have been shown to get corrupted using GParted. In these cases, use the builtin Disk Management utility to make partition changes.  There are also freeware MS Windows-oriented partitioning tools available.

---

