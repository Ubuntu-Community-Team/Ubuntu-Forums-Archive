---
title: "wubi vs dual boot"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by bilalakhtar on 2009-01-30
Hello everyone:o
can anyone tell me whether installing using wubi is better or using it in a dual boot config with xp proffesional sp3? Which one involvs more risks? which one is faster? is it easy to remove ubuntu if it is installed in a dual boot?

---

### Post by blazemore on 2009-01-30
Wubi is a way of installing Ubuntu to a "virtual" hard drive, contained within the NTFS filesystem of Windows.

As such, it is not normally as fast as a "bare metal" installation.

However, it is useful if you just want to try Ubuntu on your hardware.

If you like it, however, you should uninstall Wubi through add/remove programs in Windows.

You should then install Ubuntu directly to a disk partition, using ext3 or whatever, to gain the best performance. THe system will set up the dual boot for you.

---

