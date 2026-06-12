---
title: "problem with battery usage"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by videa on 2009-10-28
I installed xubuntu 9.04 for my laptop. How come it eats the battery in ~2 hours with power management settings on, when I could use vista for 3.5h. I would appreciate some tips to tweak this one out.

---

### Post by northern lights on 2009-10-30
This might be happening because of HDD I/O -
set your disk to the "noatime" option (/etc/fstab) such that there's less writing to the disk.

[wikipedia on access time]("http://en.wikipedia.org/wiki/Stat_(Unix)")

---

### Post by philinux on 2009-10-30
I think the default "relatime" is the correct one to use according to this.
e.g
UUID=xxxxxxxxx /               ext3    relatime,errors=remount-ro 0       1

[http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/)

Anyone care to explain.

---

### Post by northern lights on 2009-10-30
This is my understanding of the issue:

The power-saving preference for an idle machine should be that its disks are spun down.
If access times keep being written to the disk, it won't spin down or be woken up more often.

I keep reading warnings that "some applications" need stored access times to work properly, but I certainly know of none.
I've been using noatime as a mount option for all my partitions in both my desktop and laptop for the past 2 years and haven't ever had a problem with it. And it did increase my battery time on the laptop.

Obviously there's many more things having an influence on battery time such as CPU frequency scaling settings.

I dunno what really needs atimes to be written, I'll stick to noatime.

---

