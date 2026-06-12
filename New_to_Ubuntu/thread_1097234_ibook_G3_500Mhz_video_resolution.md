---
title: "ibook G3 500Mhz video resolution"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by nargilamonster on 2009-03-15
Hi,
My iBook G3 boots to a screen resolution problem. It was fine when I used 6.06 but when I did a fresh install of 8.04 (and then upgrade to 8.10) (Xubuntu and Ubuntu)the display option for 1024x768 is not available in the GUI. Only 800x600 is available. I saw some threads explaining I needed to modify my xorg.conf file b/c of incompatibilities with my video card. Problem is, I have no clue what that xorg file is, or how to modify it. Could someone please explain it using beginner talk?

thanks!

---

### Post by miegiel on 2009-03-15
It's a settings file for X11 (part of the GUI), you can find it in /etc/X11/

To edit it type
```
sudo gedit /etc/X11/xorg.conf
```
in a terminal.

---

### Post by nargilamonster on 2009-03-15
aha! thanks so much!

---

