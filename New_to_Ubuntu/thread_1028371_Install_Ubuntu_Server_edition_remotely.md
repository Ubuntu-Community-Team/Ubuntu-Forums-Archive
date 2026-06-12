---
title: "Install Ubuntu Server edition remotely?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by peterlauri on 2009-01-02
Hi,

Is it possible to install Ubuntu remotely somehow? I have a server in US that now have Fedora C8 installed but want to replace it with Ubuntu Server Edition.

I guess it is not possible as I need to reboot etc :(

/Peter

---

### Post by BenAshton24 on 2009-01-02
If your server is run by a company then why not just give them a call and ask them to do it... if they say no then you could always try saying that perhaps you will be considering a more helpful provider :P

---

### Post by paris_alex on 2009-01-02
wow.. sounds like something crazy.. hehe.. but i'd be interested to know if it's possible... do update if u somehow manage to do it ya...

*** warning: instructions below are purely my imagination on how this would work (but it does not) ***
- create an ubuntu ISO with automated installation scripts
- create a new blank partition on the remote server
- copy the ubuntu ISO to this new partition
- configure grub to read that new ISO partition as the default 'boot partition' during startup
- restart the remote computer...and pray!

anyway, good luck!

---

### Post by paris_alex on 2009-01-02
wow.. sounds like something crazy.. hehe.. but i'd be interested to know if it's possible... do update if u somehow manage to do it ya...

*** warning: instructions below are purely my imagination on how this would work (but it does not) ***
- create an ubuntu ISO with automated installation scripts
- create a new blank partition on the remote server
- copy the ubuntu ISO to this new partition
- configure grub to read that new ISO partition as the default 'boot partition' during startup
- restart the remote computer...and pray!

anyway, good luck!

---

### Post by handydan918 on 2009-01-02
I'm betting this is not so tough. Assuming you have remote access, like ssh, then you should be able to download an iso, (debian netinstall comes to mind)and use a boot-time fromiso option to boot from the .iso.

Seems like you could test the theory on a somewhat less remote server...

---

### Post by albinootje on 2009-01-02
> **peterlauri said:**
> Hi,

Is it possible to install Ubuntu remotely somehow? I have a server in US that now have Fedora C8 installed but want to replace it with Ubuntu Server Edition. 

I read about this approach years ago already, although I didn't try it myself yet :

Here's a howto for Debian :
[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

And, for black humor entertainment, here for FreeBSD :
[http://www.daemonology.net/depenguinator/](http://www.daemonology.net/depenguinator/)

Greetings from a Debian/Ubuntu/FreeBSD fan :)

---

