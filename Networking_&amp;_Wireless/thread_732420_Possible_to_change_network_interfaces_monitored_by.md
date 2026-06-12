---
title: "Possible to change network interfaces monitored by gnome-system-monitor?"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by dmonner on 2008-03-22
I recently installed a wireless card that uses the madwifi driver, and since then have been seeing a constant stream of data from gnome-system-monitor and multiload-applet-2 (gnome-system-monitor's associated panel applet).

The installation of this card added two network interfaces, ath0 and wifi0. As I understand it, ath0 is a virtual interface created by the madwifi driver and is the one that actually gets an IP address, whereas wifi0 is the "real" interface. Anyway, the stream of data is coming from / going to wifi0, and from what I've read it's harmless local overhead traffic that for some reason doesn't get accounted to ath0. 

Anyway, seeing that traffic in gnome-system-monitor is disconcerting when I'm not actually using the network, so I'd like to remove wifi0 from the list of interfaces it monitors. Does anyone know if there is a way to configure gnome-system-monitor or multiload-applet-2 to no longer monitor an interface?

In case it helps, I have a Kubuntu machine with an identical wireless card, which also has both the ath0 and wifi0 interfaces, and the same amount of constant traffic on wifi0. However, KDE's System Guard and the associated panel applet do not show this traffic, since I can select exactly the interfaces I would like to monitor. So it's possible to do this apparently, at least over on the KDE end.

---

