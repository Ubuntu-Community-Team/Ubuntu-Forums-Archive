---
title: "something's wrong"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by ludwigvan1988 on 2010-07-27
hello,
I have a radeon x300 video card and run ubuntu 10.04.
After an nvidia driver was installed, the x server (i think) would crash after somebody logged in. I logged in from the ctrl+alt+F1 terminal and was able to remove the nvidia software, but that didn't change anything. I removed, reinstalled, and reconfigured xorg, but that didn't do anything. 

Is there a way to see if the default video driver is still working? 

Why won't the desktop start?

---

### Post by 3rdalbum on 2010-07-27
```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

See if that works - it deletes the Xorg configuration file, which in its current state probably has references to the Nvidia driver you erroneously installed.

---

### Post by muteXe on 2010-07-27
Great thread title.

---

