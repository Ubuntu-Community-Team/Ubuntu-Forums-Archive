---
title: "Remove network-manager from wired computer"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by fwheeler_1 on 2007-08-15
Hi-  I am using Kubuntu 7.04 on a desktop computer with a wired ethernet connection.  As usual, Kubuntu installs network-manager and knetworkmanager by default.  Networking is functioning fine, but the computer has limited RAM, so I am trying to squeeze every Mb out of it.

If I remove network-manager and knetworkmanager (sudo apt-get remove network-manager knetworkmanager), will I still maintain my wired ethernet connection and be able to change network settings (if needed) through the KDE control panel?  Or do I need to replace the two programs with something else in order to keep things functioning?  Thanks in advance, FW

---

### Post by noob12 on 2007-08-15
I don't know about Kubuntu, but in the regular (gnome) edition you would still retain the network-admin gui which is part of gnome-system-tools (and you get to this via the panel menus System | Administration | Network).

You can always just edit /etc/network/interfaces directly, which is what I prefer to do anyway.

---

