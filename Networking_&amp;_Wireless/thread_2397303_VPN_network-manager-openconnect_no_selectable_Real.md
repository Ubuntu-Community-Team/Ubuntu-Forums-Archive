---
title: "VPN network-manager-openconnect no selectable Realm"
date: 2018-07-27
forum: Networking &amp; Wireless
---

### Post by aldo3 on 2018-07-27
Hello,

I have just installed the package network-manager-openconnect(-gnome  also) on my recently updated Ub 18.04, but when I try to connect to the  VPN (juniper based), at the moment to insert my credentials in the  pop-up window, the Realm button shows the correct options but it seems I  cannot select them. I click on any of them but the only selected (shown  when the drop-down menu closes) is the first one. How can this be  fixed?

  
Bests,

  
Aldo

---

### Post by praseodym on 2018-07-29
Try reinstalling all packages at once:

```
sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-openconnect network-manager-openconnect-gnome
```
Check also the necessary mtu-value and add it manually (instead of "Automatic") into the respective profile

---

### Post by aldo3 on 2018-07-29
Hi, I did it (and restarted) but nothing changed.

In addition, in the syslog I could trace this message:

gnome-shell[1380]: JS ERROR: TypeError: item is undefined#012setActiveConnections/<@resource:///org/gnome/shell/ui/status/network.js:1518:17#012setActiveConnections@resource:///org/gnome/shell/ui/status/network.js:1515:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_syncVpnConnections@resource:///org/gnome/shell/ui/status/network.js:1853:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22

---

