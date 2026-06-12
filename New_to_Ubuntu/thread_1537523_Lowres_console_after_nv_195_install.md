---
title: "Lowres console after nv 195 install"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by ignavia on 2010-07-23
My console used to run at native res, but then I used the hardware drivers panel to enable Nvidia-current (which is 195.35.24), and now it's at VGA or something. 

Surely there's an easy fix for this...

(By console, I mean tty1-tty6, and also the loading and shutdown screens.)

Thanks.

---

### Post by matrixblue on 2010-07-23
Run dpkg-reconfigure on the package you installed

---

### Post by ignavia on 2010-07-23
Surely there's just a config file to edit or something, right?

...and yes, I tried dpkg-reconfigure. No dice.

---

