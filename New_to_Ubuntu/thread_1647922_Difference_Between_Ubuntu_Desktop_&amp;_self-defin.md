---
title: "Difference Between Ubuntu Desktop &amp; self-defined X Session"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by tanmoykrthakur on 2010-12-18
What is the Difference Between Ubuntu Desktop & self-defined X Session & what is preferable

---

### Post by cariboo on 2010-12-18
Depending on your setup, /etc/X11/xorg.conf is the file the sets up the desktop resolution, color depth and more. It is used no matter what desktop environment you are using. 

The only real difference is that the default desktop allows you to set things up with a couple of clicks, where as if you set things up manually, you have to download the drivers and edit /etc/X11/xorg.conf manually.

---

