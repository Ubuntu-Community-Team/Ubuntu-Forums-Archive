---
title: "Routing /Networking help needed"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by bean66 on 2007-04-10
Hi,  I could use your help with setting up routing;

I have two netgear devices:
   192.168.0.1 (firewall that is connected to the internet)
   192.168.1.1 (wireless router, that has its internet port connected to the 192.168.0.1 device/network. This device is 192.168.0.51 on the 192.168.0 network.)

On the unbuntu system connected to 192.168.1.1 i can ping my internal systems as well as internet connect. 

However, I can not seem to ping from 192.168.0 -> 192.168.2  ...
 I can ping 192.168.0.51


PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
From 192.168.0.1: icmp_seq=2 Redirect Host(New nexthop: 192.168.0.51)



What do I need to do in order to ping the 192.168.1.2 system?

Thanks for your help.
Ken

---

### Post by rajko on 2007-04-10
you need to add static route from subnet 192.168.0.x to 192.168.1.x
use:

route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.51

this will add route to 1.1 network through 192.168.0.51

rajko

---

### Post by bean66 on 2007-04-11
Nope that didn't work..

I'm using two netgear routers...  ONe of which is a wireless the other is wired.

I've resolved this by putting the wireless router onto the wired routers network. And assigning the wireless router an ip address on the 192.168.0 network. Also set the wired router (192.168.0.1 device) as the only dhcp server. So basically the wireless router is configured to forward to the 192.168.0.1 as the internet gateway. I moved the physical plug from the internet connection to one of the network connections as well..

I also tried disabling the wireless routers firewall. No luck there either..


Hope this helps someone else... 

Ken

---

### Post by Bakey on 2007-04-11
If I were you, I'd flatten out my network, there's no reason to have your 2nd router doing any "routing." You'd be better off plugging into a standard lan port on your 2nd router and giving it a 192.168.0.x address, disabling the DHCP services on it, and basically using it an access point instead of a router. Even if you did get your current setup working, you'd be double-NATed which breaks a lot of websites.

*edit*  That's exactly what you did.  Didn't read all of your second post before replying. *embarrased*

---

