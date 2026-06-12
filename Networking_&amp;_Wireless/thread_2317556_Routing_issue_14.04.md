---
title: "Routing issue 14.04"
date: 2016-03-17
forum: Networking &amp; Wireless
---

### Post by shadragon on 2016-03-17
I have a 14.04 server set up to run OwnCloud. Everything was working for six months up until yesterday. 

We have two sub-nets involved: 

192.168.20.0/24 is our Corporate network.
192.168.0.0/23 is our Guest network. (OwnCloud server is here for student access)

192.168.1.2 is our firewall. eth0 is disabled and not used. 

Problem is from the OwnCloud server. I cannot resolve any DNS names. If I use IP's it goes through except on our Corp network. Cannot see it at all. Here's some info. 

**/etc/network/interfaces**

auto eth1
iface eth1 inet static
address 192.168.1.28
netmask 255.255.254.0
gateway 192.168.1.2
nameservers 192.168.1.2, 192.168.20.9
broadcast 192.168.0.255
post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.1.2 eth1
post-up route add -net 192.168.0.0 netmask 255.255.254.0 gw 192.168.1.2 eth1
post-up route add -net 192.168.20.0 netmask 255.255.255.0 gw 192.168.1.2 eth1

[B]
>route -n[/B]
```
Kernal IP Routing table
Destination       Gateway        Genmask        Flags Metric Ref    Use    Iface
0.0.0.0            192.168.1.2    0.0.0.0           UG    0       0        0      eth1
192.168.0.0       0.0.0.0        255.255.254.0   U     1       0        0      eth1
```


You'll notice three static route lines on the interfaces, but only two show up under the route. If I manually add the Corp network route, it appears, but I cannot ping or resolve names from the OwnCLoud server. If I restart my network-manager (or reboot) the two lines for route appear, but not the Corp route. Apache/OwnCloud is working as advertised. 

From the OwnCloud server, if I ping the guest network I see the nodes. If I ping 8.8.8.8, I get a return. Ping google.com, nothing. Ping DNS server IP on Corp and nothing. The staff and instructors cannot access the OwnCloud server from Corp to upload materials. 

This was working perfectly until yesterday. My guys tell me no one has changed anything, but I'm not sure. Do you notice any reason why this would not work? I've been staring at this for four hours and I'm mystified. 

Cheers.

---

### Post by papibe on 2016-03-17
Hi shadragon.

A few thoughts:

Since the server's only way out of the LAN is 192.168.1.2, you just need one route: the default route pointing to 192.168.1.2.

This route is already created when you specify netmask, gateway, and broadcast on /etc/network/interfaces (you may add 'network' too, but it is implied).

When the server wants to go to 192.168.20.9, which is not in the LAN range, the server will send packages to the firewall (192.168.1.2). Then it is the firewall's job route the traffic to the other network, and route the responses back to the server.

May be someone changed something on the firewall?

Hope it helps. Let us know how it goes.

BTW. I believe the broadcast should be 192.168.1.255

EDIT: also the field is  dns-nameservers not  nameservers. That may be the reason you don't have resolution.

---

### Post by shadragon on 2016-03-18
Cheers Papibe. 

I cleared the route commands from interfaces and  rebooted. I was able to ping 8.8.8.8, but still couldn't get to  google.com. I suspect the firewall is parsing info as I cannot ping from  Corp to Guest either. People can log on in the short term and that was  the biggest issue. DNS is not resolving still on the server itself, but I  can work on that long term.

Thanks again.

---

### Post by papibe on 2016-03-18
Could you open a terminal, run these commands, and paste back the results?
```
ls -l /etc/resolv.conf 

cat /etc/resolv.conf 

nslookup google.com

dig ubuntuforums.org
```
Regards.

---

