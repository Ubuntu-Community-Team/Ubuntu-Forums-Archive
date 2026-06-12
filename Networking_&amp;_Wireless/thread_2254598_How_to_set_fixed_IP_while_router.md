---
title: "How to set fixed IP while router"
date: 2014-11-28
forum: Networking &amp; Wireless
---

### Post by yigal2 on 2014-11-28
My router has no capabilities of setting fixed IP according to MAC address.
Can my Ubuntu "tell" the router to assign it a specific IP?

---

### Post by Bucky Ball on 2014-11-28
Welcome, and yes, it can. I only use static IPs on all my machines. 

Firstly, to the router. You need to set the DHCP server on the router to serve addresses ONLY within a certain range. For instance, 192.168.0.10 to 192.168.0.20. If you don't need the DHCP server, disable that function.

On your computer, click the network icon and then Edit Connections. Select the connection you want to edit and In the IPv4 settings tab there, set the machine's IP as, say, 192.168.0.30, outside the range the router's DHCP server is serving IPs. Set the gateway to the IP of the router and the network mask to 255.255.255.0.

Your ISP can supply you with their DNS IPs. 

So, in other words, set the static IP at the machine, not the router. I have four machines set up this way and the router serving with a range of IPs for visitors to use. 

Hope that helps. Good luck. ;)

---

### Post by yigal2 on 2014-11-29
> **Bucky Ball said:**
> Welcome, and yes, it can. I only use static IPs on all my machines. 

Firstly, to the router. You need to set the DHCP server on the router to serve addresses ONLY within a certain range. For instance, 192.168.0.10 to 192.168.0.20. If you don't need the DHCP server, disable that function.

On your computer, click the network icon and then Edit Connections. Select the connection you want to edit and In the IPv4 settings tab there, set the machine's IP as, say, 192.168.0.30, outside the range the router's DHCP server is serving IPs. Set the gateway to the IP of the router and the network mask to 255.255.255.0.

Your ISP can supply you with their DNS IPs. 

So, in other words, set the static IP at the machine, not the router. I have four machines set up this way and the router serving with a range of IPs for visitors to use. 

Hope that helps. Good luck. ;)

Thank you! it worked like a charm.

But I wonder why you prefer doing it on the machine, not on the router?

I have to, because my Router is primitive: I can't set static IPs per MAC address, I can't name the computers (I assume better routers can name each device, because MAC IDs are not easy to remember). But if I had a normal router, wouldn't it be better to control it there?
I think this is a must with laptops/mobile devices: At my place I can control the IP range of the router, but I can ensure that each router  will keep the same rules of IPs allocations.

I am going to buy a new router soon anyway, so I would appreciate any idea (or a recommendation for router .....)

---

### Post by Bucky Ball on 2014-11-29
I screwed around with trying to set static IPs on the router and couldn't get it working when I first started with Ubuntu (about 7 years ago), but I could get things working via this method. Have just always gone that way since. No other reason. ;)

Glad it worked.

---

