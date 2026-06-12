---
title: "Cannot change xorg.conf in Hardware Drivers"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-05-11
I went to System>Administration>Hardware Drivers to Activate NVidia accelerated graphics driver version 173 and deactivate 180 but I was unable to. I got a message that I cannot reconfigure xorg.conf. What should I do? How do I fix this so that I can activate 173 and deactivate 180?

I usually can change from 180 to 173 on my old Ubuntu 8.10.

NVidia 8200M G on Ubuntu 9.04

EDIT: I did a

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo dpkg-reconfigure -phigh xserver-xorg
```

to create a backup of xorg.conf, and reverted to failsafe settings.

and installed 173. Automatically deactivated 180.

---

### Post by lavinog on 2009-05-13
Cool background and theme.

have you tried removing xorg.conf then install?
or post your xorg.conf

---

