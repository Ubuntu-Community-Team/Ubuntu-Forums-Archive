---
title: "Two NIC's in Round Robbin-- How to Force Port 80 to one?"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by mlapaglia on 2008-10-28
```
mlapaglia@jennifer-desktop:~$ ip ro
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.5 
192.168.2.0/24 dev eth1  scope link  src 192.168.2.5 
192.168.1.0/24 dev eth0  scope link  src 192.168.1.2 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.2  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default 
	nexthop via 192.168.1.1  dev eth0 weight 1
	nexthop via 192.168.2.1  dev eth1 weight 1
mlapaglia@jennifer-desktop:~$ 

```

and 

```
mlapaglia@jennifer-desktop:~$ ip ru
0:	from all lookup local 
32764:	from 192.168.2.5 lookup 2 
32765:	from 192.168.1.2 lookup 1 
32766:	from all lookup main 
32767:	from all lookup default 
mlapaglia@jennifer-desktop:~$ 

```

These settings allow me to round robbin two of my NIC's together, which helps a lot on torrent downloads, where the connections can be split up over each network.

Now I'm having the issue of port 80 switching from one to the other. Is there a way to have a port stay on a specific NIC, like permanent forwarding from eth0 to eth1, so if anything is outgoing to eth0 it will forward to eth1 and then go to the internet?

Thanks.

---

### Post by mlapaglia on 2008-10-28
So far I have tried: 

```
iptables -t nat -A PREROUTING -p tcp -i eth0 -d 192.168.2.1 --dport 80 -j DNAT --to 192.168.1.1:80

iptables -A FORWARD -p tcp -i eth0 -d 192.168.1.1 --dport 80 -j ACCEPT

```

but it doesn't seem to be doing much. I've been perusing google but haven't found any solid how-to's for something like this.

---

### Post by mlapaglia on 2008-10-29
bump? Anyone know if this is possible with iptables or do I need to venture another route?

---

### Post by PinkFloyd102489 on 2008-10-29
Im sure there has to be a way to bind port 80 to a certain interface. Instead of iptables, try searching for interface port binding.

---

### Post by mlapaglia on 2008-10-29
isn't port binding done per application (telling firefox to only use eth0, etc)?

I need a low level forward, or route, or something, because I have numerous programs and scripts accessing the web, and I need them to use the same IP address so cookies will remain in place etc.

thanks :)

---

