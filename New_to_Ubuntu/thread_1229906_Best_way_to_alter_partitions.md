---
title: "Best way to alter partitions"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by mesmith on 2009-08-02
My hard disk consists of two partitions, a primary linux and a primary swap.  I want to delete the primary swap and in its place install a logical swap area.  What is the best way to go about this using the partition editor?

Thanks.

---

### Post by ajgreeny on 2009-08-02
Normally you would need to use gparted from a live CD. delete the primary swap and then make a new extended partition in its place and then make a new logical partition in the extended one, format it as swap and then in your install edit /etc/fstab to take account of the new UUID that will have been given to the new partition.

You may be able to do it from within ubuntu if you have gparted installed by right clicking on the swap partition and choosing swapoff, then unmount, if needed, then do everything I said above, but the live CD is probably safest.

However, why do you want to do this at all?  I don't see any real advantage to it unless you have lots of space available and intend to add other partitions to the extended partition you make.

If it ain't broke, don't fix it!

---

### Post by mesmith on 2009-08-02
Good advice.  It ain't broke.

Thanks.

---

