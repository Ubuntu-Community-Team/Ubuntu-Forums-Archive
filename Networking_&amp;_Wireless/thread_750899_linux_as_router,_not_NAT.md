---
title: "linux as router, not NAT"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by waltervalderrama on 2008-04-10
Hello my friends. I want to configure linux as a router (interface conmutation). I don't want to share an internet connection, not NAT. I have 2 networks:

192.168.13.0
192.168.14.0

I want PCs between these 2 networks ping and reach each other. I have already echo 1 > /proc/sys/net/ipv4/ip_forward, now what else. 

Please if anyone can help me.

---

### Post by dmizer on 2008-04-10
router = NAT = internet (or in this case "subnet") connection sharing.

if you just want two computers to communicate to eachother, connect them with a crossover cable, set them both with static ip (different ip addresses) and you're good to go.  no further configuration is necessary.

if you want traffic to pass from one network into the next, then you need NAT, and you should use this howto:
[https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

but instead of one device connecting to the "internet", you have one device connecting to your second subnet.

---

### Post by waltervalderrama on 2008-04-10
A router has two main functions:

- Packet switching (between interfaces).
- And routing and path search

A router shares with other routers routing tables, when a packet arrives to a router interface, it is send through the right interface according the routing table. If I turn on a Cisco router, with 2 ethernet interfaces: 192.168.1.1 and 192.168.2.1 and connect two computers through the router with the right network configuration (IP, gateway, mask), both computers communicate with each other. If I had a public and private network, then NAT is the solution. But with two same class networks, i only want routing.

---

### Post by Kebabman on 2008-04-10
> **dmizer said:**
> router = NAT = internet (or in this case "subnet") connection sharing.

if you just want two computers to communicate to eachother, connect them with a crossover cable, set them both with static ip (different ip addresses) and you're good to go.  no further configuration is necessary.

if you want traffic to pass from one network into the next, then you need NAT, and you should use this howto:
[https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

but instead of one device connecting to the "internet", you have one device connecting to your second subnet.

Since when does a router require NAT? Who knows how routers worked before RFC 2663.  A router does not need to do any kind of address translation in order to route traffic. The OP said he wanted to connect two networks, not PC's, hence the .0 at the end of the IP address.

In order to enable a Linux machine as a router you need to enable IP forwarding, as you have done. You also need to create the routing table entries telling the machine what interfaces to forward packets bound for various networks.

You can do this using two main programs so it would probably be useful to look them up.

[LIST]
[*]man route
[*]man ip
[/LIST]

Using either or both of these you should be able to set up your machine to route the packets effectively.

Here is a good set of examples for using `ip` to manipulate the routing tables :

[ip route examples.]("http://linux-ip.net/html/tools-ip-route.html")

Hope this helps.

---

### Post by waltervalderrama on 2008-05-06
I know that when you have two networks directly connected to a router, it is not necessary to add any route. They can communicate each other. I have the following topology:


LAN----------Linux--------Firewall-------ISP Router-------Internet
 192.168.13.0    192.168.14.0    Public IPs       Public IPs

I want Linux behave as a router. The firewall is doing NAT. I have a default router in Linux, aiming the Firewall. And in the firewall I have a static route to network 192.168.13.0 with Linux as the next hop. I don't understan what is wrong

---

