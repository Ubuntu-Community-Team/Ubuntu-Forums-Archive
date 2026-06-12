---
title: "Screen Rotation &amp; Metacity Problem"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by john_gault on 2009-01-09
Hello. I have Ubuntu 8.10 64 bit, Athlon 3800+ dual core and a geforce 8600gt. I recently ordered a monitor that I can rotate 90 degrees to read .pdf files. Unfortunately the rotate option in screen resolution is not working. I tried adding a rotate command to the old xorg file that I found on Google and then thanked god I had made a backup. How do I enable the rotation option without kill my display? Also, my windows keep sticking to the top left bar under applications and will not move. I use the 'metacity --replace' command to  reset them but I have to type it in every time I restart the computer. Any help is appreciated.

---

### Post by gettinoriginal on 2009-01-15
For the rotation problem: :p
```
sudo gedit /etc/X11/xorg.conf
```

and added
Option "RandRRotation"
so it looks like this.

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Option "NoLogo" "true"
Option "RandRRotation"
EndSection


For the metacity problem, install "Compiz Fusion Icon" (in Synaptic), it allows you to select your window decorator and window manager, thereby making metacity your default manager.

---

