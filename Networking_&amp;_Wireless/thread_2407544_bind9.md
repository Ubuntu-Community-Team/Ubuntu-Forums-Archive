---
title: "bind9"
date: 2018-12-05
forum: Networking &amp; Wireless
---

### Post by betanine on 2018-12-05
Ok, this one is throwing me off.

I have bind9 installed and a records setup for my cluster, and the proper domain and nameserver 127.0.0.1 in my /etc/resolv.conf

When I have 127.0.1.1 servername.domain servername in my /etc/hosts, I can connect to all of my servers by name, but when I comment it out and have the private IP in /etc/hosts, I have to use nodename.domain to ssh into them, but can ping them and do nslookup.

I'm just wondering what the reason behind that is?

---

