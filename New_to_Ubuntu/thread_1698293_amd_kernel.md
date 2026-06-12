---
title: "amd kernel"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by dzon65 on 2011-03-02
Did this minimal squeeze install on a amd rig. Small question. How come that when using the 2.6.32-5-amd kernel,the cpu goes up twice compared to the default 2.6.32-5-686 kernel with the nouveau driver? (Going from 60Mb idle to 120b idle.)
Oh, and, how can I delete the not-in-use kernels in the grub menu when there's no menulist in /boot/grub ?

---

### Post by el_koraco on 2011-03-02
you can go to synaptic and look for linux-image-2, then remove. repeat the procedure for linux-headers.

---

### Post by dzon65 on 2011-03-02
Linux-image-2?

---

### Post by dzon65 on 2011-03-02
Second part ( grubmenu) solved. Grub2, duh. To do it, upgrade the /etc/default/grub file

---

