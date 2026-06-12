---
title: "Hard Drive question"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-01-20
I have a 320 SATA HDD and karmic is reading it as 285gb HDD  I also have a 150gb SATA hard drive too but it reads it fine I just mount it to put more space on my comp .

can someone tell me how to get get the full 320 gb

---

### Post by underquark on 2010-01-20
1] Karmic likely isn't reading the hard drive but a partition on the hard drive.  Do you also have a swap partition and any other partitions (System...Admin...Partition Editor will tell you)?

2] 320 doesn't usually equate to 320 all being available once a drive is formatted.

3] Journalling on an ext3 partition can take up 5% of the remaining space.

---

### Post by underquark on 2010-01-20
[Sorry, double-posted in error]

---

