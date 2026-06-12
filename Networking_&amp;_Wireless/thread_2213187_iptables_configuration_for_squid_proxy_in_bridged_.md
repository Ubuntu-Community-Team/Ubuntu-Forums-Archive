---
title: "iptables configuration for squid proxy in bridged mode"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by srijit92 on 2014-03-25
Hi,

I recently set up a squid proxy in bridged mode. But Squid is not caching due to some firewall issues I guess. Manual caching is perfectly ok.
Here is what I have set up in **/etc/rc.local**

```

ifconfig eth0 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
ifconfig br0 192.168.1.30 netmask 255.255.255.0 up
route add default gw 192.168.1.1 dev br0
ebtables -t broute -A BROUTING -p IPv4 --ip-protocol 6 --ip-destination-port 80 -j redirect --redirect-target ACCEPT
iptables -t nat -A PREROUTING -i br0 -p tcp --dport 80 -j REDIRECT --to-port 8080

```

Squid is configured on port 8080 in transparent mode.

What could be the issue?

---

