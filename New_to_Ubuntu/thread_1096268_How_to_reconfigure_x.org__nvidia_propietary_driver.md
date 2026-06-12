---
title: "How to reconfigure x.org  nvidia propietary drivers after a kernel upgrade"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Kosimo on 2009-03-14
Hello. I couldn't find out how to reconfigure x.org after a kernel upgrade if you previously installed nvidia proprietary drivers manually.

How was the command? 

Thanks!!!

---

### Post by martrn on 2009-03-14
> **Kosimo said:**
> Hello. I couldn't find out how to reconfigure x.org after a kernel upgrade if you previously installed nvidia proprietary drivers manually.  How was the command?  Thanks!!!

You don't need to reconfigure Xorg.conf is your are re-installing the nVidia drivers, after a kernel upgrade, you will need to run the (same) nvidia propietary driver install (or newer) again in order to install the driver again after a kernel upgrade and every kernel upgrade.

reconfigure-ing xorg involves manually editing xorg.conf via '**sudo nano /etc/X11/xorg.conf**'   The command was :: '**sudo dpkg-reconfigure xserver-xorg**' but I belive now this just writes an empty file.  '**sudo nvidia-xconfig**' will put back-in using the nvidia config files, as nvidia drivers need some sort of xorg.conf file for it to work, but usually installing (again) the nvidia proprietary drivers do that in any case.

---

### Post by Kosimo on 2009-03-14
> **martrn said:**
> You don't need to reconfigure Xorg.conf is your are re-installing the nVidia drivers, after a kernel upgrade, you will need to run the (same) nvidia propietary driver install (or newer) again in order to install the driver again after a kernel upgrade and every kernel upgrade.

reconfigure-ing xorg involves manually editing xorg.conf via '**sudo nano /etc/X11/xorg.conf**'   The command was :: '**sudo dpkg-reconfigure xserver-xorg**' but I belive now this just writes an empty file.  '**sudo nvidia-xconfig**' will put back-in using the nvidia config files, as nvidia drivers need some sort of xorg.conf file for it to work, but usually installing (again) the nvidia proprietary drivers do that in any case.


Ok.
I though that by just typing some instruction nvidia-xxxxx then I could easily reconfigure them.
Thanks for the answer!

---

