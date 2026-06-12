---
title: "Gparted - cannot reuse unallocated space"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by bartgovaert on 2009-08-02
Friends,
I have a dual Vista/Ubunto 9.04 system.
I want to increase the size of the Ubuntu partition.
There are 3 unallocated "partitions" that I'd like to use. From what I have read, I need to move these inside the logical partion where I want to append them. So I guess I would have to move them to /dev/sda4 (where /dev/sda5 - the actual Linux disk and the swap disk /dev/sda6 live). The unallocated sectors do not seem to live under any /dev

However, using Gparted from Live CD, unmounting everything, I do not seem to be able to do anything with the unallocated sections, all options are greyed out.

Anybody has any experience with this?

Thanks

Bart

---

### Post by apmcd47 on 2009-08-02
You cannot move them into sda4, all you can do is move and resized sda4. So, if you have something like ```
(free-space)(partition)(free-space)(partition)
``` you need to move all partitions up to and including sda4 forward so there are no gaps between them. Also move all partitions behind sda4 to the end of the disk. This may cause problems as partitions may end up being renumbered, so you should back everything up. You can then resize sda4. Once that is done you can either resize the partition inside sda4 or add new partitions.

Good luck!

Andrew

---

### Post by LewRockwell on 2009-08-02
I've had problems with using Ubuntu LiveCDs to work on partitions before
(seemed like it was an issue with not dismounting the swap partition even after repeated attempts via different methods)


Subsequently, I've just thrown a Puppy Linux LiveCD in when I wanted to use Gparted to work on partitions

.

---

