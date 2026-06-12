---
title: "up route problem"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by noobb2 on 2014-03-17
I was trying to connect a server(that is  connected to a dhcp server throug eth0 ) to another pc throug eth1.


/etc/network/interfaces

```

auto eth0
iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp
iface eth1 inet static
address 192.168.3.1
netmask 255.255.255.0
up route add -net 192.168.1.0/24 eth1


```

At this stage the server connection is closed(eth0), if i comment up route add -net 192.168.1.0/24 eth1  the connection will be  opened.
The 192.168.1.0 is the subnet  ip of eth0.

p.s. and i did some ip forwarding setings but i deleted them with 
```


iptables -Z
iptables -F
iptables -X

```

---

