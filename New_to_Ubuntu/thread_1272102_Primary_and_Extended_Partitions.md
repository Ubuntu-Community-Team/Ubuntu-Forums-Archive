---
title: "Primary and Extended Partitions"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-09-21
I'm going to install Kubuntu (9.04) on my laptop, which currently has:
Recovery partition - 9.77GB
Vista - 59.00GB
Free space - 164.12GB


I want to have a swap partition and a separate home partition - something like:
Recovery partition - 9.77GB
Vista - 59.00GB
Swap - 4GB
/ - 10GB
/home - (the rest)

I've read that a hard disk can have only 4 primary partitions, so I'll need to make one extended partition.  Should I have swap and root in the same primary partition, or swap and home, or root and home, or doesn't it really matter?

---

### Post by wojox on 2009-09-21
Swap and root. Then if you run into troubles home is alone.

---

### Post by EssexEagle on 2009-09-22
> **wojox said:**
> Swap and root. Then if you run into troubles home is alone.

Thanks very much :)

---

