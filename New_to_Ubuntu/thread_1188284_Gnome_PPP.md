---
title: "Gnome PPP"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Linguist99 on 2009-06-15
I have an Ubuntu 9.04 on my computer and I want to setup a dial-up connection via my 56k modem. But there is no Gnome PPP in it, and when I want to install gnome ppp packages it says that an internet connection is required, but if I don't have a dialer program how can I connect to the internet and install packages? Are there ways of installing packages without connecting to the internet?

---

### Post by tomszyszko on 2009-06-15
It really should have been part of network manager :(

---

### Post by tomszyszko on 2009-06-15
> **Linguist99 said:**
> I have an Ubuntu 9.04 on my computer and I want to setup a dial-up connection via my 56k modem. But there is no Gnome PPP in it, and when I want to install gnome ppp packages it says that an internet connection is required, but if I don't have a dialer program how can I connect to the internet and install packages? Are there ways of installing packages without connecting to the internet?

You can install packages from cd, just burn the .deb files

---

### Post by lkraemer on 2009-06-15
Here you go.
[http://ubuntuforums.org/showthread.php?t=1170782&page=3](http://ubuntuforums.org/showthread.php?t=1170782&page=3)

Once you have the Deb's downloaded and copied to /var/cache/apt/archives/
you can just use Synaptic to install wvdial.

and the guide is at:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Posting #4

lkraemer

---

### Post by SOULRiDER on 2009-06-15
Remember to also copy all of the dependencies. Also, you could check out AptOnCD

---

