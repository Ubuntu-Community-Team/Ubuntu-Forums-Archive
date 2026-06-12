---
title: "Rolling back kernel"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by mikeody on 2010-11-21
Am  running 10.04 with 2.6.32-21 kernel.
If I want to 'roll back' to use an 'older' kernel, how do I do it ?
When I boot and hold down 'Shift' the only option I have is 2.6.32-21
I would want to continue to use the 'older' kernel for a while.
Thanks.

---

### Post by ajgreeny on 2010-11-21
If it's not in the grub menu you don't have an earlier kernel.

Why do you think you should have one?

---

### Post by wojox on 2010-11-21
> **mikeody said:**
> Am  running 10.04 with 2.6.32-21 kernel.
If I want to 'roll back' to use an 'older' kernel, how do I do it ?
When I boot and hold down 'Shift' the only option I have is 2.6.32-21
I would want to continue to use the 'older' kernel for a while.
Thanks.

Look in your /boot directory. Do you see an older one?

---

### Post by mikeody on 2010-11-21
Am having problems with a Dell GX260 [Intel 845 chipset] shutting down randomly. Have swapped ALL hardware - have identical PC - copied OS to new hard drive etc.
I read somewhere here that there MAY be some potential problems with late kernels and 845 chipsets.
Almost a last resort.
Thanks.

---

### Post by mikeody on 2010-11-22
No, only one kernel is in /boot.
Does that mean then that there is nothing I can do about an earlier kernel ?

---

### Post by wojox on 2010-11-23
> **mikeody said:**
> No, only one kernel is in /boot.
Does that mean then that there is nothing I can do about an earlier kernel ?

Never tried it, but you could open synaptic and search for kernel and look for the one before that and mark for installation.

---

