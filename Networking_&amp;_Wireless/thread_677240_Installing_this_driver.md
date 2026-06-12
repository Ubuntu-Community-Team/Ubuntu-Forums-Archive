---
title: "Installing this driver"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by leafhound on 2008-01-24
I have a USB modem and driver

When i run Gnome it is easy to install, but i'm trying to run it on KDE

so far
I have managed to extract the firmware files and copy them to the appropriate location.

the i'm stuck on is configuring the connection as the instructions are for Gnome


```
gksudo gedit /etc/ppp/peers/ueagle-atm

gksudo gedit /etc/ppp/chap-secrets

gksudo gedit /etc/ppp/pap-secrets

gksudo gedit /etc/init.d/modem-startup
```

I did kdesudo kwrite and in each command kwrite opened up and i edited the files, it is Kubuntu

```
john@kubuntu:~$ kdesudo kwrite /etc/ppp/peers/ueagle-atm
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$ kdesudo kwrite /etc/ppp/chap-secrets
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$ kdesudo kwrite /etc/ppp/peers/ueagle-atm
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$ kdesudo kwrite /etc/ppp/pap-secrets
Error: "/var/tmp/kdecache-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/kde-john" is owned by uid 1000 instead of uid 0.

Error: "/tmp/ksocket-john" is owned by uid 1000 instead of uid 0.

john@kubuntu:~$
```

---

