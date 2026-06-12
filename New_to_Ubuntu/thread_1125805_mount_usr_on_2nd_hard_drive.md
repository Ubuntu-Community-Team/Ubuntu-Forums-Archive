---
title: "mount /usr on 2nd hard drive?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by sschnee on 2009-04-14
I have a netbook with 2 solid state drives.  sda is small, but faster.  sdb is larger and slower.  I would like to mount / to sda, and /home and /usr to sdb, since those are my two biggest space hogs.  Can I do that, or are there files in /usr that need to be on the same drive as /   ?

This would be for a fresh install once jaunty is out.

Thanks.

---

### Post by unutbu on 2009-04-14
When you run the Jaunty installer, at the fourth step entitled something like "Partitioning", choose "Manual" rather than "Guided" partitioning. This will allow you to define which partition you wish for /usr. (And which for /, /home, etc.).

---

### Post by durand on 2009-04-14
This thread might help you: [http://ubuntuforums.org/showthread.php?t=1074631](http://ubuntuforums.org/showthread.php?t=1074631)

---

### Post by sschnee on 2009-04-14
> **unutbu said:**
> When you run the Jaunty installer, at the fourth step entitled something like "Partitioning", choose "Manual" rather than "Guided" partitioning. This will allow you to define which partition you wish for /usr. (And which for /, /home, etc.).

So there is no problem with /usr being on a different hard drive than root?

---

### Post by unutbu on 2009-04-14
There is no problem with /usr being on a different hard drive than /, as long as both hard drives are always present at boot.

---

### Post by sschnee on 2009-04-15
Excellent, thanks.

---

