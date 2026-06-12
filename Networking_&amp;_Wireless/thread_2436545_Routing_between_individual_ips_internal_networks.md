---
title: "Routing between individual ips internal networks"
date: 2020-02-08
forum: Networking &amp; Wireless
---

### Post by dieterkkk on 2020-02-08
Hello,

I have a slightly stupid question about iptables.

At my "router" I have 2 internal networks in different IP networks.

eth0: inet 10.0.0.1  netmask 255.255.255.0  broadcast 10.0.0.255
eth1: inet 10.1.0.1  netmask 255.255.255.0  broadcast 10.1.0.255

Default gateway is 10.0.0.1

Most devices are attached to eth0 with ips within 10.0.0.x.

Now there are a few devices within eth1 (e.g. 10.1.0.10) which i would like to reach from certain eth0 devices.


e.g.
10.0.0.100 and 10.0.0.101 should be able to access 10.1.0.10 and vice versa.

Additionally, 10.1.0.10 should also have "external access" via 10.0.0.1 (default gw).

What is the correct way to implement this with iptables?

Thanks

Dieter

---

### Post by SeijiSensei on 2020-02-08
Do you need to control access to the networks as you describe? Or do you just want to route packets from any device on 10.0.0.0/24 to 10.1.0.0/24?  If the latter, all you need to do is uncomment the line 
```
net.ipv4.ip_forward=1
```
in the file /etc/sysctl.conf and reboot. If you are using iptables, make sure the FORWARD policy is ACCEPT.

Devices on both networks need to have the router as their default gateways. The router itself should have an upstream router that is connected to the Internet as its default gateway if you want to let traffic leave the building.

---

### Post by dieterkkk on 2020-02-11
Thanks for the answer.

I have already tried it like this with FORWARD:
```
iptables -A FORWARD -s 10.0.0.0/24 -j ACCEPT
iptables -A FORWARD -s 10.1.0.0/24 -j ACCEPT
```

But if I want to access 10.0.0.5 from a device with the IP address 10.1.0.100, unfortunately nothing works:
```
# traceroute 10.0.0.5
traceroute to 10.0.0.5 (10.0.0.5), 30 hops max, 38 byte packets
 1 10.1.0.1 (10.1.0.1) 5,969 ms 3,094 ms 2,625 ms
 2 * * *
```

From the router (10.0.0.1/10.1.0.1) I reach of course everything.

Thanks

---

### Post by The Cog on 2020-02-11
Does 10.1.0.100 know the correct route to reach 10.0.0.5? It needs to know to send via  10.1.0.1.
Look at the routing table or ask explicitly what the route is, by running one of these two commands on 10.1.0.100:
```
ip route list
ip route get 10.0.0.5
```
Similarly, does 10.0.0.5 know how to send replies to 10.1.0.100?

Oh, and do 10.0.0.5's firewall rules allow incoming from 10.1.0.100?

---

### Post by SeijiSensei on 2020-02-11
> **dieterkkk said:**
> 
But if I want to access 10.0.0.5 from a device with the IP address 10.1.0.100, unfortunately nothing works:

As The Cog says, it's likely that 10.0.0.5 doesn't have a route to the 10.1.0.0/24 network. Is 10.0.0.1 the default gateway for 10.0.0.5? If not, you'll need an explicit route on 10.0.0.5 that directs traffic to 10.1.0.0/24 via 10.0.0.1.

---

### Post by dieterkkk on 2020-02-11
```
[COLOR=#000000](on 10.1.0.100)
# ip route list[/COLOR]
[COLOR=#000000]default via 10.1.0.1 dev eth0 [/COLOR]
[COLOR=#000000]10.1.0.0/24 dev eth0  src 10.1.0.100[/COLOR]
[COLOR=#000000]# [/COLOR]
[COLOR=#000000]# ip route get 10.0.0.5[/COLOR]
[COLOR=#000000]10.0.0.5 via 10.1.0.1 dev eth0  src 10.1.0.100[/COLOR]

```[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Is the router (10.0.0.1/10.1.0.1 with both interfaces) not able to take care of this?[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]10.1.0.100 <==> 10.1.0.1/10.0.0.1 <==> 10.0.0.5[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by The Cog on 2020-02-11
That looks OK  for the outgiong direction.
What about getting replies back (the reverse direction)?
And what about firewall rules in 10.0.0.5?

---

### Post by SeijiSensei on 2020-02-11
What's the default route on 10.0.0.5?

Your reply above looks at the situation from the point of view of the router. You also need to think about it from the point of view of 10.0.0.5.

---

