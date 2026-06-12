---
title: "gparted error"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by libihero on 2011-01-09
i did a reinstall of ubuntu so i could seperate it into /, /home/, and /boot partitions. to do so i shrank my original ubuntu partition, installed the three seperate partitions, and copied my home folder from my original into the /home and deleted the original partition.  now when i tried to move my new /home partition to the left in order to grow it, gparted always gives me the following error:

```

GParted 0.6.2

Libparted 2.3
Move /dev/sda2 to the left and grow it from 59.60 GiB to 115.41 GiB  00:00:00    ( ERROR )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2
start: 363399166
end: 488392064
size: 124992899 (59.60 GiB)
move partition to the left and grow it from 59.60 GiB to 115.41 GiB  00:00:00    ( ERROR )
     	
old start: 363399166
old end: 488392064
old size: 124992899 (59.60 GiB)
libparted messages    ( INFO )
     	
Unable to satisfy all constraints on the partition.

```

i attached what i'm trying to do with what my partition looks like

---

### Post by kevxh on 2011-01-09
sda2 is the extended partition. sda7 is the partition you should be modifying.

---

### Post by srs5694 on 2011-01-09
If I'm interpreting it correctly, libihero started with space that was unpartitioned in the primary table -- that is, /dev/sda2 needed to be resized before /dev/sda7 could be resized, and the /dev/sda2 resize operation is failing.

This can happen because of differing alignment requirements. Until recently, most Linux partitioning tools aligned on the (essentially fictitious today) "cylinder" boundaries. Recently, though, tools have been favoring alignment on 1 MiB boundaries, in order to improve performance with Advanced Format disks and RAID arrays. Windows switched to MiB alignment with Vista. My suspicion is that the disk originally used cylinder alignment, but the version of GParted you've got is using MiB alignment (or possibly the other way around), and you're running into a rounding error bug.

One way around this problem is to look for options in GParted to change the alignment policy. Such options should appear in the Resize/Move dialog box. On the GParted 0.5.2 I've got on the system on which I'm typing now, there's a "round to cylinders" check-box that you could uncheck. Newer versions have a field with three options, IIRC, to align to cylinders, align to MiB, or not align at all.

Another approach is to resize the partition so that there's a small gap between it and the preceding (and/or following) partition(s). You'll waste a bit of disk space, but at least you'll be able to get the job done.

---

### Post by libihero on 2011-01-09
it worked!! thanks srs! :)

---

