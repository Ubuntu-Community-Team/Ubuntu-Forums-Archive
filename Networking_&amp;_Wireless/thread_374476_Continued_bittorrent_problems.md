---
title: "Continued bittorrent problems"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by fishe on 2007-03-02
I'm running Edgy and since initial installation I've had constantly poor bittorrent performance - generally around 4 to 12k/s on all torrents, from ones with a few seeds to others with thousands. Under Windows on the same box I get normal/decent speeds over 100k/s.

I've already tried the following from others with problems on here:
[LIST]
[*]disabling ipv6
[*]using many different applications - the default bittorrent downloader, ktorrent, azuras, deluge, qbittorrent - all of them perform the same
[*]I've triple checked the correct ports are open on the router and by all accounts they test OK as open.
[*]I've tried with and without firestarter - currently using it, with the ports open
[*]All programs I use generally say my network health is OK
[*]I've tried enabling and disabling DHT
[/LIST]

The only thing I can think of which may be impacting the performance is some sort of system network setting, or setting on my Wireless NIC. The poor performance may be related to the application connecting to a small amount of seeds/peers - so maybe some type of maximum TCP connections setting gone wrong?

Any ideas guys? thanks

---

### Post by Prometheus.172214 on 2007-03-02
Does the NAT show Green? If it does not show green, this is a port forwarding issue. If it shows green, you might give uPnP configuration a try.

---

### Post by fishe on 2007-03-03
> **Prometheus.172214 said:**
> Does the NAT show Green? If it does not show green, this is a port forwarding issue. If it shows green, you might give uPnP configuration a try.

What exactly do you mean by "the NAT"? The health monitoring some apps have? :) If yes, then yes this is always green/ok/healthy.

Regarding uPnP, I've tried to both on and off, on both the router and the application of course. Same issues...

---

