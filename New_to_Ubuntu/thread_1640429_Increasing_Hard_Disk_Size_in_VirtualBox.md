---
title: "Increasing Hard Disk Size in VirtualBox"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by chome4 on 2010-12-07
How is this done? I can see my existing size but it doesn't make it clear how to increase it.

---

### Post by bodhi.zazen on 2010-12-07
It is covered here under "Storage"

[http://forums.virtualbox.org/viewtopic.php?p=33945](http://forums.virtualbox.org/viewtopic.php?p=33945)

Basically you make a new disk and copy the old data either with dd or gparted.

If you use gparted, boot a "live" disk, copy, then resize the old partition (s).

Details in link above.

---

### Post by CharlesA on 2010-12-07
Don't forget to make sure you have backups before doing anything.

Even if it's a VM, things can go wrong.

---

### Post by chome4 on 2010-12-08
Thanks for the info...

---

