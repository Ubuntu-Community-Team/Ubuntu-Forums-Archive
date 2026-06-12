---
title: "vbox issues"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Griffi09 on 2008-11-24
looking for some new directions to go.  I want a bridged connection from vbox and ubuntu.  I installed the bridge utils and have followed the directions on.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)  

but i get stuck, when i alter the /etc/network/interface file.
to 
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
   bridge_ports eth0 vbox0

auto lo
iface lo inet loopback

saves fine, but when i restart the networking servcie it fails
and states "cannot read interface file"

any idea's on where i've gone wrong?

---

