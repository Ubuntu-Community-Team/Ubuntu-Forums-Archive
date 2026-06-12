---
title: "compiling linux kernel : initrd"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by ercferret18 on 2009-03-07
I have just compiled the latest linux kernel using make oldconfig ; make ; make modules_install ; make install. But then, when I tried to make an initrd image, i noticed that the mkinitrd command does not exist. Is there any way to make an initrd image? because without it, my computer will not even mount the root file system.

---

### Post by sdennie on 2009-03-07
Is there a reason you are using the generic kernel compilation and not make-kpkg?  Using that method creates a .deb file for you and automatically does the initrd configuration.

Having said that, check the man pages for update-initramfs or mkinitramfs.  One of those two will probably work for you.

---

