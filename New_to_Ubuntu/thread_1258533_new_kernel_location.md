---
title: "new kernel location"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by eddski on 2009-09-05
When I update my system and it updates the kernel, where does it go? I am trying to match up the numbers in menu.lst file( where does the uuid come from, where can I locate it)

---

### Post by Liolikas on 2009-09-05
Newbie friendly distro like Ubuntu should update menu.lst automatically or at least suggest this!?

Ah if you still want manual menu.lst update just copy paste old section and change version numbers. Or talking in short way kernels should be in /boot.

---

### Post by Arand on 2009-09-05
and UUID is a unique identifier for partition.
The command "blkid" will list those
- Arand

---

### Post by wojox on 2009-09-05
Kernels in /boot
Menu.lst is in /boot/grub/

---

### Post by eddski on 2009-09-05
thanks for the comments, I just got intimidated by all the other numbers in menu.lst...didn't realize they were all the same except for the version number.

---

