---
title: "Screen Resolution Problems"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by bwsmith25 on 2008-12-12
I am running Ubuntu 8.10 on my HP nc6000 laptop. It has a 14.1 inch 1024x768 monitor. When I set the screen resolution on Gnome to 1024x768, everything (icons, etc.) is huge and slightly blurry. When I set the resolution higher (any of the higher options) the images are distorted/grainy and I can barely see the text because it is so small. Can someone please help me, because I really like everything else about ubuntu that I have encountered so far....

---

### Post by Mucho on 2008-12-12
open as sudo in your favorite text editor /etc/x11/xorg.conf and modify selection screen ...
after that save and reboot.

---

### Post by bwsmith25 on 2008-12-12
Not sure if this makes a difference, but when I am talking about images being distorted and text being blurry...I mean on the internet. When I press CTRL+ to enlarge the screen, it screws up the layout of mostly every website...

---

### Post by superprash2003 on 2008-12-12
which browser are you using?? have you tried another browser?? opera,firefox etc..

---

### Post by bwsmith25 on 2008-12-12
I am using Firefox 3

---

### Post by mapes12 on 2008-12-13
I had a similar problem with 8.10. I followed many threads and the general feedback is that editing the xorg.conf file in 8.10 makes little difference. This is because there appears to be a newer version of the X server deployed in 8.10 that tries to do things automatically.

In the end I solved the problem by installing 8.04LTS where manual configuration is still possible. If you do install 8.04 and you need to change your screen res settings then right click **Applications** select **Edit Men**u. When the GUI pops up select **Other** in the L/H column then select **Screen and Graphics** in the R/H column. Close. You should then be able to go Applications>Other>Screen and Graphics to manually set what you want. Your machine may require a restart first though.

That fixed it for me.

8.04 is supported up to April 2011 whereas 8.10 is only supported to April 2010.

---

