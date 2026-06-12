---
title: "Monitoring DNS queries from LAN"
date: 2016-12-17
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2016-12-17
So I am working on a side project where I want to monitor for DNS queries (udp/53) from remote LAN devices from my client PC. To do this, I understand I needed airmon-ng to run the WLAN NIC in monitor mode, fire up wireshark and start grabbing packets. Unfortunately, even though airmon says that mon0 is in monitor mode, wireshark doesn't see it that way.


I also assume at this point it's not going to capture DNS traffic on the wired LAN, but only wireless.


The goal of this project is to monitor the network internally from the end point, rather than going out to OpenDNS to see the query logs or monitoring from the router/DNSserver directly.


Thanks UF!

---

### Post by SeijiSensei on 2016-12-17
You can log the requests with iptables if you don't need to see the packet contents:

```
sudo iptables -I INPUT -p udp --dport 53 -j LOG
```

---

### Post by 98cwitr on 2016-12-19
> **SeijiSensei said:**
> You can log the requests with iptables if you don't need to see the packet contents:

```
sudo iptables -I INPUT -p udp --dport 53 -j LOG
```

But that would have to be run from the source pc (making the request)...this would need to be captured by a device for which the packet is not intended.

---

