---
title: "Help! Can't ping router no internet!"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by Stelmate on 2006-10-19
Okay I did something a little silly and now I can't ping my router and don't have any internet access.  I acidently installed that silly ubuntu parental control and something happened.  I couldn't ping anything so I removed it using synaptic.  Still no dice, so I flushed the IpTables, removed guard dog, removed IPv6 in the aliases,removed squid.  Now I still see Destination host unreachable when I ping my router.  
my /etc/network/interfaces is fine

auto eth1
iface eth1 inet static
address 192.168.15.9
netmask 255.255.255.0
gateway 192.168.15.1

did flushing the iptables hurt the matter?

---

