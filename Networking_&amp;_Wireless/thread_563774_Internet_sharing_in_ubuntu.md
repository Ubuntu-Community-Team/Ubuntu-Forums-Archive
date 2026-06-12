---
title: "Internet sharing in ubuntu"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by ayet on 2007-09-30
in windows you can share the internet connection of a single pc to many on the network just use the IP address of the host pc as a gateway, can this be done in ubuntu? I need this to share my second pc to have internet.

---

### Post by spd106 on 2007-09-30
There is no specific tool in the default Ubuntu (Gnome), so if you want an easy life I recommend that you install [Firestarter]("https://help.ubuntu.com/community/Firestarter").

Otherwise you've got to set-up Dhcpmasq, IPmasq and configure IPTables for NAT manually, which isn't trivial, though there are a few guides in the wiki e.g. [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

