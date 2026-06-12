---
title: "iptables for Ubuntu Bridge"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by tequila-net on 2008-10-28
Hello All.

I started in a new company and found a bad, independet network with foreign, official IP adresses and a Win2003 Server. The network has more than 300 devices that are talking all day long to the Server.
My idea now is to install a linux-bridge between the server and the network. The Bridge has 2 IP-Networks on the client-side for the old IP adresses and the new ones, to have time to change all devices step by step.
My problem now how to arrange the iptables to allow the communication between the two ethernet interfaces. I think i only need some rules in the nat table. The policies for all tables are on ACCEPT, because it is a temporary solution without any access from outside.

Here are the networks and the interfaces:

eth0
ip: 192.168.0.5
mask: 255.255.255.240

eth1
ip: 123.45.0.100
netmask: 255.255.0.0

eth1:1
ip: 10.100.0.1
netmask: 255.255.240.0

Thank you to everybody that can help me with this problem.

---

### Post by nixscripter on 2008-10-28
The general theory of ethernet bridging is here:

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

This will cause all packets to be forwarded across both networks. However, if you want to do IP address translation between networks on either side (NAT), that's more complicated.

---

