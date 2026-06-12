---
title: "How to remove Dual Linux OS"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by elurban3d on 2009-10-02
I have installed both Ubuntu and Xubuntu on my computer.  they are setup as installed as separate partitions.  How do I remove Xubuntu?  Xubuntu was installed second.

---

### Post by Zoot7 on 2009-10-02
Just delete the relevant partition, you'll only have to re-install grub to the MBR afterwards.
**[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")**

---

### Post by LewRockwell on 2009-10-02
depending on which /boot/grub/menu.lst file you were using you might only need to edit your menu.lst file

.

---

