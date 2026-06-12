---
title: "VPN Connections Don't Show up in NetworkManager"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by T_W on 2008-07-25
A problem recently developed.  It may be related to the 8.04.1 upgrade.

I have 2 VPN connections defined in Network Manager.  I can see them if I select "VPN Connections/Configure VPN..." on the Network Manager context menu.

However these VPN connection **do not show up** on the VPN Connections menu itself, so I cannot activate them.

Normally the menu looks like:

VPN Connection 1
VPN Connection 2
----------------
Configure VPN...
Disconnect VPN...

And I would click on "VPN Connection 1" to activate.

The problem is the menu items for the VPN connections aren't displaying so I cannot activate the VPN.

Any ideas?  I tried restarting NetworkManager, NetworkManagerDispatcher, and nm-applet, but no change.

---

### Post by T_W on 2008-07-31
Bump.. anyone?

VPN is totally down for me and I cannot get it running again.

---

### Post by T_W on 2008-07-31
Bug and workaround documented here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/200304](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/200304)

Basically workaround is to manually:

$ sudo /etc/init.d/dbus restart
$ nm-applet &


Man, these kind of regressions are damn annoying.

---

### Post by lime3k on 2011-05-25
I know bumping isn't appreciated but I've just had this problem in 11.04 and this really helped out! Thanks

---

### Post by T_W on 2011-05-25
You're welcome.  I'm glad my notes could help someone else out.

---

