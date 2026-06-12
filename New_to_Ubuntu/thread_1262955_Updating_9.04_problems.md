---
title: "Updating 9.04 problems"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by johntrublu on 2009-09-10
hi,
just installed 9.04 ubuntu.  I need to update my system but every time i try i get this message.


The upgrade needs a total of 332M free space on disk '/'. Please free at least an additional 332M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by Her Ghost on 2009-09-10
sounds like your harddrive is full.  can you free up any space on there?

---

### Post by irv on 2009-09-10
Check your free space by going to Applications> Accessories> Disk Usage Analyzer. This Should tell you how much space you have available.

---

### Post by mapes12 on 2009-09-10
Go to Terminal and ```
sudo fdisk -l
```post the output back here. Meanwhile, have a read of this while we scratch our heads: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

