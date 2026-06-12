---
title: "Net devices connect, but it's so slow it's useless"
date: 2005-11-01
forum: Networking &amp; Wireless
---

### Post by Papasasha on 2005-11-01
I just installed the 5.10 version.  I am having trouble with the net connection.  I use the Centrino 802.11b/g device.

The wlan device seems to function, and can connect to the router.  But the data flow is so slow it may as well not exist.

I've noted the following:

- The router uses DHCP
- all is well under Windows, or even Kanotix
- iwconfig can configure the device
- iwlist successfully scans for access points
- either the Gnome tool or iwconfig/ifconfig/dhclient connects the device with the router
- I can connect to the router
- I have no trouble pinging google, yahoo, router, other websites with low ping score
- Via Firefox it successfully resolves mail.google.com from [www.gmail.com](www.gmail.com), but that's as far as it gets
- apt-get update yields some data transfer, but very slow
- there is no firewall in effect (ipchains is not there, iptables is all ACCEPT)
- ipw2200 module is running
- /etc/resolv.conf shows the correct DNS
- I have the same trouble if I directly connect the router to the ethernet port

Any assistance is much appreciated -- thanks in advance.

---

### Post by teaker1s on 2005-11-01
ipv6 seems to be a major problem and dns resolution is crap unless you tell ubuntu and router the dns address of your ip

---

