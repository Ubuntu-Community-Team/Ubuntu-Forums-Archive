---
title: "Minimal Ubuntu"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by GreenDance on 2009-07-26
Hi, This is what I'm running on my minimal ubuntu machine, gnome-core, gdm & firefox, is there anything else important that I am missing?

thank you :popcorn:

---

### Post by Liolikas on 2009-07-26
What you are trying to do?
gdm is not important it just allows nice boot screens instead of text boot and login.
Gnome-minimal is also not important if you want to run Firefox only you can try crazy small WM like Ratpoison more info here:
[http://www.nongnu.org/ratpoison/](http://www.nongnu.org/ratpoison/)

---

### Post by Eisenwinter on 2009-07-26
How is this related to the absolute beginners forum?

---

### Post by GreenDance on 2009-07-26
> **Liolikas said:**
> What you are trying to do?

Save Disk Space, even though my HDD is 80GB :D

> **Liolikas said:**
> What you are trying to do?
gdm is not important it just allows nice boot screens instead of text boot and login.
Gnome-minimal is also not important if you want to run Firefox only you can try crazy small WM like Ratpoison more info here:
[http://www.nongnu.org/ratpoison/](http://www.nongnu.org/ratpoison/)

I forgot to mention I run Evolution Mail & Pidgin IM.

I like how clean-cut gnome is.

---

### Post by SuperSonic4 on 2009-07-26
A music player such as mpd

---

### Post by Liolikas on 2009-07-26
sudo apt-get clean
lsmod and what is not listed remove from /lib/modules (many "drivers" there is you remove too much you get problems)
Be sure to remove old kernels though synaptic.
Remove programs you do not use like gnome-games etc.

---

