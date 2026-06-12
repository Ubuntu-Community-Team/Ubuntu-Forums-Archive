---
title: "Find LVM UUID for fstab ?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by thornomad on 2009-02-25
Hi -

I am using LVM2 and have two different volume groups with a number of logical volumes.  

For one volume group, all of my UUIDs for the logical volumes seem to be mapped correctly (and I can use them in /etc/fstab) -- however, on my other volume group, they don't seem to show up and fstab won't recognize them.

Here are the details (uuid by disk):

```
damon@leaker:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 25 2009-02-24 21:15 0a9a787e-1947-4996-9e5e-35cba443534b -> ../../mapper/raid5vg-home
lrwxrwxrwx 1 root root 10 2009-02-23 12:01 7f02b98e-6157-44f8-8d89-e50f61b28cd3 -> ../../sdd1
lrwxrwxrwx 1 root root 25 2009-02-23 12:01 8831f2b5-ab8a-41b7-ae61-2fdf0adaa6fd -> ../../mapper/raid5vg-swap
lrwxrwxrwx 1 root root 25 2009-02-23 12:01 9636f138-5d3d-49c9-ad28-159adfeb88a4 -> ../../mapper/raid5vg-root
lrwxrwxrwx 1 root root  9 2009-02-23 12:01 d7c8b839-3a9d-4326-8d9f-da7a6d5c1e61 -> ../../md0
```

Now, there is one logical volume that is missing from this list (should be: --> ../../mapper/backup-daily):

```
damon@leaker:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/backup/daily
  VG Name                backup
  LV UUID                JtefkS-bfqy-JpYO-yLA0-J827-FgUn-k1RGFO
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                600.00 GB
  Current LE             153600
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:3
   
  --- Logical volume ---
  LV Name                /dev/raid5vg/swap
  VG Name                raid5vg
  LV UUID                5zrzIy-8jd1-f1b9-G5q0-O7fe-Rb9R-FRx9D5
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.86 GB
  Current LE             476
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/raid5vg/root
  VG Name                raid5vg
  LV UUID                26wkDV-9ch0-R63z-ID6o-l6yb-wD0o-XSo8vJ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                5.59 GB
  Current LE             1430
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1
   
  --- Logical volume ---
  LV Name                /dev/raid5vg/home
  VG Name                raid5vg
  LV UUID                bOy9Nd-j8WL-e7ji-piGA-rF0C-icxa-BKgLJU
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                932.32 GB
  Current LE             238674
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:2


```

Right now, I am just using the physical path to the volume in fstab (/dev/backup/daily) but I would rather use the UUID in case something crazy happens.

Any ideas on what's not working ?  Do I have to manually create a new uuid link or something ?  Register it somehow ?  I think I must have missed a step ... the first group (that is working) was setup through the ubuntu alternate installer ... the second group (that I can't find the uuid for) was done via command line.

Thanks,
Damon

---

### Post by blueridgedog on 2009-02-27
I don't know anything about LVM, but I get my UUIDs by:
```

blkid /dev/deviceIwanttoknowabout
```

---

