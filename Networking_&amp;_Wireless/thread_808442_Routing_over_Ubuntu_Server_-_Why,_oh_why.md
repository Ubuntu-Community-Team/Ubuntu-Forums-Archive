---
title: "Routing over Ubuntu Server - Why, oh why?"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by IOWAHC on 2008-05-26
I set up a LAN which looks like:
[Internet(VPN)]
|
[Switch]----[Laptop 1]
|
|   172.16.0.0 / 16
|
[Server]
|
|   192.168.3.0 / 24
|
[Switch]----[Workstation]
|
|
[Laptop 2]

Server (Gutsy 7.10)
Laptops (Hardy 8.04)
Workstation (Vista Business)

I activated ip_forwarding, NAT and iptable rules after some tutorials here.
Everything works fine, I can connect from every PC/Laptop to the Internet, only problem is:

When I try to connect from Laptop 2, or Workstation to certain sites (for example [http://openstreetmap.org](http://openstreetmap.org)) he can't establish the connection, Laptop 1 and the server connect without problems.

Every other WebURI is working except some i Really need,
(myspace.com, osm.org, one.at)

Hope someone knows the answer out there,

Greets Rudolf

---

### Post by fwre01 on 2008-05-26
Sounds very strange, is laptop 2 actually resolving the IP addresses of the sites?

---

### Post by superprash2003 on 2008-05-26
i would say try changing DNS Servers of laptop to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) ..

---

### Post by IOWAHC on 2008-05-26
Laptop 2 is resolving the IP.

Tried changing the DNS to openDNS but didn't work, although the Laptop 1 can reach the sites, so this shouldn't be a DNS Problem.

Found maybe the error, the Server isn't responding to ICMP Packages (ping); but to HTTP and some other connections (JOSM Client); Could this be the Problem?

Greets

---

### Post by IOWAHC on 2008-05-26
Better Net Topology Graphic:

---

### Post by IOWAHC on 2008-05-27
So no one could help me. Still having troubles...

thx anyway

---

