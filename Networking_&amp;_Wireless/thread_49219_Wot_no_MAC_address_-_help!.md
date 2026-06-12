---
title: "Wot no MAC address - help!"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by graza on 2005-07-15
Ok,  so I installed kubuntu fine, on a dell gx110. I disabled the onboard LAN, but have added an extra PCI LAN card. This appears to be working (lights up where the network cable plugs in). 
but ifconfig or  sudo ifconfig don't display the mac address
lspci displays the card as 3com 3c905 100base tx [boomerang]

The card is disabled in the network settings, and I can't enable it

I need the MAC address so that the work network can be setup to allow the computer to work, so at the moment the computer is not connected to an active LAN (although it is plugged in, the network won't recognise it) - would this effect the network card, preventing it from being enabled?

Thanks for any advice

Graza


IFconfig:

link encap: local loopback
inet addr 127.0.0.1 mask 255.0.0.0
Up loopack running
etc

---

