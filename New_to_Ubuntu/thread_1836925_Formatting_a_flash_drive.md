---
title: "Formatting a flash drive"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by dgoddard1 on 2011-08-31
I have this 8gig SanDisk that I want to use for archiving files, and it comes with some files on it for windows.I don't want those files and I don't want any partitions that they created for security that they did not tell me about.

SO IN UBUNTU ....

**How do I format the flash drive and utterly wipe out any software partitions or whatever that are on it from the manufacturer ?**

---

### Post by wojox on 2011-08-31
Use Disk Utility or Palimpsest.

---

### Post by dgoddard1 on 2011-08-31
> **wojox said:**
> Use Disk Utility or Palimpsest.Please excuse my ignorance but are these:
A.
-- Somewhere in the menu tree?
B.
-- Command line items?
C.
-- Something I have to download from somewhere?

---

### Post by bigpayne69 on 2011-08-31
withing the menu, go SYSTEM-> ADMINISTRATION-> DISK UTILITY

---

### Post by bigpayne69 on 2011-08-31
some of the newer versions don't use it anymore but I have always liked gparted for creating, managing, and deleting partitions.

---

### Post by Sef on 2011-09-01
> some of the newer versions don't use it anymore but I have always liked gparted for creating, managing, and deleting partitions.

I use [GParted]("http://gparted.sourceforge.net") for that too. It is also available in the repositories.

---

### Post by jfed on 2011-09-01
I like to use Gparted for this sort of thing. I'm pretty sure you can just run
```
sudo apt-get install gparted
```
The program is in system>administration Gparted and is fairly self explanatory 

Just select the drive from the drop down arrow on the top right, right click it in the main part and unmount, then right click it again and select "format to.." then pick the desired filesystem, and click the check on the top of the window to apply the changes.

Hope this helped!

---

