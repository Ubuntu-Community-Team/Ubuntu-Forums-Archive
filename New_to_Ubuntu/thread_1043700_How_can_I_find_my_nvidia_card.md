---
title: "How can I find my nvidia card"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by waynefwayne on 2009-01-18
I want to be able to look and tell what hard ware my computer
has to research my driver problem.:confused:

---

### Post by abn91c on 2009-01-18
in synaptic look for and install hardinfo, it will show you all you hardware

---

### Post by aheckler on 2009-01-18
The command ```
lspci | grep VGA
``` should display it.

---

### Post by jimmy the saint on 2009-01-18
If you are trying to install a video card driver, first go to 
System>administration>hardware drivers and see if any restricted drivers are listed.  If there are, just click enable and let it install.  You will have to restart then you will be good to go.

---

### Post by waynefwayne on 2009-01-18
Thanks

---

### Post by hyperyoda on 2009-01-18
lspci -vv|grep "VGA "

here is mine:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])

zach

---

