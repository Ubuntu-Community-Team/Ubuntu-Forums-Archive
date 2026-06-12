---
title: "Ati Catalyst control center, 9.04 &amp; Radeon 9600XT"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Barba Pere on 2009-06-06
So, last night I installed Catalyst control center with Applications >> Add&Remove.

This morning I could not start Ubuntu (9.04). Something like Blue screen appeared which makes me belive graphic card has some problems

What is wrong. am I not supposed to install it.

My comp is from 2003 - Amd Barton, Nvidia motherboard & ATI Radeon 9600XT graphic card

---

### Post by Legace on 2009-06-06
ATi Catalyst Control Center doesn't support your card on Ubuntu 9.04.
You need to uninstall the driver:

Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

