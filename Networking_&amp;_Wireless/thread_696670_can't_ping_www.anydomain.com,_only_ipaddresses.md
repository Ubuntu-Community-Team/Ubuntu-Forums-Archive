---
title: "can't ping www.anydomain.com, only ipaddresses"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by webdevotion on 2008-02-14
Hello,

Trying to fix this situation on my ubuntu 7.10 server.

We can't ping any domain names ( eg: ping [www.google.com](www.google.com) )
but we can ping ipadressess ( eg: google's ip address ).

Strange part: we can use nslookup.

[PHP]
nslookup www.google.com
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
www.google.com  canonical name = google.navigation.opendns.com.
Name:   google.navigation.opendns.com
Address: 208.69.34.230
Name:   google.navigation.opendns.com
Address: 208.69.34.231
[/PHP]

using dhcp
on our router (draytek vigor 2910) we have forced the use of an OpenDNS server

[PHP]
cat /etc/resolv.conf
nameserver 192.168.0.1
[/PHP]

---

### Post by webdevotion on 2008-02-18
I've been in contact with the manufacturer of our router etc.  but it boils down to a config issue on our server. 

Someone with a clue how to tackle this problem?

---

