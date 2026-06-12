---
title: "Wireless issue"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by jdglover on 2009-09-27
Hi,

I'm having an issue with a wireless card that will not connect.  I'm using Jaunty on an older HP Pavillion PC with a wireless PCI card.  I've tried two different cards, and SMC card and an Intellinet card.  Ubuntu recognizes both cards and my wireless network is detected in the network manager but the card will not connect to the router. Both cards hang when trying to connect.  The router is running WPA/WPA2 security and this seems to be where it hangs, the passphrase is never accepted and the connection times out.  Both cards are supposed to support WPA/WPA2 security.  I'd prefer to keep the WPA security enabled. Any suggestions would be welcome. TIA,

John

---

### Post by nhasian on 2009-09-28
first i would try (just for testing purposes) disabling the security on your router and seeing if you can connect to the open network.  if that works, try wpa1 before wpa2.  if it doesnt like either wpa1 or wpa2, then you can fall back to wep.

---

