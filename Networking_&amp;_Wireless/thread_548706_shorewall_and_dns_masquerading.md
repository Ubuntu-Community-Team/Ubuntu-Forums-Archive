---
title: "shorewall and dns masquerading"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2007-09-11
Im trying to set up a network server.
Ive got DHCP being done by dnsmasq and it is giving addresses out to the clients. ( DNS lookup seems to be better IMHO with this package)

Ive got intenet access from the server without a problem. 
the clients are doing dnslookup ok but dont have a route to the internet
 
when Ive used shorewall before there is a /etc/shorewall/masq file that has something to do with dns masquerading but ubuntu doesn't seem to have it 
So how do i get the clients to the internet ?

root@goldthorpe:/usr/share/shorewall# grep ^[A-Aa-z] /etc/dnsmasq.conf
bogus-priv
local=/home.nw/
interface=eth0
domain=home.nw
dhcp-range=192.168.0.50,192.168.0.150,60h
dhcp-authoritative
root@goldthorpe:/usr/share/shorewall#       


root@goldthorpe:/usr/share/shorewall# route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
82.39.120.0     *               255.255.248.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         82-xx-xx-x.cab 0.0.0.0         UG    0      0        0 eth1
root@goldthorpe:/usr/share/shorewall#

---

