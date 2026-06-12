---
title: "Is that a routing problem?"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2008-03-28
Good day (or nite) everyone!

I've got a problem that I really can't solve myself: I've got a PPTP connection that works perfectly in Windows, but I want to make a Windows free Linux server! The problem that worries me is the fact that I can't establish a PPTP connection with the server and I doubt that it even hears me, 'cause I get the 'LCP timeout sending config requests' everytime. pptp-connect-errors log says 'no route to host' sometimes.

The server has a statistics HTTP server that is on 172.20.0.2 and you can visit it without authorization and that's what I do in Windows, I plug the cable, DHCP gives me IP and here I go! But that doesn't happen in Ubuntu. I can ping all the provider IPs from Ubuntu though. 

My route table is as follows:> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.21.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         172.21.0.1      0.0.0.0         UG    100    0        0 eth1It seems that 172.21.0.1 (my gateway) is here and it is default but it doesn't work anyway. Yet I do not get how the netmask can be 0.0.0.0 in the line below... Please help me, I'm really lost here...](*,)

---

### Post by PryGuy on 2008-03-29
Please help me

---

### Post by PryGuy on 2008-03-29
Okay, here's another thing, I remembered what I used to do before when I tried to establish a pptp connection using GUI tools and found out that I used to install Firestarter... So I did again and EVERYTHING WORKED!!! Do you have any idea what Firestarter changes/adds to the current setup 'cause I don't want to use it?

---

