---
title: "Will kernel upgrade bugger up current drivers"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2009-11-20
Just curious as I current run the 2.6.31.14 kernel, and I keep getting asked to update to 2.6.31.15. Now the question is if I do this will I have to re-install the nvidia drivers that I installed manually? and will it affect any other settings in general or will it just upgrade itself and have no problems what so ever?

Plus is it worth updating the Kernel?

---

### Post by blazemore on 2009-11-20
If you have to ask, then no, you don't need to upgrade the kernel.
Why did you install the nVidia drivers manually?

---

### Post by terrykiwi83 on 2009-11-20
It's because I installed a beta version 190.42, and the one that Ubuntu installed by default wasn't the most up to date. :)

---

### Post by blazemore on 2009-11-20
Well then you'll have no problem reinstalling them

---

### Post by 3rdalbum on 2009-11-20
Your manually installed drivers will need to be recompiled (or in your case, reinstalled) when you upgrade the kernel. There are some HOWTOs around for adding your drivers to DKMS which automatically rebuilds the driver on kernel update.

This is a good reason to stick with repository drivers whenever possible, until Nvidia actually adds DKMS support to the Nvidia installer to save you from having to do it manually.

---

### Post by philinux on 2009-11-20
> **terrykiwi83 said:**
> Just curious as I current run the 2.6.31.14 kernel, and I keep getting asked to update to 2.6.31.15. Now the question is if I do this will I have to re-install the nvidia drivers that I installed manually? and will it affect any other settings in general or will it just upgrade itself and have no problems what so ever?

Plus is it worth updating the Kernel?

You must also have the proposed repos active. This is for testing and bug reporting. It could break your system. ;)

---

