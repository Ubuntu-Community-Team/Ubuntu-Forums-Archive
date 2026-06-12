---
title: "no DNS with wlan"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by sfrank on 2008-05-28
Hi,

I have a very strange problem with my wlan setup on my hardy system that by now has completely baffled me and I hope that one of you is kind and knowledgeable enough to shed some light on the situation.

The network is working flawlessly when accessing the net through an Ethernet cable and the on-board network adapter.
I'm now trying to get wlan access on my system using a Linksys WUSB54GC USB-WLAN-Adapter and the rt73usb driver. Everything looks OK:

- I get an IP address from my Netgear DSL-router
- the gateway/routing table is setup correctly
- I can ping and access every local and outside server and nameserver

The only thing that does not work is DNS-lookup but only when I am on wireless. The resolv.conf is the same as in the working eth0 case where it works flawlessly. As a test I have added the openDNS nameservers but that didn't help. The last thing I tried was disabling IPv6 but still no change in the not working DNS-lookup behavior (the DNS servers are all reachable via ping).

Any ideas?

Thank you very much in advance.

Kind regards,
Stephan

---

