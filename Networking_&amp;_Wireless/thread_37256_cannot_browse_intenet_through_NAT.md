---
title: "cannot browse intenet through NAT"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by accmariano on 2005-05-26
Hi all, 

I have installed Ubuntu in an old Compaq Notebook with PCMCIA Realtec RT8139 and I can't browse internet

Here my configuration

NOTEBOOK CONFIG:
Ip addres 192.168.0.25
NetMask 255.255.255.0
route default gateway 192.168.0.1
DNS in resolv : My ISP DNSs

I''ve disabled ipv6 by adding following  lines to /etc/modprobe.d/aliases

alias net-pf-10 off
alias ipv6 off



GATEWAY CONFIG:
My gateway is a linux KNOPPIX kernel 2.6.11 with iptables configured like this


Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:522
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1719
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1720
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1721
ACCEPT     udp  --  anywhere             anywhere            udp dpts:5000:5016
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:30000:30010
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ircd
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:auth
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:gnutella-svc
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1215
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:kazaa
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6699
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6257
DROP       all  --  anywhere             anywhere            state INVALID,NEW

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere            state INVALID,NEW

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


I can resolve any name and i can also ping anywhere without problems. 
I can also connet to other linux box anywere in internet by ssh using host names or  IP.
From the same notebook in windows I can browse internet without problems using my knoppix gateway.
I'm not using any proxy and the browsers are configured to Direct acces to internet.

[B]I can browse some sites , but the most sites I try, firefox or konqueror browser keep "waiting for ....." for ever

even if I can ping  those sites (like [www.cisco.com](www.cisco.com)) without problem.[/B]

It seems the problem is with http requests, but i don't know
 

Any suggestion???

Thanks
Mariano

---

### Post by accmariano on 2005-06-22
Hi all, 

Thanks to all that has read my post. After a month of working I 've got the solution. The problem was not on UBUNTU, the problem was on my Knoppix router box. With exactly the same configuration of iptables I ever has, but, after my las apt-get upgrade on knoppix, all works fine in Ubuntu

Regards
Mariano

---

