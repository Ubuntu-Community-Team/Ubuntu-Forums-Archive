---
title: "ubuntu vpn configuration fails"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by kermy on 2007-07-23
I have installed network-manager-vpnc on Ubuntu *Feisty*. This enables a vpn submenu with the options to configure or disconnect a vpn network connection. When I choose the configure option nothing happens. I've tried to run network-manager on the console with 'sudo NetworkManager --no-daemon', but I get no error message to explain the unresponsiveness.

Might it be the difference in version number?

network-manager                           0.6.5-0ubuntu7
network-manager-vpnc                      0.6.4svn2422-0ubuntu3

---

### Post by kermy on 2007-07-23
The program for vpn settings was moved from network-manager-gnome to the main package network-manager hidden in some lib directory. When I add vpn connections with this program run from the console they appear fine in nm-applet and also work as they should.

/usr/lib/network-manager/nm-vpn-properties

Which is probably why nm-applet can't find it... Should I post a bug report?

---

