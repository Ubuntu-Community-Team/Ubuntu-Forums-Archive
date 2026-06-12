---
title: "WPA2 natively (no ndiswrapper evilness) supported interfaces?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by kung fu buntu on 2007-05-09
Hi,

The topic says it all.
I would like to know which network interfaces (either PCI or USB) are known to work with WPA2.

Although there is information on which cards work in linux, rarely there is information on if WPA2 or other features are supported.

I've searched:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
[http://www.seattlewireless.net/index.cgi/LinuxDrivers](http://www.seattlewireless.net/index.cgi/LinuxDrivers)
But it's rare to see WPA2 references and the other side of the problem is having the netowork interface in my local stores.


**Do you have a interface card, using linux native drivers, working with WPA2? Please state here the name of the card as well as its chipset.**

Thank you all!


BTW, as for the router, any router works right? (since it's all OS independent on that level) I'm thinking on going with a SMC, just don't know which one yet.

---

### Post by spd106 on 2007-05-09
Most recent cards will do WPA2, avoid the older cards like most prism based ones that are 802.11b only. 

Since you want one that's supported natively I think that's going to be the deciding factor as all cards that were made in approx the last three years will support AES/CCMP, if not in hardware then through wpa_supplicant.

---

### Post by kung fu buntu on 2007-05-10
Any comment on whether to go with a **Ralink** based chipset or an **Atheros** (madwifi driver) chip?

---

### Post by Kobalt on 2007-05-10
I've had pretty good echoes from the Ralink chips, but I don't know about Atheros...

---

