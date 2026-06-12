---
title: "Strange Ubuntu 22&amp;24 problems with Fortigate 60E"
date: 2024-11-08
forum: Networking &amp; Wireless
---

### Post by vogonjelc on 2024-11-08
[FONT=arial]Hello all,

I have a network that has FG60E rooter with several VLANs. I have a dns server setup with few FQDN pointing to my local servers (it just translates for instance apacheds.local to its ip address). First problems I noticed was that my ubuntu installed unifi network application was not resolved by devices. That was easy fix by setting inform to ip address of unifi server. My WordPress server also got is fqdn (wp.local) i set fqdn of my unifi to unifi.local my apacheds to apacheds.local. While ubuntu machines are on same VLAN they can resolve hostname so unifi.local would get pinged from wp.local. if they are on separate vlan not a chance. I don't belive it is fortigate issues because my MacOS 14 can resolve host and ping all of them (it has full access to all vlans when on administrative VLAN) if it is on user vlan it will not ping but will resolve hostname to ip and show that it cannot ping. My truenas can also resolve hostname to ip address and can ping my apacheds.local. Other two it can resolve ip but has no access to them so ping is 100% packet loss. 
My windows machine can also resolve FQDN. My UTAX printer can resolve apacheds.local (external phonebook use).
TrueNas is core so its is FreeBSD. I have not tried other linux distros. 
All machines have auto dhcp (ip reservations are on fg60E) and dns is set to interface ip. The UBUNTU machines can resolve inter VLAN and to internet but across VLAN-s not a chance. All other machines can resolve hostname and ping (if they have right to access device). So it must be something with the way ubuntu does DBS. [/FONT]

---

