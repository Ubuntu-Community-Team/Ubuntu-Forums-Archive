---
title: "dhclient getting back DHCPNAK from Netgear Nighthawk router since upgrade to Artful"
date: 2018-02-03
forum: Networking &amp; Wireless
---

### Post by jik2 on 2018-02-03
Since I upgraded my desktop computer to Ubuntu 17.10 (Artful Aardvark), it is able to obtain an IP address initially from my Netgear router, but then when it tries to renew the address the router sends back DHCPNAK.

I've checked the router logs and there's no explanation in the logs of why it's sending back the DHCPNAK; the event isn't even logged at all (way to go, Netgear!).

Note that my desktop has a reserved IP address in the router configuration (so, yes, I could just configure the network interface on my desktop with a static IP, which is what I'm doing for the time being, but I'd rather not), so that could be relevant, but there are a number of other machines on my network with reserved IPs, and none of them are having this problem.

Or, for all I know, perhaps the other machines are having this problem but the DHCP client they're using is automatically generating a new request -- rather than a renewal -- when the initial attempt to renew fails, and dhclient on my Ubuntu desktop isn't doing that.

Any thoughts on what might be causing this or how to fix it other than hard-coding the IP address in my desktop's network config?

---

