---
title: "RALINK Turbo pcmcia"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by brianw0667 on 2007-03-01
I have a ralink turbo pcmcia card.  It shows under iwconfig as wlan0 and wmaster0.  I can't get the networking tool under system to get an ip address (it doesn't even show activity on the indicator).  When I use wifi-radar it sees my netgear travel router which I have set to 192.168.1.1 and does dhcp.  I turned off security on the router.  wifi-radar attempts to get an IP address and there is activity shown on the indicator but no IP is obtained.  any ideas?

---

### Post by brianw0667 on 2007-03-04
Found out what was tripping me up.  I had followed directions from other posts I could not get my wireless card working.  I compiled the software from ralink and installed it but when I did an iwconfig it would report that ra0 had no wireless extensions and I could not get any wireless card to show in the network manager under the system menu.  I tried setting the ip using ifconfig and ping the wireless router (which I had configured to accept pings) but kept getting an error that the network was unreachable.  I uninstalled the ralink software and got the wan devices back.  Finally I reinstalled the ralink stuff and after a reboot got the wireless car showing in the network manager again.  After unchecking and then rechecking the wireless card I got an automatic IP assigned via DHCP.  I noticed that the IP was assigned by my FREESCO router not by my wireless router even though my wireless router I have set to 192.168.1.1 and my freesco router is 192.168.0.1.  Once I realized what was going on I turned DHCP off on my wireless router and just used my freesco box as the sole DHCP server.

Thanks to all the other posts I was able to work this out.

---

