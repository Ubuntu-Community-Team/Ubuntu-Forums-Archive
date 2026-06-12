---
title: "VPN via ppp0?"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by robbbert on 2007-10-11
Hi, I'm using the Gnome **NetworkManager** (nm-applet), resp. knetworkmanager to establish **VPN** connections when being connected by wire (**eth0**).

Now I'd like to establish VPN connections via **UMTS** card.

The UMTS card itself works fine, it brings up interface **ppp0** and lets one browse the internet.

The problem is, when eth0 gets disconnected, the "my VPN connection" menu entries in (k)NetworkManager become deactivated (resp., disappear), thus not letting me establish VPN connections via UMTS.

Any ideas on how to proceed are greatly appreciated as I've been sticking on this for two days now.

Thanks

-----------------------------
Edit:

For the record, NetworkManager (GNOME and KDE version) only supports connecting via ETH, not PPP. This feature might be planned for version 0.7.

Is there a How-to on doing this by editing config files / script.

Thanks

---

