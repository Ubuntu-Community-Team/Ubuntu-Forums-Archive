---
title: "Decreasing size of an extended partition"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Wrathe on 2010-03-06
Hey,

I reduced the size of my /home partition in the extended partition, but now how do I reduce the size of the extended partition?  

The unallocation space is still 'inside' the extended partition and I want to add it to a partition outside the extended partition.  It won't let me reduce the extended partition in GParted.

Thanks

---

### Post by oldfred on 2010-03-06
Is swap inside the extended? If so gparted has probably mounted it. Use swapoff on the swap partition to unmount it. If any part of the extended is mounted the whole thing is and cannot be edited.

---

