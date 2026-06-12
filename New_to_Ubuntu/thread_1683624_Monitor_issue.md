---
title: "Monitor issue"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by crowhill on 2011-02-07
Hi there!

Today, I got myself an ACER P216H monitor to attach to my laptop. When I fired it up and switched to it by hitting Fn+CRT/LCD I got to see stuff on the new monitor. However, the resolution was horrible so that I went to the Nvidia GUI for monitors. There, I switched to the advertised (on the box) 1920x1080. That worked but the problem is now that, somehow, Ubuntu or whatever doesn't know where the center of the screen is. Take a look at the attached pic. When I open a terminal window, it's not appearing in the center. Conky is also not where it should be, namely, at the right boundary. Any ideas as to what I have to do?

---

### Post by patrick281981 on 2011-02-09
Hi,

What I can suggest is to make a laptop screen as a primary ..
change the resolution screen and if that won't help check the xorg.conf X window configuration file in the /etc/X11/xorg.conf ..
and look for "Monitor 1" more about xorg file please read on [http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)

Regards.

---

### Post by crowhill on 2011-02-09
thx for the reply. i think, i completely messed up my settings. Now, neither the external screen nor the laptop screen itself look halfway decent!

help please!

---

