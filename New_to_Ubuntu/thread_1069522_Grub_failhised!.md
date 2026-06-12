---
title: "Grub failhis?ed!"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Konstabel on 2009-02-14
I have a dual boot Windows/Ubuntu system and when I tried to reboot last, the grub failed to initialise! How can I fix this?

---

### Post by golusweet on 2009-02-14
re-install your grub.

sudo grub

find /boot/grub/stage1

(Use the output in next command)

root (hd0,1)

setup (hd0)

quit

---

### Post by Konstabel on 2009-02-14
Thanks. But I cannot seem to find terminal while running the live CD. Where can I find it?

Edit:
Don't worry. Found it

---

