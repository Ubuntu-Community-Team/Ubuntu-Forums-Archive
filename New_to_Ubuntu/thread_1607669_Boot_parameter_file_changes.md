---
title: "Boot parameter file changes"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by schwine on 2010-10-28
RE: if one of the boot parameters were needed during installation, permanent changes need to be made in the following file after installation has completed:  /boot/grub/menu.lst

Can someone direct me to the changes that need to be made to this file when a boot parameter is used during the installation of Ubuntu 10.10 
I'm new to Unix and Ubuntu, so it would help me to know how to access this file, and then what changes to make to it.
I haven't done the installation yet, I'm just preparing for this potential outcome. 

Many thanks.

---

### Post by Hippytaff on 2010-10-28
10.10 uses Grub2. There is no menu.lst, but you can configure /boot/grub/grun.cfg

[https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg)

---

