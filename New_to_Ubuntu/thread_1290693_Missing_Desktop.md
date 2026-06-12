---
title: "Missing Desktop"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by GryGhst on 2009-10-13
Hi 
I have recently installed ubuntu as a duel boot and it has been running well, however i installed firestarter and after the install i had 2 broken dependencys, libgnome2-0 and xserver-xorg when i rebooted i gotta a black screen with a mouse, i ran the tests in recovery mode and got a parsing error from dpkg in the status file %  i logged in as root and fixed that using gedit and was able to fix the broken dependencys with ease but this did not fix my desktop prob, i then used apt-get to reinstall xserver-xorg-core and ubuntu-desktop but i still can only  run in a teminal session.
:(

---

### Post by zkriesse on 2009-10-13
My first and the most important question is what OS did you dual boot it with?

---

### Post by GryGhst on 2009-10-13
windows xp is the other os and i had no trouble with the install of ubuntu and it has been running well for a couple of weeks, i can only run in a failsafe terminal when i try a gnome session the mouse is there but on a black screen.
Using ubuntus recovery mode the system reports no errors and package managment also seems happy, i have run out of errors to chase and am stuck.
after reinstalled those packages do i now have to configure something?

---

### Post by nick_nik on 2009-10-13
sounds like something you installed BORKED it!

if you know the name of the package you could run the command in terminal

```
sudo apt-get remove NAMEOFPACKAGE
```

---

### Post by GryGhst on 2009-10-13
> **nick_nik said:**
> sounds like something you installed BORKED it!

if you know the name of the package you could run the command in terminal

```
sudo apt-get remove NAMEOFPACKAGE
```

Ty i have completly removed the offending package, firestarter, and restarted the system then attempted a gnome session no change unfortunately the mouse is present and appears to work but there is just a black screen in place of the desktop

---

