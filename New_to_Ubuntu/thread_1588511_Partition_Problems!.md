---
title: "Partition Problems!"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by KnightByDay on 2010-10-05
Hi everyone, I am an on and off Ubuntu user, it has been a while since I have used it...

I have recently installed Ubuntu 10.4 FROM Windows xp (Downloaded and installed while in xp) on my HP mini 110, and for some reason the most I could make the linux partition was 30 gig. Once it was all loaded and installed I opened Gnome Partition Editor and it will not allow me to unmount the root (main) partition as both ubuntu and xp seems to be one the same partition???

Im sure the solution is fairly simple but yeah! Please help... (:

---

### Post by Elfy on 2010-10-05
You installed using wubi - this is not the same as installing to a seperate partition. Wubi uses a virtual disk - in effect a file within windows.

You won't be able to unmount it when it's in use. You can look at LVPM to resize [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

If you wanted to be able to work with the partitions it would have been easier to not have started with wubi.

---

### Post by KnightByDay on 2010-10-05
> **forestpiskie said:**
> You installed using wubi - this is not the same as installing to a seperate partition. Wubi uses a virtual disk - in effect a file within windows.

You won't be able to unmount it when it's in use. You can look at LVPM to resize [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

If you wanted to be able to work with the partitions it would have been easier to not have started with wubi.


Yes! This is exactly what I have done. Thanks for your help! I will attempt to put linux in its own partition using the JKDefrag. (: Thank you again

---

