---
title: "Detect But Not Connect With wlassistant"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Rhey on 2006-12-03
My wireless card (some toshiba built-in using the atheros chipset) works fine. When I start up Ubuntu the wireless driver loads fine and a wireless network is found and connected to. However, if i try to change wireless networks with wireless assistant (or kwifi) I am no longer able to connect. Even if I attempt to connect to the first network that was connected to when started-up, it cannot connect. Iwlist scans and I can change essids/ap/wep/... with iwconfig, but still no connection. Help would be greatly appreciated, b/c the first network connected to is my neighebors :( .

---

### Post by stupidkid on 2006-12-03
You probably need to use dhcp to get the IP. There are a couple commands

pump -i <interface>
dhcpcd <interface>
dhcpclient <interface> (I'm not 100% sure about the spelling)

You can probably just type dh and then press tab to see all the dhcp commands.

---

