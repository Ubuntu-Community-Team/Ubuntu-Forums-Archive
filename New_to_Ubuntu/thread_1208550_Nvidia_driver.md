---
title: "Nvidia driver"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-07-09
Hi
My ubuntu has updated from Linux 2.6.28-11-generic to Linux 2.6.28-13-generic by automatic update. But the new version doesnt support the Nvidia driver(NVIDIA-Linux-x86-185.18-pkg1.run). What can I do?
Now the boot menu shows 2 ubuntu option. How can I reduce to 1?

---

### Post by CLomax on 2009-07-09
1. The method you used to install the driver causes it to be reset when the kernel updates, you'll have to reinstall the driver - that's all I know.

2. *gksudo gedit /boot/grub/menu.lst*
   Scroll to the bottom and remove the menu entries labeled with ***2.6.28-11-generic***. I would keep two different kernel versions there in case the new one messes up something awful - it gives something to fall back on to.

---

### Post by ptn107 on 2009-07-09
You need to rebuild the module for the new kernel just like you did the first time.  You need to do this for each kernel update.  Using the driver from the Ubuntu repositories is much easier because it handles kernel updates automatically using dkms.

---

