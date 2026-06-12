---
title: "resizing /home question"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by eddski on 2009-04-23
I have /home on a logical partition, and have some room to the left of it. How would that work since info is stored beginning on the left of the partition? Would it be better if I resize, reformat and restore from backup?

---

### Post by unutbu on 2009-04-23
Make a backup, delete the partition, create a new, larger partition, and then restore from backup. 

Resizing a partition can be a very slow operation.
Having a backup is always a good idea before you do a resize operation, since if something goes wrong (like a power outage) you could lose everything otherwise.

So if you have a backup, the quickest way to expand is to delete and recreate the partition.


If you create a new partition, it will have a new UUID. You'll need to update your /etc/fstab so it associates the new UUID with /home.

---

