---
title: "Hard Drive Inquiry"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Grifulkin on 2009-02-23
So I just happened to check out my Disk Usage Analyzer and it claimed that my total filesystem capacity is 53.1 GB but my hard drive in this old laptop is only 30 GB how is that possible?

---

### Post by matteojg on 2009-02-23
Isn't the western digital an external hard drive?
So...do you have the linux OS installed on the external drive, maybe?

---

### Post by Grifulkin on 2009-02-23
No, that is in my desktop that I have an 80 GB Western Digital.  This laptop was my first computer and it only had a 30 GB and the hard drive is going up so I got rid of windows and put stricktly Ubunut on it, and I love it, I also have a Netbook and I really need to update that 80 GB hard drive in my desktop but that is beside the point.

---

### Post by benerivo on 2009-02-23
Try ```
sudo fdisk -l
```the first line of the output gives you the drive size.

---

### Post by 3rdalbum on 2009-02-23
Disk Usage Analyser counts external mounted drives and the "virtual" filesystems too (~/.gvfs, /proc, /sys). The virtual filesystems appear to take up space, but do not. It's normal.

---

