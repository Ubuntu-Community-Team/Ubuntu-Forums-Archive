---
title: "is there any way to have a xorg.conf file for ubuntu 10.04?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by legolas_w on 2010-05-19
hi

I want to configure my monitor resolution manually in ubuntu 10.04 but when I looked inside the /etc/xorg/  there is no xorg.conf file there.

Any suggestion on what should i do?


thanks.

---

### Post by AnimalMagic on 2010-05-19
Create one...? It's just a text file.

---

### Post by jbrown96 on 2010-05-19
> **AnimalMagic said:**
> Create one...?

xorg.conf is no longer necessary, but if you need to create one, then the settings will be respected. 
There's probably a better way to set your resolution though. Usually, xorg.conf is only needed for strange input hardware.

---

### Post by AnimalMagic on 2010-05-19
I use a KVM switch which doesn't seem to provide proper video data to ubuntu, so xorg.conf is necessary, unless I want 800x600 on a 20" widescreen...!

---

### Post by ddecator on 2010-05-19
/etc/X11/xorg.conf if you really need it.

---

### Post by elliotn on 2010-05-19
check out this post there is a xorg file there.
[ubuntuforums.org/showthread.php?p=9299880#post9299880]("ubuntuforums.org/showthread.php?p=9299880#post9299880")

---

