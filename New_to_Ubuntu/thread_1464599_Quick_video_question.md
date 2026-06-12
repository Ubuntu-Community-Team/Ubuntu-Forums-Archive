---
title: "Quick video question"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by mesmith on 2010-04-28
Running Xubuntu 10.04.  I noticed while in synaptic that intel video drivers have been installed (I have 82865G), but also a video driver call "nouveau" which is experimental.  Why both, and is their a terminal command that will tell me which my system is using?  Would I want to use nouveau?  How would I switch if their were any advantages?

---

### Post by quadproc on 2010-04-28
> **mesmith said:**
> Running Xubuntu 10.04.  I noticed while in synaptic that intel video drivers have been installed (I have 82865G), but also a video driver call "nouveau" which is experimental.  Why both, and is their a terminal command that will tell me which my system is using?  Would I want to use nouveau?  How would I switch if their were any advantages?
If your system is using the xorg.conf file then you can run
```
grep "river" < /etc/X11/xorg.conf
```
and look for a non-commented line.  The driver name will be in quotes.

I hadn't heard of "nouveau" so I don't know its claims to fame.

Changing drivers is a moderate amount of work.  You have to uninstall the old driver and then install the new one.  Any configuration that the new driver needs will have to be set up.  Of course, all of this involves stopping and restarting the X server, and perhaps also requires rebooting.  Some drivers get really tangled up with the kernel and you'll have to use a reboot to get them to behave properly.

quadproc

---

### Post by Sef on 2010-04-28
> Would I want to use nouveau?  Nouveau is an open source driver for NVidia cards.  Currently, it only supports 2-D.

Update: [Nouveau Wiki]("http://nouveau.freedesktop.org/wiki/")

---

### Post by cgroza on 2010-04-28
Nouveau will be only used if a Nvidia card is detected, just ignore it.

---

