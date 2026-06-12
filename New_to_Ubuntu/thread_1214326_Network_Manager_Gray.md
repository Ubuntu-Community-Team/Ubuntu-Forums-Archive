---
title: "Network Manager Gray"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-07-15
I had this issue in Intrepid and I thought it would be gone in Jaunty but, it is still here. For some odd reason the network manager icon in the system tray is always gray (I'm pretty sure it should have blue bars indicating signal strength). Is there anyway to fix this?

I posted a screenshot as well to show what I mean.

---

### Post by ronocdh on 2009-07-19
Have you tried right-clicking on it and making sure that it's pointed to the right device (i.e. your wireless card)? Are you connecting via a wireless card to the internet or are you using an ethernet cable?

I think the problem is that the system tray widget just isn't too sure which device it should be referencing.

Familiarize yourself with **iwconfig** (read the man page by typing **man iwconfig** in the terminal) and then once you're sure the wireless card is working properly and you can indeed access all the data you want the widget to display, focus on the widget.

---

