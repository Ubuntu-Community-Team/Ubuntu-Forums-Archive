---
title: "Trouble Installing"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by bvil on 2011-03-03
While I was installing from live CD, install process completely stopped, and I tried to reinstall it for the second time there was no option says automatic partitioning. Does this mean that I've already installed it?

---

### Post by sandyd on 2011-03-03
> **bvil said:**
> While I was installing from live CD, install process completely stopped, and I tried to reinstall it for the second time there was no option says automatic partitioning. Does this mean that I've already installed it?
you said it froze, so it might have been half-installed.

choose custom partitioning
select the linux partition, and click edit/properties/(or whatever corresponds to edit)
make sure the "format" box is checked, and choose the mountpoint as "/" (without quotes).
continue installing.

p.s. make sure your selecting the right linux partition. It should say that the file system is EXT4

---

### Post by bvil on 2011-03-04
Okay, so I literally don't have any free space and can't shrink my windows partition somehow. Should I go back to windows and delete my files or any other options?

---

