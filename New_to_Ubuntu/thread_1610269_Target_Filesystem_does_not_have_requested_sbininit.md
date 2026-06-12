---
title: "Target Filesystem does not have requested /sbin/init."
date: 2010-10-31
forum: New to Ubuntu
---

### Post by Tiz_earth on 2010-10-31
I've recently put Ubuntu 10.10 on a 2002 HP Omnibook xe4400s.  I know, you might think it's an old computer, but I don't like spending money.  Anyhow, it was working fine (or okay, I guess) until yesterday, when for the first time, I get a screenful of this:

> mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg

Busybox asks me for a command, and I'm completely lost.

---

### Post by Gone fishing on 2010-10-31
Its not finding / when booting up - the question is why? Probably a damaged file system I'd boot up on a live CD and try to fix it and have a look at the root partition.

Have a look at:

[http://ubuntuforums.org/showpost.php?p=9411005&postcount=2](http://ubuntuforums.org/showpost.php?p=9411005&postcount=2)

---

### Post by Tiz_earth on 2010-11-01
Turns out the HD was dead.  Gparted checks didn't work.  TOPIC CLOSED.

---

