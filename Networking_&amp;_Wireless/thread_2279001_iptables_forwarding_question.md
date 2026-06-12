---
title: "iptables forwarding question"
date: 2015-05-20
forum: Networking &amp; Wireless
---

### Post by vperaino on 2015-05-20
Hey everyone. I'm trying to get familiar with iptables just as a general matter of knowing stuff. :) Right now I was trying to work out a practice solution for a little setup I have going on my desk. Basically, I just have a little Ubuntu server box hooked up to a switch (internet source) via eth0, and I want to forward all traffic *except ssh connections on port 6500* (such that I can still communicate with it) to a laptop connected to the server box via its eth1 port, such that the laptop behind the server box can have full network access. 

I've enabled traffic forwarding on the server box using sysctl, installed **iptables-persistent**, and these are the iptables rules I've tried implementing:

```
iptables -A INPUT -p tcp --dport 6500 -j ACCEPT

iptables -A FORWARD -i eth0 -j ACCEPT

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

But this doesn't seem to be working. Any suggestions?

---

### Post by SeijiSensei on 2015-05-20
If the client is connected to eth1, and eth0 points to the upstream router with Internet service, you need to use "-o eth0" in the masquerading command.

---

### Post by vperaino on 2015-05-20
> **SeijiSensei said:**
> If the client is connected to eth1, and eth0 points to the upstream router with Internet service, you need to use "-o eth0" in the masquerading command.

I'm a little confused on the syntax, how would iptables know then to route the traffic from eth0 to eth1?

---

### Post by SeijiSensei on 2015-05-20
The routing table handles all of that.  Masquerading simply replaces the source IP address of outbound packets with the Internet-facing address of the router and keeps track of which LAN machine created the connection so it can pass reply traffic back to the origin.

For instance,
```

10.200.200.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.10.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         10.200.200.1    0.0.0.0         UG    0      0        0 eth0

```
This routes traffic between an internal network on 10.10.0.0/16 and an external network, 10.200.200.0/24 with an Internet-connected router at 10.200.200.1.  (The router has another interface that points to the Internet.)  Traffic within 10.10.0.0/16 stays on the eth1 network, and traffic on 10.200.200.0/24 stays on the eth0 network.  Traffic between the networks is handled by the routing table. All other traffic (0.0.0.0) is forwarded to the router since it is the machine's "default gateway."  

The machine has this masquerading rule:
```
/sbin/iptables -A POSTROUTING -o eth0 -j SNAT --to-source 10.200.200.200 
```
This rule masquerades outbound traffic using the machine's eth0 address of 10.200.200.200.  I used SNAT (source NAT) rather than MASQUERADE because the box has other interfaces as well as these.  Either SNAT or MASQUERADE will work on a simple router with two interfaces.

---

### Post by vperaino on 2015-05-22
One other thing I'm confused about concerning this. 

I'm practicing this here in the office at work. Here's a simple diagram of the relevant network structure (with the iptables stuff going on in the "server box"):

[IMG]http://i.imgur.com/7kR0pC7.png[/IMG]

If the DHCP source is BEHIND the server box (with respect to the laptop I'm trying to forward everything to), is that a problem? I'm having a little trouble understanding how I'm supposed to configure the networking on the server box with respect to both NICs.

---

### Post by SeijiSensei on 2015-05-22
In that arrangement you can run isc-dhcp-server on the "SERVER BOX" to provide addresses to client machines behind it. Alternatively you can run isc-dhcp-relay on that box to forward requests to the actual DHCP server.  I'd take the first route because I suspect addressing and routing would get complex in a relay scheme, especially if masquerading is involved.  

An easier solution if you're supporting just the laptop is to give it a [static IP address]("https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing"). Create a unique subnet between the BOX and the LAPTOP, enable packet forwarding on the BOX, and masquerading as well. For instance, if 192.168.37.0/24 isn't in use anywhere on the network, give the LAPTOP 192.168.37.2 and the BOX 192.168.37.1.  Make 192.168.37.1 the laptop's default gateway, and use 
```
/sbin/iptables -A POSTROUTING -t nat -o eth0 -j MASQUERADE
```
on the BOX if eth0 points upstream.

---

