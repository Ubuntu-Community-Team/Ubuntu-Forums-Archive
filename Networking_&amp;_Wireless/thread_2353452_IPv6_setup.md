---
title: "IPv6 setup"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by ELMIT on 2017-02-21
I have fiber coming to my place, with 6 IPv4 addresses and /64 IPv6

My fiber splits up into Ethernet, which I use with 2 dedicated Linux boxes and 2 Asus routers.
These two routers split the network in my desktop area (including web server with IPv6) and my TV area, plus 4x wireless (2.4 and 5 GHz).

Now I would like to use my IPv6 on all devices, but how?

I got following information:
Client Host IPv6 Segment ****::/64
Client Host IPv6 Gateway: ****::FFFF/64

Client Router WAN Port IPv6 Address: ****::0001/64
Client Router WAN Port IPv6 Gateway: ****::FFFF/64

Client Router LAN Port IPv6 Address: ****::/56

---

### Post by geeksmith on 2017-02-21
The IPv6 routing doesn't have to follow your IPv4 routing in any way. I'd suggest you start off by routing the whole /64 IPv6 network to all hosts. This is the simplest and easiest to set up while you get your feet wet with IPv6. Without more info on the routers you're using and what exactly you're trying to accomplish, it's hard to give a more precise answer than than.

As you get more comfortable with it, you could segment it, although IPv6 subnets smaller than /64 are highly discouraged, as is NAT.

---

### Post by ELMIT on 2017-02-22
Maybe it was not very clear, or I mis-understand your answer.

I am connected to the Internet with a fiber, which ends on my site with a Ethernet box of 4 ports. There I put a fast hub on one port and the other three ports are connected to Asus-1, Asus-2 routers. Further are connected some other dedicated servers.

Currently the Asus-1 router has setup the IPv6 and with DHCP distributes to the LAN-1 the IPv6. I want to have also IPv6 on the other router Asus-2 and that my dedicated servers would be reachable via IPv6.

Your suggestion to setup both router and all servers the same way, but with different WAN port address sounds good, just the segment /64 sounds not good.

I also have difficulty to understand why the LAN has a /56. Maybe there is the solution.


I want that each device on my network gets also a IPv6 address. E.g., I would like to ssh from one Asus router device to a device on the other Asus router.

---

