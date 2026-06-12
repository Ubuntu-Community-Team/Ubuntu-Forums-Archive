---
title: "Network Manager only shows wired connection, even though card is detected"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by Landslide on 2006-12-05
I have a D-Link PCMCIA Wi-fi b/g card with an Atheros chipset that is detected and works fine in Ubuntu. I can use the wifi-radar to scan for networks and then connect to them manually using the System -> Networking menu, but I installed the network-manager applet and got it to work... ONCE. As soon as I rebooted, and ever since, it has only ever showed the wired ethernet connection, and I can't control my wireless NIC with it anymore. Does anyone have any solutions to this problem?

---

### Post by GuruX on 2006-12-06
> **Landslide said:**
> I have a D-Link PCMCIA Wi-fi b/g card with an Atheros chipset that is detected and works fine in Ubuntu. I can use the wifi-radar to scan for networks and then connect to them manually using the System -> Networking menu, but I installed the network-manager applet and got it to work... ONCE. As soon as I rebooted, and ever since, it has only ever showed the wired ethernet connection, and I can't control my wireless NIC with it anymore. Does anyone have any solutions to this problem?

I had almost the same problem. Found the answear in another post. Comment out everyhing except lo in the etc/network/interfaces file.

---

