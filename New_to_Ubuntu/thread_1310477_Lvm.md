---
title: "Lvm"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by corsakh on 2009-11-01
Hey guys,

How do I install LVM with Ubuntu? I did not see this option installing Ubuntu 9.10 from Live CD. Should I use an alternative version instead?

---

### Post by corsakh on 2009-11-01
Bump.

---

### Post by Dayofswords on 2009-11-01
this may help you.... idk maybe, not even sure what your talking about really

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

---

### Post by peculiar penguin on 2009-11-01
If you have a working internet connection in LiveCD mode you could apt-get lvm2, set up the partitions and stuff and then run the installer. Just don't let it reboot when it's done, you still have to chroot into the new system and install the lvm stuff there too.

At least that's what I do (plus cryptsetup for encryption), I'm not sure if this is the correct/best way but it works for me.

---

