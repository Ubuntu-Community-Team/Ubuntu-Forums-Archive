---
title: "How to configure DNS for tunlr?"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by philled on 2013-10-05
I'm trying to set my Ubuntu 12.04 DNS server up so that it temporarily uses tunlr's DNS servers. I'm using dnsmasq to provide DNS services to my LAN. I also have resolvconf running (though I hate it as it just seems to make things more complicated).

I can't seem to get it working and I can't work out what DNS server is being used. When I log onto the DNS server and do a nslookup it says it's using 127.0.0.1:
```
$ nslookup www.bbc.co.uk
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   www.bbc.co.uk
Address: 94.76.223.215
```

But my interfaces file says to use different DNS servers:
```
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface

auto eth0
iface eth0 inet static
address 192.168.0.125
netmask 255.255.255.0
gateway 192.168.0.254
### This is for Tunlr DNS for DNS geo-dodging eg BBC iPlayer, Hulu etc
dns-nameservers 69.197.168.9 192.95.16.109
```


It's all so complicated with resolvconf, resolv.conf and dnsmasq I can't work out how to configure it the way I want. Can anyone please advise?

---

