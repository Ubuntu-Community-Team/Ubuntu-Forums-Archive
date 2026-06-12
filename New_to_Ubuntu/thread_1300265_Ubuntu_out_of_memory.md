---
title: "Ubuntu out of memory?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by halo45121 on 2009-10-24
Uhh... Not too sure what's up. I have Vista and Ubuntu. Whenever I try to do really anything on Ubuntu, it tells me I don't have enough memory. (My hard drive is about half full.)
I have a six gigabyte partition of unallocated memory sitting around doing nothing.
How would I add that memory to Ubuntu so I can update and get apps and all that fun stuff again? Thanks!

---

### Post by 3rdalbum on 2009-10-24
"Memory" refers to the computer's temporary storage; what you're talking about is "disk space".

Boot up a live CD and take a look in System > Administration > Partition Editor. If the 6 gigabyte partition (or unallocated space) is adjacent to the Ubuntu partition, then you may be able to delete the partition and resize the Ubuntu partition upwards into the freed space.

---

