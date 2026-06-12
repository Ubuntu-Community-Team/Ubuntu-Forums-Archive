---
title: "RAID - matching disks?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Twizzle on 2008-12-12
I am about to re install Ubuntu server edition and use software raid to mirror two partitions which will be the full capacity of the disks.
Is it better to have identical disks or is it fine to use disks from different manufacturers?

I only ask because my local supplier is all out of Seagate (which I have always used) but does have a Western Digital of the same capacity of a drive I alreadt have.

---

### Post by sydbat on 2008-12-12
I think that they need to be similar in size (ex 80GB and 80GB), but different manufacturers shouldn't be a problem.

---

### Post by stefangr1 on 2008-12-12
That's right: the reason it is best to have identical disks is that you always have the capacity/performance of the smallest/slowest disk when using RAID1.

---

### Post by albinootje on 2008-12-12
I read that it is recommended to let RAID have the full capacity of the disks. I don't remember reading a clear or important reason for that.

But i'm happily using software RAID on one server for more than a year now with different partitions where some are software RAID and some are not.

If you're using software RAID1, and choose for partitions rather than giving it the full disk right away, then it's a matter of making the partitions the same size.
In case you're using a 200 Gb disk with a 250 Gb disk, then you would have an additional 50 Gb of space.

---

