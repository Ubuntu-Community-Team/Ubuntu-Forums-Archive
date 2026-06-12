---
title: "Dual-Booting, removing the windows partition"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Alfx on 2009-01-29
-I had been using windows XP for quite a while

-I installed Ubuntu on another partition

-I now wish to format the windows XP partition and add the memory to the Linux one.

Question: Can I boot from a live CD, format the Windows partition and then add it to the Linux partition with gParted?

Thanks

---

### Post by marshall.robert on 2009-01-29
Yes.

---

### Post by caljohnsmith on 2009-01-29
If you want to add the Windows partition freed space to your existing linux partition, it depends on the physical layout of your partitions whether you can do that or not. In other words, your linux partition would have to be physically next to your Windows partition on the drive. In order to get an idea of what your current partition scheme looks like, how about opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu

```

---

