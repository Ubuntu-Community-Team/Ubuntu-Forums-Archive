---
title: "Turning openvpn on and off..."
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by ragtag on 2008-11-07
Hi,

I've managed to set up openvpn on my home machine to connect to work. I've disabled openvpn at boot, but would like a quick way to enable and disable it.

Currently I have a two step process.

1. Run:  sudo /etc/init.d openvpn start
2. Switch Location in network settings to work.

And the reverse to stop it.

openvpn seems to override Network Settings, so disabling tun0 in Network Settings doesn't really have any effect as far as I can tell.

 Any suggestions?

  ragtag


p.s. I'm using static IP at home and dynamic through the VPN.

---

