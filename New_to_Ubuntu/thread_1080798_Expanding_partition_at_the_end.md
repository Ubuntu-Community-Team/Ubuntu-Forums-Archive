---
title: "Expanding partition at the end?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by linkmaster03 on 2009-02-25
Say I have a partition at the beginning of my drive, another after it, and free space after that. Can I expand the 2nd partition to occupy the rest of the free space if it already has files on it?

---

### Post by swoll1980 on 2009-02-26
> **linkmaster03 said:**
> Say I have a partition at the beginning of my drive, another after it, and free space after that. Can I expand the 2nd partition to occupy the rest of the free space if it already has files on it?

Sure download a partitioner like [parted magic]("partedmagic.com/") burn it to a cd (like a distro) and boot it. It will let you "grow" your partition

---

### Post by zeroseven0183 on 2009-02-26
Yes, you can. You may also use **Gparted** (Gnome Partition Editor) for this. It offers a live CD version or you can download it from the repositories:

1. Click on **Applications** > **Add/Remove...**
2. look for **Gnome Partition Editor** from System Tools on the left pane of the Add/Remove Applications window
3. tick the check box
4. click **Apply Change**s
- or -
1. open **Terminal**
2. type **[B]sudo apt-get install gparted**[/B]
3. enter your password

Once it's installed, 
1. click on **System**
2. point to **Administration**
3. select **Partition Edito**r
4. enter the root password when required
5. then you can play around with GParted on your hard drive partitions

Remember: the partition should be unmounted first before you can reformat it.

I hope that helps.

---

### Post by linkmaster03 on 2009-02-26
Thank you very much swoll and zero.

---

