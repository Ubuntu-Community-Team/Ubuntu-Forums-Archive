---
title: "Avahi necessary for Xubuntu?"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by impuwat on 2007-08-14
Is Avahi necessary for Xubuntu?   I've been plagued with internittent internet and have read a number of threads about disabling Avahi.  

Jerry

---

### Post by spd106 on 2007-08-14
If you are not using anything related to [Zeroconf]("https://help.ubuntu.com/community/HowToZeroconf") (or Bonjour) then you can disable Avahi. This will remove some features, but it shouldn't break any networking applications.

On Xubuntu, stop the services from the CLI as shown on the above wiki page. i.e. open /etc/default/avahi-daemon and change the value of AVAHI_DAEMON_START to zero.

On Gnome, open System -> Admin -> Network, go to the General tab and untick Automatic Service Discovery.

---

