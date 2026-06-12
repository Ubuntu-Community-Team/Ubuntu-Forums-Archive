---
title: "Clonezilla partition restore"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by melrokz on 2009-02-08
I just downloaded the latest version of Clonezilla to restore my ext3 partition from a Clonezilla image. I also saved a windows partition ntfs image using the previous version of Clonezilla.
      My doubt is, how will i restore clonezilla images to partitions after repartitioning the hard disk??? Clonezilla does not seem to restore the images properly if my partitions have changed. (I'm using the right partition type and have enough free space.)

---

### Post by Pollox on 2009-02-08
This might be something better asked on the [Clonezilla Forums]("http://clonezilla.org/") as they'll know more about it.

I had a similar problem, and ended up doing the device-to-device clone to store a copy of the partition I wanted to backup on an external device.  I think it had something to do with the partition numbers being different from the original partitions, so perhaps if you make sure they're the same you won't have a problem.

---

