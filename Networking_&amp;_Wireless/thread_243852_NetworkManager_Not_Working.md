---
title: "NetworkManager Not Working"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by pak33m on 2006-08-25
Belkin G Wireless Card
BLKWGN.SYS Driver

I've installed NetworkManager via apt-get install NetworkManager and I get the following:

(nm-applet:6287): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by ciscosurfer on 2006-08-25
I would first make sure all dependencies are resolved for Network Manager....try uninstalling it via apt-get, then reinstalling it via aptitude```
sudo aptitude install network-manager-gnome
OR (if you use KDE)
sudo aptitude install knetworkmanager
```and see if that solves the problem (you may still need follow up with the link I give below).

Do you have nm-applet setup to run at startup via your sessions panel?  If so, and you don't see the icon, I would suggest reading this page ([https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/35662](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/35662)) that suggests a fix (basically you reset your icon cache)

---

