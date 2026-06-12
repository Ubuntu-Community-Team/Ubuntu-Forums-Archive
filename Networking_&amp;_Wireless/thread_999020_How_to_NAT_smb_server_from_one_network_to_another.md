---
title: "How to NAT smb server from one network to another?"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by rado3105 on 2008-12-01
Hi, I have problem to set NAT. I set it like this but doesnt work:


WAN - is interface where samba server is(192.168.76.4), here is also internet
LAN - is interface where computer 10.15.17.5 is

I dont want to get internet on 10.15.17.5, only communication between that samba server and computer.

smbserver --------> router(here I need to set up NAT) ---------> PC
(192.168.76.4) WAN (10.85.17.1/192.168.76.99) LAN (10.85.17.5)

when I masquerade it, it works but also internet, what I dont want.
I was trying to do that using DST-NAT, but without good result.
The only way that, I know to do that is to masquerade it and then in firewall, drop all communication to that pc(beside between SMBserver - PC), but I dont think this is good solution.

---

### Post by felker2 on 2008-12-01
Samba is IPv6 enabled as of Ubuntu 8.10, so you could use it over IPv6. I've tried that and it works. With IPv6 working, it's as easy as

smbclient \\\\system.name.net\\share_name

No NAT invovled, so no NAT-problems. :-)


If you want to stay on IPv4, have a look at [http://troy.jdmz.net/samba/fw/](http://troy.jdmz.net/samba/fw/) with this info:

netbios-ns 137/tcp # NetBIOS Name Service
netbios-ns 137/udp
netbios-dgm 138/tcp # NetBIOS Datagram Service
netbios-dgm 138/udp
netbios-ssn 139/tcp # NetBIOS Session Service
netbios-ssn 139/udp
microsoft-ds 445/tcp # Microsoft Directory Service
microsoft-ds 445/udp


HTH

---

### Post by rado3105 on 2008-12-01
problem is that I have many users, that use Windows and that is problem. Or is possible to run samba in both ipv4 and ipv6?
Probably not.

---

