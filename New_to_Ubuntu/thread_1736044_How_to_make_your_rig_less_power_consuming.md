---
title: "How to make your rig less power consuming?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-04-22
I have this rig which I use as a storage server. I want to make it less power hungry as possible. The hardware part is taken care of, I just want to about all the software changes that can be made :)

---

### Post by NertSkull on 2011-04-22
What version of ubuntu are you running.

I'm not sure what your "storage server" consists of.  But, from my understanding, running ubunte-server edition should be about as good as it comes power wise.  Its a minimal install, but still lets you use it as a server.

I have an old computer that I run a media server on.  I keep my videos, music and databases on.  But there is no graphical component and it works great.  It sounds like that could potentially work well for you.

---

### Post by cyb3r_sn4k3 on 2011-04-22
> **NertSkull said:**
> What version of ubuntu are you running.

I'm not sure what your "storage server" consists of.  But, from my understanding, running ubunte-server edition should be about as good as it comes power wise.  Its a minimal install, but still lets you use it as a server.

I have an old computer that I run a media server on.  I keep my videos, music and databases on.  But there is no graphical component and it works great.  It sounds like that could potentially work well for you.

Thank you,
But I will need an X system for some video surveillance, so what Desktop Manager/Environment should I use or should I go for just a WM?(WM sounds like a bad idea since it dosen't have any power saving options built in).

---

### Post by Bucky Ball on 2011-04-22
sudo apt-get Xfce (the xubuntu desktop environment) from the terminal in the server install. That should work fine. You can, of course, go even more lightweight.

---

### Post by cyb3r_sn4k3 on 2011-04-22
> **Bucky Ball said:**
> sudo apt-get Xfce (the xubuntu desktop environment) from the terminal in the server install. That should work fine. You can, of course, go even more lightweight.

Do u mean a WM or ....

---

### Post by mastablasta on 2011-04-22
if you have wakeon LAN option on your motherboard you could put it to slee when you don't need it. i guess that all depends on how often you are accessing it.

---

He means install a desktop environment (XFCE) that uses less resources to do it's job than GNOME.

Another option is LXDE or probably even lighter and more limited IceWM.

There are a few more X option out there (fluxbox, E11...)

---

### Post by Bucky Ball on 2011-04-22
This is what I mean:

[http://blog.skaelede.hu/archives/2007/04/02/install-xserver-and-xfce4-on-ubuntu-server/](http://blog.skaelede.hu/archives/2007/04/02/install-xserver-and-xfce4-on-ubuntu-server/)

Install the Ubuntu (or Xubuntu) server version. There is no Desktop Environment so from the terminal you are in, making sure you have an ethernet cable attached, of course, follow those instructions. You'll then have a clean desktop to work from and can install other packages as required. 

Have fun and good luck. ;)

* Incidentally, it is always a good idea to use an LTS release for a server. Five years support, more stable and meant for it; 10.04 LTS.

---

### Post by tgalati4 on 2011-04-22
If you are using an Intel machine, then you can install powertop:

sudo apt-get install powertop
powertop

It was designed for laptop use, but it works with most Intel CPU's.

---

