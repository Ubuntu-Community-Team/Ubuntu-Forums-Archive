---
title: "Wireless Connection"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by kell05 on 2007-09-04
Hey, I have a USB wireless card that detects my wireless network however it is unable to connect to the network for some reason unknown to me.  I have disable all encryption incase that was the problem but that didn't work.  I then used a Live CD Backtrack2 and the connection worked with minimal setting up.  I then tried to use the same KDE tools that Backtrack2 uses but this did not work.  Can anyone help?

Thanks Kell05

---

### Post by ubuntu.daemon on 2007-09-04
is it going thru knetworkmanager or network-manager-gome?
and what is the name of the connection? (eth1, ath0, etc.)
post your /etc/network/interfaces too

---

### Post by kell05 on 2007-09-04
Here is the /etc/network/interface 

I know this is wrong since there should be an entry for rtusb I believe


auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


The connection should be going through network-manger-gnome

---

