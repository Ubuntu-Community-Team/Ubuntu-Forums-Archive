---
title: "Can't delete partitions?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-06-24
I'm on a Live CD and want to delete all partitions, and then re create them to re install on this computer.  But I still have 2 partitions that won't let me delete...  /dev/sda2 and unallocated.  Please help?

---

### Post by Paqman on 2010-06-24
The LiveCD automatically mounts any swap partitions it finds to improve performance. In doing so it locks that swap and any extended partitions surrounding it from being modified by Gparted.

Simple solution: right click on swap > "swapoff" > job done!

---

### Post by anewguy on 2010-06-24
And...unallocated isn't really a partition - it's telling you this space on the drive is not allocated to any partition.

Dave ;)

---

### Post by elliotn on 2010-06-24
Unmount the drive first

---

### Post by TriBlox6432 on 2010-06-24
Thanks guys.  But it's not swap.  It's an extended partition...

---

### Post by TriBlox6432 on 2010-06-24
How do I unmount it?

---

### Post by TriBlox6432 on 2010-06-24
Nevermind.  I figured it out.

---

