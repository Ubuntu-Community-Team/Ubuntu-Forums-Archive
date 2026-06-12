---
title: "Group unallocated memory?"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Aquatic Fist on 2010-07-11
[IMG]http://dl.dropbox.com/u/6029947/gparted.png[/IMG]

I would like to make a partition out of all unallocated memory shown in the picture above. But it seems like it's only possible to make a partition out of one of these.

So is it somehow possible to make a partition of all unallocated memory with gparted or any other application for Ubuntu?

---

### Post by sanityfare on 2010-07-11
Hi

I managed to do this by using the startup disc and then using gparted to first create a partition and then resizing the partition you want it to be included in. Please remember that as your picture shows, the free space on you drive (grey areas) are free as shown, so your /dev/sda4 can be resized to the left or the right(grey areas) once a new partition is created. 

Hope this helps

SF

---

### Post by Shazaam on 2010-07-11
Memory? No, it's called "Unallocated" space. Don't worry, a lot of us have called it that before.  :)
No need to add any more partitions; use GParted (Partition Manager) on the livecd to resize/move your partitions. "Merge partitions" is not available using GParted.

---

### Post by Bachstelze on 2010-07-11
You'd have to move your existing partition to one end of the disk so that all free space is contiguous (you obviously can't create a partition from non-contiguous blocks).

---

### Post by Aquatic Fist on 2010-07-12
Thanks for the quick replies everyone. :)

> **Shazaam said:**
> Memory? No, it's called "Unallocated" space.  Don't worry, a lot of us have called it that before.  :)

Thanks for telling. ;)


> **sanityfare said:**
> Hi

I managed to do this by using the startup disc and then using gparted to first create a partition and then resizing the partition you want it to be included in. Please remember that as your picture shows, the free space on you drive (grey areas) are free as shown, so your /dev/sda4 can be resized to the left or the right(grey areas) once a new partition is created. 


Hope this helps

SF
> **Bachstelze said:**
> You'd have to move your existing partition to one end of the disk so that all free space is contiguous (you obviously can't create a partition from non-contiguous blocks).

I ended up like this:
[IMG]http://dl.dropbox.com/u/6029947/gparted2.png[/IMG]

I deleted the sda4 and made a big partition. (sda1) So I guess it's [SOLVED].

---

