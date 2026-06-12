---
title: "Nvidia Resoltion settings not holding"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by servicetech on 2009-04-06
I have to keep resetign the refresh rate every time I boot the computer. I've tried to save to file and got this message:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by jbrown96 on 2009-04-06
> **servicetech said:**
> I have to keep resetign the refresh rate every time I boot the computer. I've tried to save to file and got this message:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

You probably did not open nvidia-settings with root permissions. Try it again and press Alt+F2 then if you are using ubuntu, ```
gksu nvidia-settings
``` or kubuntu ```
kdesudo nvidia-settings
``` If you are making changes that you want to save, you will need to launch it with root permissions. However, if you are just temporarily changing the resolution or attaching a projector or temporary monitor, then you can launch it normally.

---

### Post by servicetech on 2009-04-07
Perfect !!
:guitar:

---

