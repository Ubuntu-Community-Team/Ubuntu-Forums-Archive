---
title: "Replace KDE network manager"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by rkakkar on 2010-09-23
unfortunately KDE network manager and I have never seemed to have gotten along .. is it possible for me to replace it with gnome's network manager? if so, how can I do it without being left in between with neither? :p :D

---

### Post by khelben1979 on 2010-09-23
I would recommend [Wicd]("http://en.wikipedia.org/wiki/Wicd") instead. What do you think?

---

### Post by mprice on 2010-09-23
Here is some instructions for you if you want to use gnome-network-manager instead of knetwork-manager.

[http://digitizor.com/2010/05/21/how-to-replace-the-kde-network-manager-with-the-gnome-network-manager-in-ubuntu/]("http://digitizor.com/2010/05/21/how-to-replace-the-kde-network-manager-with-the-gnome-network-manager-in-ubuntu/")

---

### Post by beew on 2010-09-23
> **khelben1979 said:**
> I would recommend [Wicd]("http://en.wikipedia.org/wiki/Wicd") instead. What do you think?

I don't know how wicd performs on a KDE desktop, but I have tried it on gnome and am less than impressed.

It connected to the network on start up, but then it would lose it after about 20 minutes or so and it would take it forever to reestablish connection if it did it at all, otherwise you would have to reboot. Upon reboot it connected immediately but then the same thing happened again. This appears to be a known bug which has existed for years based on some google search as well as reading posts on the (old) wicd forum.

I have experienced no problem with gnome network manager, everything works perfectly and I have tried different machines with different cards. I was only trying to experiment with wicd because I heard many good things about it, I am a bit disappointed.

P.S. Wireless never works on KDE from my admittedly limited experience. Tried kubuntu, KDE versions of Fedora and Debian on multiple machines, none worked. On the other hand, in the gnome version wireless always worked out of the box (ok, in one case I have to install the broadcom drivers but wireless worked immediately after that)

---

### Post by sandyd on 2010-09-23
have you tried plasma-widget-networkmanagement?
The one in KDE 4.5 I mean.

---

### Post by khelben1979 on 2010-09-24
> **beew said:**
> I don't know how wicd performs on a KDE desktop, but I have tried it on gnome and am less than impressed.

It connected to the network on start up, but then it would lose it after about 20 minutes or so and it would take it forever to reestablish connection if it did it at all, otherwise you would have to reboot. 

I made a google search myself and I read that for some it works great and for others it don't. Maybe it's badly configured?

---

### Post by rkakkar on 2010-09-26
> **mprice said:**
> Here is some instructions for you if you want to use gnome-network-manager instead of knetwork-manager.

[http://digitizor.com/2010/05/21/how-to-replace-the-kde-network-manager-with-the-gnome-network-manager-in-ubuntu/]("http://digitizor.com/2010/05/21/how-to-replace-the-kde-network-manager-with-the-gnome-network-manager-in-ubuntu/")

This worked! Thanks :)

---

