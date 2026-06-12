---
title: "Keep Losing Wireless Card Setup"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2008-07-14
Every time I reboot my system, I have to re-establish the wireless card's connection to the network.  I have to type:

> sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

I got this from one of the Sticky Posts above.  Does anyone know why I have to do this?  Can I create a script to do it?  If so, how?

Thanks.

---

