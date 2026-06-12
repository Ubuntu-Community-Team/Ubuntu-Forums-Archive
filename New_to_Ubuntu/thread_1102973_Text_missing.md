---
title: "Text missing"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Paul T. on 2009-03-22
On some applications such as Amarok & Qcad, the text is missing from the drop down menus such as file, edit etc, there are icons shown but no text?
Same applies to the help menus, icons but no text.

---

### Post by Temposs on 2009-03-22
That's probably a compiz & graphics driver problem. Do you have desktop effect/compiz enabled? Which graphics cards do you have?

---

### Post by ajgreeny on 2009-03-22
Try running without compiz, if you have it running.  ```
metacity --replace
``` should do it just to try, though you may find a different setup of config will overcome the problem, so get **configcompiz-settings-manager** if you haven't already installed it, and try another combination of active plugins.

---

### Post by Paul T. on 2009-03-27
Thx for the replies guys; I've not been using Compiz previously, but have now installed it, though where to start with it I'm not sure as there are so many options, any ideas?

I'm using Nvidia graphics card with the 'proper' driver so 3D effects are activated, though I'm using the older version 96 driver, as the recommended version 173 didn't work.

---

### Post by Paul T. on 2009-04-10
Any advice anyone?
Attatched image to show problem:

---

### Post by Paul T. on 2009-04-10
Sorted,

seems to be a known issue with Nvidia driver, disabled all desktop effects and problem solved, apps load faster too. :cool:

---

### Post by ameermawia on 2009-04-10
hey i have the same problem with few of my applications like valknut.
i tried disabling all desktop effect by selecting from the visual effects. but still the problem persist.so is there ant other way of disabling compiz effects .or is there any thing i will have to change to fix this problem.plz reply
with thanks......

---

### Post by Paul T. on 2009-04-10
> **ameermawia said:**
> hey i have the same problem with few of my applications like valknut.
i tried disabling all desktop effect by selecting from the visual effects. but still the problem persist.so is there ant other way of disabling compiz effects .or is there any thing i will have to change to fix this problem.plz reply
with thanks......

I found solution on launchpad, see here for more info:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/294076)

---

### Post by ameermawia on 2009-04-10
hey really thanks for the reply .
solution given  worked fine.
for future refrence :
all i needed to do was open the /etc/X11/xorg.conf
then added in the device section ;
Option RenderAccel false

although i dont know wether it was necessary to run this command
dpkg-reconfigure -phigh xserver-xorg
but anyway i ran it  and then rebooted the system and voila problem was solved.

---

