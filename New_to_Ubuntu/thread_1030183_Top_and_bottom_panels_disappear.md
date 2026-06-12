---
title: "Top and bottom panels disappear"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by gzav on 2009-01-04
Hi,

I've got a slight problem ever since i rebooted xubuntu, i can't see the top or bottom panels anymore. Everything else is normal, the icons are there, but that's it. I've tried deleting my .config folder to return to dafaults, but it didn't change anything

Can anyone help me find my panels again??

---

### Post by fooman on 2009-01-04
have you tried pressing alt-f2 and see if that brings up a "run program" box?

if it does....try typing the following into it and pressing "run":

          ```
xfce4-panel &
```see if that works.

---

### Post by gn2 on 2009-01-04
Right-click on the desktop and if you don't get the Main Menu, select Desktop Settings > Behaviour and tick "Show desktop menu on right-click"

Now close that box and right-click on the desktop and select Settings > Settings Manager > Panel and you will be able to add and configure new panels as desired.

---

### Post by gzav on 2009-01-04
> **fooman said:**
> have you tried pressing alt-f2 and see if that brings up a "run program" box?

if it does....try typing the following into it and pressing "run":

          ```
xfce4-panel &
```see if that works.

Yay! It worked! Thanks a lot

---

