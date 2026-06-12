---
title: "Disk sort of gone"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-01-11
I noticed a little problem when I started my computer today, it booted as normal but then stopped saying that some program saying that it couldn't mount *long uuid* that included my home folder. Now I managed to mount it anyhow but it's a little weird since I'm forced to manually mount it every time I boot and even wired disk utility say it don't recognize the partition (see attachment and notice where it's mounted).

What is the problem?


EDIT:
fdisk
```

:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000927e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         851     6835626   83  Linux
/dev/sdb2             852       60801   481548375    5  Extended
/dev/sdb5             852        5714    39062016   83  Linux
/dev/sdb6            5715        5957     1951866   82  Linux swap / Solaris
/dev/sdb7            5958       60801   440534398+  83  Linux


```

---

### Post by tom.swartz07 on 2010-01-11
> **SpinningAround said:**
> I noticed a little problem when I started my computer today, it booted as normal but then stopped saying that some program saying that it couldn't mount *long uuid* that included my home folder. Now I managed to mount it anyhow but it's a little weird since I'm forced to manually mount it every time I boot and even wired disk utility say it don't recognize the partition (see attachment and notice where it's mounted).

What is the problem?


EDIT:
fdisk
```

:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000927e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         851     6835626   83  Linux
/dev/sdb2             852       60801   481548375    5  Extended
/dev/sdb5             852        5714    39062016   83  Linux
/dev/sdb6            5715        5957     1951866   82  Linux swap / Solaris
/dev/sdb7            5958       60801   440534398+  83  Linux


```

Try a badblocks search. I had something similar to that happen to me just the other day.

in a terminal
```
badblocks
```
it will run for a little while, depending on the speed of your drive.

Post the output here and we could take it from there.

The only other thing that i could think it would be is a bad fstab file.

---

### Post by warfacegod on 2010-01-11
> "Windows 7 was my idea"- I guess Microsoft enjoys copyright infringement?

Not really, it's just Microsoft's new way of yet again blaming the user.

---

