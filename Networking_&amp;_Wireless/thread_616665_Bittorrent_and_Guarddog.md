---
title: "Bittorrent and Guarddog"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by benn333 on 2007-11-18
Azureus works fine with Guarddog disabled, but the bittorrent tracker can't get through with Guarddog enabled. Same thing happens with KTorrent.

I've configured both apps to use port 50000 for TCP and UDP traffic and set up my router to forward the traffic. In Guarddog I've created new User Defined Protocols for the port and permitted the protocol on both the Internet and Local Defined Network Zones.

Still the tracker connection times out in both apps, which prevents torrents from starting. If I disable the firewall via Guarddog, the tracker connects and the torrent starts. If I reenable Guarddog the download continues, but the tracker continues to fail on future connections.

Any ideas what's going on here? Everything seems in order, but the traffic keeps getting blocked by Guarddog.

---

