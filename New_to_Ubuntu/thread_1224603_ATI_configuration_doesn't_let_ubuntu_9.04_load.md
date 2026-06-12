---
title: "ATI configuration doesn't let ubuntu 9.04 load"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by agst on 2009-07-27
Hi

I reinstalled ubuntu 9.04 because it wouldn't finish loading after I installed some apps.  It was working fine and I was installing those apps (one by one this time...) and the problem appeared when I installed the ATI configuration application.

I have a Dell Inspiron 6400 with Win 7 dual boot.  The video card is ATI Radeon X1400

How do I uninstall or remove that from the hard drive while I'm running on a live CD?  I already tried safe mode and the video fixing option at the bottom and it still doesn't work.

please help!!  I don't want to reinstall everything AGAIN!
:(

EDIT: What I installed was actually ATI Catalyst Control Center and my video card is actually an ATI Mobility Radeon X1400

---

### Post by Michael.Godawski on 2009-07-27
Enter the Root Shell (Recovery Mode during boot)
Then try:
```
apt-get remove xorg-driver-fglrx
```

worked for me today ;)

Can you tell us what ATI configuration application you installed?

---

