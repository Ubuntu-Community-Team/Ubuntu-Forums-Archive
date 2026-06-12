---
title: "Static IP setup"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by rob_w on 2007-06-03
I know that this must surely have been covered a thousand times, but searching the forums gives me a thousand results, and the wiki has nothing, so:

How do I set up a static IP address for my computer on a wireless home network? I need to do it so that I can tell my router to use port forwarding for BitTorrent. I'm using Wicd to connect because I have an rt2500, and a Netgear DG834 router. I see the Static IP options in Wicd, but I don't know how to find out what to use for Netmask and Gateway.

Any help would be appreciated.

---

### Post by Jussi Kukkonen on 2007-06-03
gateway is your router address (often 192.168.0.1), netmask is normally 255.255.255.0

I do not know wicd, but normally you'd edit /etc/network/interfaces or use the graphical settings in System / Administration / Network.

---

