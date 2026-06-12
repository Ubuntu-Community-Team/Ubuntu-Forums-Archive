---
title: "DHCP not found with wpa_supplicant"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by The Mad Scientist on 2005-10-31
I am using D-Link wireless products to network my home computers.  The router is a DI-624, the NICs are DWL-G520s.  These work well with Windows systems.  If I set up the system in Ubuntu with no security but MAC filtering, everything works fine.  When I try to use wpa_supplicant to enable WPA-PSK, the card connects, but cannot find a DHCP server.  The output of wpa_supplicant shows the connection was established and the router status window confirms it is connected.  However, it tries several times at different intervals to get a DHCP server, then gives up.  The output of ifconfig at this point shows the IP address to be the MAC address.  I have tried all the methods on the WIKI page to set up wpa_supplicant on versions 5.03 and 5.10 of Ubuntu, with the same result each time.  Any ideas?

---

### Post by The Mad Scientist on 2005-10-31
Pseudo-false alarm.  After perusing this forum some more, I found that if you disable and re-enable your connection using the network manager, it should work.  It did.  Problem solved.

---

