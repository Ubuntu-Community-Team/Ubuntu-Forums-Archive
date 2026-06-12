---
title: "Client not being pointed to DNS server"
date: 2015-01-06
forum: Networking &amp; Wireless
---

### Post by abasel on 2015-01-06
I have set up two virtual machines. 
[LIST]
[*]DHCP & DNS server
[*]Standard Desktop
[/LIST]

Using Ubuntu 14.04 server and desktop respectively.

DHCP is working and DNS works on the server

When I run NSLOOKUP on the desktop and enter "server" it returns 127.0.0.1 instead of the DNS ip.

What have I forgotten to do?

---

### Post by papibe on 2015-01-06
Hi abasel.

That's is because of the dnsmasq plugin on the Network Manager. It is standard since 12.04.

Run this instead
```
nm-tool
```
or this:
```
nm-tool | grep -i dns
```
Regards.

---

