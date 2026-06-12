---
title: "Partioning with gparted"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Sam3280 on 2009-02-05
Hi,
I'm trying to partition a portable hard drive for a family friend. How do i start with gparted?
Thanks

---

### Post by iaculallad on 2009-02-05
> **Sam3280 said:**
> Hi,
I'm trying to partition a portable hard drive for a family friend. How do i start with gparted?
Thanks

Navigate through System->Administration->Partition Editor, running GParted would require you to input your privileged password.

---

### Post by Sam3280 on 2009-02-05
Sorry should have been more clear I want to know how to actually partition

---

### Post by mikeize on 2009-02-05
Find the disk you want to partition in gparted.  Should be pretty clear from the size of the disk.  Unmount it (partition>unmount).  Then right-click on it, and select Resize/move.  Set the size of one partition, then similarly, "create new" partition in the empty space.  You can also easily format these partitions to whatever file system you like.  After you have made all the changes, apply them.  If it is a big disk, it may take some time to finish.

---

### Post by Elfy on 2009-02-05
There's a lot of simply written documentation there and pictures on the gparted docs - [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

