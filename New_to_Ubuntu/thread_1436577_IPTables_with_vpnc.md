---
title: "IPTables with vpnc"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by lumitoro on 2010-03-22
(Laptop with lots of roaming) I'm trying to setup my firewall(using fwbuilder as a front-end in kubuntu).
Network-Manager was not connecting to my university's network(wpa2-Enterprise, TTLS, PAP) so i went the old way, using "/etc/network/interfaces" with wpa-roam configured for my wlan0(wireless NIC, as you have guessed already). Everything works fine, and I even managed to vpnc my way into the university LAN automatically on boot flawlessly, but now I'm trying to enable my firewall, and making it to accept a few services through this vpn(tun0). Everything gets BLOCKED...
Just a simple example script would be nice, I'll make it from there.


P.S.: The attachment shows my latest tryout...thanks for the reply (if you are replying :D)

P.S. 2: Do I need to forward wlan0 traffic to tun0, or am i just clueless????

---

