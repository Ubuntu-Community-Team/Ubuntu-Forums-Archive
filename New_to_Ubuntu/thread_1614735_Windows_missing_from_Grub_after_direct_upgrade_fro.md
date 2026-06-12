---
title: "Windows missing from Grub after direct upgrade from 8.04 to 10.04."
date: 2010-11-06
forum: New to Ubuntu
---

### Post by diablo75 on 2010-11-06
A friend of mine upgraded his computer directly from Ubuntu 8.04 to 10.04.  Things went smoothly for the most part, but for some reason Grub doesn't list Windows in the menu as an available operating system like it used to.  Does anyone know of an easy way to fix this?

Thanks!

---

### Post by wilee-nilee on 2010-11-06
Hardy was grub-legacy and lucid is grub2. If it was me I would just upgrade to grub2.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

I think the sudo update-grub command can sometimes work in grub-legacy, but generally it is putting the correct stanzas in the grub menu.list

You probably should have them run the bootscript in my signature to see the whole setup.

---

