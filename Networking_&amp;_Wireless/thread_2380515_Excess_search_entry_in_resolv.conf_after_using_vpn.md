---
title: "Excess search entry in resolv.conf after using vpn"
date: 2017-12-18
forum: Networking &amp; Wireless
---

### Post by pkrause1980 on 2017-12-18
I'm using Ubuntu-mate 17.10 desktop edition and have a problem using the network manager with an openconnect vpn.

If I connect to a vpn (lets call it vpn.domain.com) via the openconnect plugin, after disconnection there is an excess "domain.com" in the "search" line of /etc/resolv.conf. Before connecting to the vpn it is not there.
As far as I can tell resolv.conf is only modified by the network manager and systemd-resolved.

I'm not sure if this is a bug or somehow a misconfiguration. However I made no special configuration apart from adding the vpn in the graphical network manager interface.
Can somebody help me? Thanks!

---

