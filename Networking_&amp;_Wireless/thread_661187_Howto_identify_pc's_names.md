---
title: "Howto identify pc's names"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2008-01-07
You can check all connected IP's in your LAN with:
```
#nmap -sP 192.168.0.*
```
But, what about trying to know the name of each machine?
If your server gives dinamic adresses it would be usefull to know not just the ip but also the name of the computers.
¿is there any way to know that?
Thanks a lot!

---

### Post by schaumkeks on 2008-01-08
> **jmvidalvia said:**
> You can check all connected IP's in your LAN with:
```
#nmap -sP 192.168.0.*
```
But, what about trying to know the name of each machine?
If your server gives dinamic adresses it would be usefull to know not just the ip but also the name of the computers.
¿is there any way to know that?
Thanks a lot!

For each IP you can use
```
host <ip>
```

Bye, Sven

---

### Post by jmvidalvia on 2008-01-08
Thanks, but...
```
jm@jm:~$ sudo host 192.168.103.171
Host 171.103.168.192.in-addr.arpa not found: 3(NXDOMAIN)

```
:(

---

### Post by schaumkeks on 2008-01-08
> **jmvidalvia said:**
> Thanks, but...
```
jm@jm:~$ sudo host 192.168.103.171
Host 171.103.168.192.in-addr.arpa not found: 3(NXDOMAIN)

```
:(

I don't know how your LAN is connected, but if you use a server with DHCP and name server capabilities you can ask directly via
```
host <ip> <server_ip>
```
But this ip might be in your /etc/resolv.conf and therefore used anyway.

Bye, Sven

---

### Post by jmvidalvia on 2008-01-10
Many thanks!:D

---

