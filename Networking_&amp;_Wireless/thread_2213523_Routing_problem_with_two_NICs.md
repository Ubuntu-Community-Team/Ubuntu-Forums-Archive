---
title: "Routing problem with two NICs"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by rosmo on 2014-03-27
Hellou,

I have Ubuntu 12.04 LTS server virtualised and it has two NICs attached, one for external network (Internet) and one for internal. The problem is that I can't access server from internal network with public IP-address (eth0), but only with intranet's IP-address (eth1) from intranet. If I disable eth1 everything works just fine, I can connect to server with public IP-address from intranet and also I can connect to server from external network if both NICs are enabled. 

I hope that I explained problem in somewhat clear way :)

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:15:5d:64:64:09
          inet addr:88.148.163.156  Bcast:88.148.163.255  Mask:255.255.255.192
          inet6 addr: fe80::215:5dff:fe64:6409/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1735925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1016800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2050109814 (2.0 GB)  TX bytes:108907423 (108.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:15:5d:64:64:0a
          inet addr:192.168.100.103  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::215:5dff:fe64:640a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17279953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1776769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2675595258 (2.6 GB)  TX bytes:2433460635 (2.4 GB)

```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         88.148.163.129  0.0.0.0         UG    90     0        0 eth0
0.0.0.0         192.168.100.1   0.0.0.0         UG    100    0        0 eth1
88.148.163.128  0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

/etc/network/interfaces
```

#external network
auto eth0
iface eth0 inet static
metric 90
address 88.148.163.156
netmask 255.255.255.192
broadcast 88.148.163.255
gateway 88.148.163.129
dns-nameservers 8.8.8.8


#Intranet
auto eth1
iface eth1 inet static
metric 100
address 192.168.100.103
netmask 255.255.255.0
broadcast 192.168.100.255
gateway 192.168.100.1
dns-nameservers 192.168.100.10

```

---

### Post by rosmo on 2014-03-28
Bump

---

### Post by Iowan on 2014-03-28
What happens if you omit (comment out or delete) the gateway for eth1? 
Some routers won't let you come in on an external address with an internal IP (to prevent spoofing).

---

### Post by SeijiSensei on 2014-03-28
Remove the "gateway 192.168.100.1" from the second stanza.  Your machine should have only one default gateway, the upstream router that connects to the Internet.  Traffic within the 192.168.100.0/24 network does not need a gateway; those machines talk among themselves via Ethernet broadcasts.

---

### Post by SeijiSensei on 2014-03-28
Remove the "gateway 192.168.100.1" from the second stanza.  Your machine should have only one default gateway, the upstream router that connects to the Internet.  Traffic within the 192.168.100.0/24 network does not need a gateway; those machines talk among themselves via Ethernet broadcasts.  Machines on that network do need to have 192.168.100.103 specified as their default gateways, so that traffic to the Internet is forwarded through the Linux box.

---

### Post by apohal9 on 2014-03-29
The "gateway" option sets the _default_ gateway. This is by name why you cannot have two gateways. There will never be the possibility to add more the _one_ default gw.

---

### Post by rosmo on 2014-04-01
> **apohal9 said:**
> The "gateway" option sets the _default_ gateway. This is by name why you cannot have two gateways. There will never be the possibility to add more the _one_ default gw.

Tried that one. Didn't work :(

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         88.148.163.129  0.0.0.0         UG    90     0        0 eth0
88.148.163.128  0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

---

### Post by apohal9 on 2014-04-01
Can you ping both server adresses?
Would you mind to please collect the network setting of the client (ip, routes) from which you are trying?

---

### Post by rosmo on 2014-04-01
Nope, can't ping from intranet to external ip, but of couse I can ping server's intranet address from intranet. And that goes for all workstations.

My windows-box's ipconfig
```


   IPv4 Address. . . . . . . . . . . : 192.168.100.246(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.100.1

```

---

### Post by apohal9 on 2014-04-01
I assume, when you ping the public IP, your passing the router at 192.168.100.1 that translates (NAT) the private 192.168.100.246 to a public IP, correct? If so, does it got translated to an IP within the same subnet as the servers public IP? If so, then it should work if you therefor sending your request from the "outside" (interface). Anti-Spoofing should then not take place. (See Iowan's post)

But: what is the need of connecting from the external IP to the server if you are even in the same subnet (192.168.100.0/24)? Why don't you like to use the servers IP on eth1?

---

### Post by rosmo on 2014-04-02
> **apohal9 said:**
> I assume, when you ping the public IP, your passing the router at 192.168.100.1 that translates (NAT) the private 192.168.100.246 to a public IP, correct? If so, does it got translated to an IP within the same subnet as the servers public IP? If so, then it should work if you therefor sending your request from the "outside" (interface). Anti-Spoofing should then not take place. (See Iowan's post)


Apparently router doesn't translate private to public. So then anti-spoofing is taking place?

> 
But: what is the need of connecting from the external IP to the server if you are even in the same subnet (192.168.100.0/24)? Why don't you like to use the servers IP on eth1?

Annoyingly, for some people understanding intranet and internet address is quite difficult. And then there have been mix-ups sending intranet address to client. And of course this problem just bugs me :)

---

### Post by apohal9 on 2014-04-02
> **rosmo said:**
> Apparently router doesn't translate private to public. So then anti-spoofing is taking place?
If the router/firewall has such rules implemented and active, yes.

> **rosmo said:**
> 
Annoyingly, for some people understanding intranet and internet address is quite difficult. And then there have been mix-ups sending intranet address to client. And of course this problem just bugs me :)
Just a bunch of numbers ;)

---

### Post by SeijiSensei on 2014-04-02
> **rosmo said:**
> Annoyingly, for some people understanding intranet and internet address is quite difficult. And then there have been mix-ups sending intranet address to client. And of course this problem just bugs me :)

Do you have an internal DNS server?  If so, why not assign a name to 192.168.100.246 and tell people to use that rather than an address?

Even better is to have the name match 192.168.100.246 on the internal DNS server, but point to the router's external address in your public DNS records.  Then you can send the same hostname to people inside and outside your organization.

---

### Post by apohal9 on 2014-04-02
> **SeijiSensei said:**
> Even better is to have the name match 192.168.100.246 on the internal DNS server, but point to the router's external address in your public DNS records.  Then you can send the same hostname to people inside and outside your organization.

Exactly the best solution. Resolving different via DNS is the best way.

---

