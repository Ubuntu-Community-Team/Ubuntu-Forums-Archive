---
title: "ISP Router &amp; Subnet"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by carl.michaud on 2013-12-01
Hi.

I have two modems:
a) ARRIS YN3720 - Provided by my ISP.
b) Linksys WRT400N running dd-wrt version v24-sp2.

I've hooked them up like so:
ISP <-> ARRIS <-> Linksys

1) The ARRIS acquires an IP address from from my ISP via DHCP from the WAN.
2) The ARRIS sets up a local network on 10.0.0.x
3) The ARRIS also provides a static IP address for the Linksys of 10.0.0.12 for its WAN.
4) The Linksys then sets up a local network on 192.168.1.x.

My rationale behind this is as follows: (I'm not really a networking expert so hopefully this makes sense).
A) The ARRIS really isn't very configurable and only runs 2.4GHz. The Linksys on the other hand serves both 2.4GHz and 5.0 GHz.
B) So I use it to provide unfiltered internet in my house to devices I trust (i.e. my personal desktop via an ethernet cable or wifi to my WII via a hidden password protected network).
C) Then I use the Linksys to provide filtered internet access via OpenDNS to the rest of the wifi devices in my house. It works as a DHCP server as well on its local LAN.

This has been working pretty well; but of course I can't figure out how to route traffic between the 10.0.0.x and 192.168.1.x networks.
a) I can't change the Linksys to setup its LAN on the 10.0.0.x network because then I'll have two DHCP servers providing IP addresses on the same subnet.
b) I could chang ethe Linksys to use 10.0.1.x for its LAN but then I don't know how to route traffic between 10.0.0.x <-> 10.0.1.x

For example my wireless printer would be living on the 10.0.1.x network (Linksys) but my desktop is on 10.0.0.x (ARRIS). I'm not sure how I'd route the traffic between the two subnets.

---

### Post by jonobr on 2013-12-02
Why not go with option A  change the Linksys to setup its LAN on the 10.0.0.x network  and disable the DHCP server on the linksys

---

### Post by carl.michaud on 2013-12-02
The problem with option A is that disabling the DHCP server for the linksys prevents me from configuring my wifi clients to use DNS servers provided by OpenDNS. DD-WRT enables me to do that on the Linksys; but the ARRIS router provided by my ISP is quite limited in its functionality.

I was also thinking about changing routers to use the same network but have the DHCP services serve only a specific range of addresses:

ARRIS
network 10.0.0.x
DHCP 10.0.0.1-127

Linksys
network 10.0.0.x
DHCP 10.0.0.128-253

That should work, right?

---

### Post by jonobr on 2013-12-02
No, I dont think that would work.

Could you disable DHCP on the Arris device? Only allow the linksys to hand out IPs?

---

### Post by carl.michaud on 2013-12-02
I'm on my way home now; I'll have a look when I get there to see if I can disable the DHCP services on the ARRIS. 

Out of curiosity why don't you think that putting the two routers on the same network will work? Here's my thinking:

The ARRIS provides a gateway to the ISP and can provide a static route to the Linksys. DHCP clients will only be connecting to this router via wifi using an SSID configured for that router only. Also my desktop will be using its own static route on the ARRIS as well. Both would be configured to use the 10.0.0.1-127 range only. 

The Linksys would be using its own SSID to allow wifi clients to connect and then would serve addresses in the 10.0.0.128-253 range. It's gateway would be the static route on the 10.0.0.1-127 range and I won't have any clients connection to this router via an Ethernet cable.

Since the two routers are connected via a dedicated cable and would be on the same network I think that they should be able to communicate with each other. As long as each router has a route to the addresses that's it doesn't serve on the other then theoretically any client on the network would be able to reach any other client on the network.

But I'm not an expert here so I'm not sure if my thinking is wrong. Why wouldn't this work?

---

### Post by jonobr on 2013-12-02
Well if your devices are connecting using distinct SSIDs I guess that would work,

I was thinking more if you had clients connecting to your network physically, then you have no real way of who it gets its DHCP ip address from,

---

### Post by carl.michaud on 2013-12-03
Ok. I gave it a whirl yesterday but I couldn't get it to work. :(

a) I can't configure the ARRIS router so that its using the Linksys to provide IP addresses via DHCP. 

b) I did try the following configuration but I can't even get the Linksys to work now. 

ARRIS
WAN 68.x.x.x via DHCP from ISP
LAN 
address 10.0.0.1 
netmask 255.255.255.0
gateway 10.0.0.1

Linksys
WAN 10.0.0.2 via a static IP from ARRIS
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.2

Thoughts?

---

### Post by pbrane on 2013-12-03
The best way would be to put the ARRIS in bridge mode if possible. You now have a router behind a router scenario. Possibly double NATed as well. Having the ARRIS in bridge mode gives you one router, the linksys.

As for your last post, the linksys gateway IP needs to be the same IP as the ARRIS (10.0.0.1). The ARRIS is the gateway to the internet or WAN. The DHCP server on the linksys would hand out a gateway IP to itself. (10.0.0.2)

---

