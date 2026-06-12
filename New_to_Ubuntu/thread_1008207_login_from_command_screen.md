---
title: "login from command screen"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by maxgt1 on 2008-12-11
after installing new programs a restart is required, but when restarted i get a command line screen which asks for login/password. I enter this and after telling me there is no warranty e.t.c it says dad@something and then a flashing cursor.
what do i do next?
I am very new to this so sorry if this sounds stupid

---

### Post by capn_hector on 2008-12-11
its not stupid  ubuntu normaly starts in gui mode however your x server has stoped running at startup when you log in try typing startx, if that gets the desktop up and running we need to change it to starting with the gui if not then we need to figure out why your xserver is not working.

---

### Post by Sirron on 2008-12-11
Try typing GDM then press enter, see what happens

---

### Post by maxgt1 on 2008-12-11
startx i get fatal server error

GDM i get command not found

gdm i get operation not permitted

I am running ubuntu in windows so that i can still access the net when i have problems like this so i have to reboot to repy thanks for your help

---

### Post by taurus on 2008-12-11
Do you remember what new programs you installed before the reboot?  Sounds like whatever you installed has screwed up X server.  Probably need to reconfigure it again.  After log in with your username and password, try running

```
sudo dpkg-reconfigure xserver-xorg
startx
```
What kind of graphic card do you have anyway?

---

### Post by maxgt1 on 2008-12-11
x server is not installed.
I think maybe reloading ubuntu and then trying to walk before i run could be the easiest route.
Thanks for your help.
Nvidia onboard graphics

---

