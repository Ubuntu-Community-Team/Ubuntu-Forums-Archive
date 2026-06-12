---
title: "IP address question"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by davidcopper on 2008-01-23
I am living on campus and connecting to Internet via gateway in university. I checked my ip address, which showed up as 10.x.x.x. Does it imply that mu university has been assigned a class A address? 

As far as I know, the number of class A address is little compared with class B and class C. I am just not sure if my university is "qualified" for a class A address. 

Thanks for any ideas you may give.

D C

---

### Post by trinak96 on 2008-01-23
Using 10.x.x.x internally is OK, it's not routable on the internet and is used quite commonly in private LAN's, as in your campus. For internet access your university will have been issued a "public" ip address which is routable on the internet and all user pc's will have their 10.x.x.x address NAT'd to the public address.
Check out [http://www.faqs.org/rfcs/rfc1918.html](http://www.faqs.org/rfcs/rfc1918.html) for details of reserved private subnets...

---

### Post by dannyboy79 on 2008-01-23
ithat's not uncomon, my dad's airport extreme wifi router provides him an ip exaclty the same. My home wifi router provides me 192.168.x.x, it's really up to dhcp server in the router BUT all private networks have to be using set defined number per RFC 1918 per here: [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

---

