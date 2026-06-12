---
title: "Curious About InternaI IP's On Bootup"
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2016-03-13
Attached are internal IP's I've noticed on my computer right after boot up.  They do not always show up so I'm just curious as to why sometimes they do?

---

### Post by ian-weisser on 2016-03-13
Those are IPV6 ports.
They should show up if you are running the service.

For example, if you disable CUPS print sharing, the process listening on 631 will disappear.

---

### Post by shane_faulkinbury2 on 2016-03-14
So if IPs were present the would show?

---

### Post by ian-weisser on 2016-03-14
Those are the ipv6 equivalent of 'localhost' or  ipv4's '127.0.0.1'. Those on your ports on your system's address.

Er, do you understand the difference between an *address* and a *port* ?
The way you phrased the question may indicate perhaps a bit of (understandable) confusion.

There is no such thing as an 'internal  IP'. IP addresses are, by definition, external to your system. They identify your sytem to others.

Addresses indicate an indivdual system anywhere the internet (or LAN):
ipv4: 132.41.0.23
ipv6: fe80:13fa:a6da:30af:fe97:8bfd

Port numbers refer to individual processes on that system
CUPS on my system via ipv4: 132.41.0.23**:631**
CUPS on my system via ipv6: fe80:13fa:a6da:30af:fe97:8bfd**:631**

When you use netstat for a list of ports in use on your own system, netstat uses the shortcut for localhost instead of your own IP address (if any).
If two processes want to communicate with each other using TCP/UDP, they can similarly use localhost instead of your system's actual IP address (if any). This is handy. 
CUPS on my system via ipv4 localhost:127.0.0.1:631
CUPS on my system via ipv6 localhost: ::1:631

---

