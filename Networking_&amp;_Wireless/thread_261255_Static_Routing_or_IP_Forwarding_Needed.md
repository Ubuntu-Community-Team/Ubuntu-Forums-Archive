---
title: "Static Routing or IP Forwarding Needed"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by VPNR on 2006-09-20
Hi

I was hoping someone could help me identify wether I need to use static IP routing or IP forwarding.

Here is the situation and the set up of my network. (The Network may seem strange, but I will be using it as a testing environment and need it as such.)

The network is made up with 3 different subnets using 4 machines and 3 swtiches, two of the machines have two NIC cards. They will be used as software routers. All use static IPs and netmask of /24. No DNS is used. 

Client1: eth0: 192.168.10.2 gw: 192.168.10.1       >

Server/Router1: eth0: 192.168.10.1
                eth1: 192.168.20.2 gw: 192.168.20.1       >

Server/Router2: eth1: 192.168.20.1 gw: 192.168.20.2       >
                eth0: 192.168.30.1                        >

Client2: eth0: 192.168.30.2 gw: 192.168.30.1


I am trying to get it so that I can ping client2 from client1.

I know when using Windows 2003 Server, I can just turn on RRAS service (Routing Service) and add a static route on each server, and I can ping across the subnets. I need to use Ubuntu and have tried adding static routes, but these dont seem to work.

I have tried adding a static route to network/interfaces file under eth0 for both servers. 

up route add -net 192.168.30.0 netmask 255.255.255.0 gw 192.168.20.1

and accordingly on the other server2.

Do I need to use static routing or IP Fwding? I have read a little about IP Fwding, but still am unclear on the issue. Do I need to install some routing application? I dont want to use any routing protocols. Just static.

Thanks for your assistance.

Paul

---

### Post by kipeloff on 2006-09-20
Hello,
I think requested scenario should be possible with static routing.
Most likely you have to add static rules to the Router1 and Router2,
Router1,
route add -net 192.168.30.0 netmask 255.255.255.0 gw 192.168.20.2
Router2,
route add -net 192.168.10.0 netmask 255.255.255.0 gw 192.168.20.1

---

### Post by VPNR on 2006-09-20
Yeah... I wouldve thought it would work with static routes, but it is not working:

Here is what I have in my interfaces file for Router 1:

auto eth0
iface eth0 inet static
address 192.168.10.1
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.20.2
netmask 255.255.255.0
gateway 192.168.20.1
[COLOR="Red"]up route add -net 192.168.30.0 netmask 255.255.255.0 gw 192.168.20.1[/COLOR]

And this is what the routing table looks like:
 
Kernel IP routing table
Destination     Gateway   Genmask       Flags Metric Ref Use Iface
192.168.20.0    *         255.255.255.0   U     0      0    0 eth1
192.168.30.0    192.168.20.1  255.255.255.0  UG   0    0    0 eth1
192.168.10.0    *         255.255.255.0   U     0      0    0 eth0
default         192.168.20.1   0.0.0.0    UG    0      0    0 eth1


I still cannot ping the client 192.168.30.2, but I can ping the internal Iface of the 2nd Router, 192.168.30.1. This works with out having a static route. (Please note: I have setup a static route on the 2nd router for the eth0 routing to 192.168.10.0

Someone.. please help

Cheers

---

### Post by VPNR on 2006-09-20
Here is a Logical Diagram to make things look clearer.
[IMG]http://www.paulhenshaw.com/Logical_design.gif[/IMG]

---

### Post by kipeloff on 2006-09-21
I think one of the server should have upstream connection (Isn't it ?).
1) I assume Ubuntu server with address 192.168.20.1 having upstream connection, let's consider the configuration.

3 hosts: 
address 192.168.10.2 (gateway 192.168.10.1); 
address 192.168.10.1 (Ubuntu server, gateway 192.168.20.2), 
address 192.168.20.2 (gateway 192.168.20.1)

4th host Ubuntu server 192.168.20.1 has default gateway to the remote networks (where 192.168.x.x doesn't exist), but 20.1 knows about 20.0 and 30.0 networks, it doesn't have information about 192.168.10.0 network. Add static route, which tell to route packets with the destination 192.168.10.0/24 trough 192.168.20.2
It should work fine.

2) Let's consider scenario, if you don't have upstream connection, it will be the same as the first one. Set correct IP address and gateway settings to the 3 hosts, add static route for the 4th host (192.168.20.1). 
You may set default gateway to 192.168.20.1 as 192.168.20.2, but than all packets destined to the networks not present on the routing table will be redirected to the neighbor router, but the neighbor router will return them back (it doesn't about this networks) and again again.

---

### Post by VPNR on 2006-09-21
Thanks for your suggestions Kipeloff

I just figured out what the problem was. The static routes are right, just like you had said. The problem was that in linux distributions, by defualt, ip_forwarding is not enabled.

All I had to do was enable the ip forwarding and I could ping across the networks.

I found a great recent article explaining it. 
[http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/#more-102](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/#more-102) 

It is well worth a read. All I had to do was change:

/etc/sysctl.conf:
net.ipv4.ip_forward = 1

It was a frustrating week tryign to figure it all out, but now atleast it is working.

Hope this post helps other people out there.

Cheers

Paul
VPNR

---

### Post by kipeloff on 2006-09-22
I'm glad to hear that you resolved the particular issue with routing.
I'm sorry for not pointing out the correct parameter.:(

---

