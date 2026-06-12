---
title: "Removing Windows, Keeping GRUB"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by joey-elijah on 2009-05-10
I want to delete my Windows partition but keep GRUB (obviously), however i assume that GRUB was installed somewhere on the Windows partition/drive and don't want to delete it! 

How do i ensure that i'm not going to delete GRUB when i partition over my Windows partition?

---

### Post by lvleph on 2009-05-10
Grub is installed in /boot/grub/. The master boot record will be fine if you delete the windows partition.

---

### Post by joey-elijah on 2009-05-10
> **lvleph said:**
> Grub is installed in /boot/grub/. The master boot record will be fine if you delete the windows partition.

Thanks for the fast response! Much appreciated!

---

