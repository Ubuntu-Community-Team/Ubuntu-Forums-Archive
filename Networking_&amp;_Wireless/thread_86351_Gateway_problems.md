---
title: "Gateway problems"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by Cambrant on 2005-11-04
Hi, I've been trying to configure a computer as a gateway for my home network for a few days now, and I finally got most of it to work, except for one thing.

My setup is like this: The gateway box that I'm currently configuring is connected to my DSL modem with eth0 and its two other NICs (eth1 & eth2) are connected to two workstations which have both been configured to use my gateway for their internet access.

It all works great when any one of the workstations are connected to eth1. The gateway can reach the workstation and vice versa, and the workstations can reach the internet. However, as soon as I try to connect a workstation to eth2 I get "Destination Host Unreachable" when trying to ping the workstation from the gateway box.

From the messages I'm getting, it seems that the gateway box tries to reach both workstations (192.168.0.5 and 192.168.0.10) from eth1 which is set to IP 192.168.0.1. What I want to do is that when any contact to 192.168.0.5 is being made, the gateway should use eth1, and eth2 for 192.168.0.10. I hope this isn't confusing anyone. :)

Could this problem be solved by adding a few iptables rules? I'm not sure how to tell the computer to connect through both NICs when trying to connect to a workstation in my local network.

Any help would be really appreciated. I'm pulling my hair here. ;)

---

### Post by greenway on 2005-11-04
Before you start toying around with your IPTABLES, I would check the routing tables first (type "route" at your terminal). Make sure that the route to 192.168.0.10 is set to eth2 and not eth1. If you need any help, please post your route output.

---

### Post by Cambrant on 2005-11-04
[QUOTE=greenway]Before you start toying around with your IPTABLES, I would check the routing tables first (type "route" at your terminal). Make sure that the route to 192.168.0.10 is set to eth2 and not eth1. If you need any help, please post your route output.[/QUOTE]

That makes sense. Here's my routing table:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
213.114.252.0   *               255.255.252.0   U     0      0        0 eth0
default         ua-213-114-252- 0.0.0.0         UG    0      0        0 eth0
```

However, the man page for route didn't make enough sense for me to figure out how to add the correct route for each internal IP-address.

---

### Post by greenway on 2005-11-05
Right! That's not going to work. According to your routing table you now have two NIC connected to the the same network (192.168.0.0). Since you are only connecting one host per NIC, I would enter both these routes manually into your routing table.

So for 192.168.0.5:

sudo route add 192.168.0.5 * 255.255.255.0 U 0 0 0 eth1

and for 192.168.0.10:

sudo route add 192.168.0.10 * 255.255.255.0 U 0 0 0 eth2

Try this and then try pinging both of the hosts. Please post your results.

---

