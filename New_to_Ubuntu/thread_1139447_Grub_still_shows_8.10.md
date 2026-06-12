---
title: "Grub still shows 8.10"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by sqrooup on 2009-04-27
Have just upgraded to Jaunty.
I have a duel boot system; Ubuntu on 1 drive (9.04), and Kubuntu on another drive (8.04).
I tend to use Ubuntu more than Kubuntu (personal preference).
However when I boot up, the choices are;
Kubuntu (and its variants), then;
Ubuntu 8.10 (and its variants).
I would like to change the order (Ubuntu first, then Kubuntu; so that it will automatically start with Ubuntu), and show the correct version number.

---

### Post by Svensk023 on 2009-04-27
you can edit your grub menu by typing the following into a terminal 

```
sudo gedit /boot/grub/menu.lst
```

towards the bottom of that file is where you will find the lists of your bootable Desktop Environments. just use caution when editing.

---

