---
title: "How can i mount Partition Disk Permenently?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by tajiknomi on 2010-09-14
[SIZE=2][I]I am Using Ubuntu, and every time when i boot up, it automatically unmount my other partition disks.

i want to **Mount** these partition disk **permanently**,is their any way for this...?
[/I][/SIZE]

---

### Post by Elfy on 2010-09-14
Use fstab 

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

There are GUI ways to accomplish it - ntfs-config or pysdm.

But it's hard to decide what would be best given the information you let us see ;)

You might it find it worthwhile to read this - [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Mark Phelps on 2010-09-14
> **tajiknomi said:**
> [SIZE=2][I]I am Using Ubuntu, and every time when i boot up, it automatically unmount my other partition disks.

i want to **Mount** these partition disk **permanently**,is their any way for this...?
[/I][/SIZE]

If any of the "partition disks" contain Vista/Win7 OS partitions, my advice is NOT to mount them permanently as it is too easy to do an unclean shutdown or unmount -- and that will render either of these unbootable.

---

### Post by tajiknomi on 2010-09-14
[SIZE=2]*Yes i have my one Partition with** win-7***[/SIZE], [SIZE=2]*If i **unmounted** them permanently,will their any probability of having **harm** to **Boot-files**..?*[/SIZE]

---

### Post by Mark Phelps on 2010-09-15
> **tajiknomi said:**
> Yes i have my one Partition with win-7

In that case, I recommend that you NOT mount it using FSTAB, unless you mount it read-only.

Instead, I recommend you do the following:
1) Use Places to mount the Win7 partition only when needed. This will put an icon on your desktop
2) Be sure to use clean shutdown option to unmount the partition when done.  Don't rely on Ubuntu to do a clean shutdown.

---

