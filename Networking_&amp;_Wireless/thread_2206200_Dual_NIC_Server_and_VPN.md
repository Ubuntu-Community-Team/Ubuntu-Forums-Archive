---
title: "Dual NIC Server and VPN"
date: 2014-02-17
forum: Networking &amp; Wireless
---

### Post by cliff-peeples on 2014-02-17
'Ello everyone.  Did some quick searching and couldn't come up with any threads pertaining to my question.

I have a new (to me) server en route, quad processor Intel box with 32GB ram and dual gig NIC interfaces.

What I'd like to know is how best to achieve the following:

I'd like certain traffic to traverse one NIC via VPN.

All other traffic should traverse the NON-VPN connection.  

Basically, I don't want Plex to traverse thru the OpenVPN connection, as it adds unnecessary hopcounts and degrades traffic performance.

Is there a way for me to shape traffic like this within Ubuntu Server, or would it best be handled by a DD-WRT equipped router?

Any opinions/thoughts are appreciated.  I'm really rusty with networking since I don't use it on a daily basis (perishable skillset and all that)

---

### Post by TheFu on 2014-02-18
Routing choices occur at the subnet level, not the sort of traffic involved.  If you don't want traffic over any subnet, then don't use that subnet for the access.  Basically, only access the plex stuff over the public interface, not the through the VPN.

OTOH, allowing a "split tunnel" like you are implying is a bad security practice and would be prohibited at most corporations.

The physical connection used doesn't really matter - a VPN is a "virtual network" first and foremost. Physically mixing traffic doesn't harm the virtual protection of the VPN.  Having 2 NICs connected to the same subnet on consumer network equipment will break simple routing. If you have internet connections on 2 different networks, it will be relatively easy. If not ... er ... not so much.

---

### Post by cliff-peeples on 2014-02-18
> **TheFu said:**
> Routing choices occur at the subnet level, not the sort of traffic involved.  If you don't want traffic over any subnet, then don't use that subnet for the access.  Basically, only access the plex stuff over the public interface, not the through the VPN.

OTOH, allowing a "split tunnel" like you are implying is a bad security practice and would be prohibited at most corporations.

The physical connection used doesn't really matter - a VPN is a "virtual network" first and foremost. Physically mixing traffic doesn't harm the virtual protection of the VPN.  Having 2 NICs connected to the same subnet on consumer network equipment will break simple routing. If you have internet connections on 2 different networks, it will be relatively easy. If not ... er ... not so much.

While I agree that a split tunnel is bad security on many levels, the intent for my particular scenario is no worse than the way it's currently configured.  For instance, my Plex Media Server is still accessible, although it's now degraded because my route now travels to the Netherlands, then back to the server via the VPN tunnel.  The hopcount is ridiculous!  The VPN tunnel is personal in nature and in no way work related.  I understand what VPN does, and what it's intended for.  

I guess what I was trying to figure out is what method is easiest in order to segregate traffic.  I understand that separate "physical" networks make it a lot easier, and I think this will be the route I will take.  For instance, create a separate 172.16.x.x network for Eth1, and Eth0 (or whatever the interfaces will be named) will maintain the 192.168.x.x network configuration.  Handled at the router, the gateway will still be x.x.1.1 and advertised to the 172 and 192 networks.  So while both interfaces access the internet from the same gateway at the router, their internal networks are separate.  

With the above being said, does this make sense?  Again, I'm REAAALLY rusty with this :)  Once I have two "segregated" networks, I should be able to tell applications what IP address/interface they will utilize?  

I really don't mean to over-complicate things, so by all means if you have an alternative solution please chime in :)

---

### Post by TheFu on 2014-02-18
If both interfaces are on separate networks and the router can use port forwarding to the specific NIC as needed (by port), then I don't see why this won't work.

But it honestly won't make any performance difference by having 2 NICs if 1 interface is VPN IPs and the other is "public".  The slowdown will be the uplink from the home network.  The VPN is already on a different subnet as far as any client is concerned. No need for 2 NICs at all.  If that doesn't make sense, draw a picture and label all the networking stuff.

I'm not saying that having Plex avoid the VPN is not a good idea, just that having 2 NICs (3 subnets) or 1 NIC (2 subnets) will be the same performance over the WAN.

---

### Post by cliff-peeples on 2014-02-18
Currently, all traffic is routed via VPN.  Every bit of it.  I can ping the IP of the tunnel at the distant end and I achieve 410ms responses vs. 21ms responses with the tunnel deactivated.  Throughput of the tunnel is roughly 30mbps down and 3mbps up.  With the tunnel deactivated its 57mbps down and 15mbps up.  To me that's a great gain to be had if I am able to segregate the PMS traffic from the tunnel.  Thanks for the help thus far!

---

### Post by TheFu on 2014-02-18
But the VPN is just a local separation ... that goes through 1 port of the router.  Is the VPN running on the router   (tiny CPU) or on the server?
If you setup the port forwarding using NON-VPN addressing, then all that traffic will not go thru the added overhead of encryption.

Is this making sense?
From the client, the client has 2 IPs ... what ever the local LAN provides and whatever subnet the VPN gives when the VPN is active.
Back at the house, the router has a public WAN IP and 64K ports, but only 1 port is used by the VPN. Hopefully it is UDP and all that traffic goes into the VPN server for a specific subnet.  If any other ports are used, then that traffic would be forwarded to whichever internal LAN IP requested.

When it comes time to respond to traffic requests, the source will be either the client-VPN or the client WAN-IP ... which will never be on the same subnet.  Right?  Did I miss something?

See how I'm unclear why 2 NICs are desired?  It won't matter at all for WAN traffic.

VPNs will have overhead, since every packet needs to be encrypted. Is that CPU upto the task?  I wouldn't use the consumer-router as the VPN server.

---

### Post by cliff-peeples on 2014-02-18
I understand what you're saying now but will need to respond from a PC.  On my phone now lol

Thanks and more to follow.

---

### Post by cliff-peeples on 2014-02-18
> **TheFu said:**
> But the VPN is just a local separation ... that goes through 1 port of the router.  Is the VPN running on the router   (tiny CPU) or on the server?
If you setup the port forwarding using NON-VPN addressing, then all that traffic will not go thru the added overhead of encryption.

Is this making sense?
From the client, the client has 2 IPs ... what ever the local LAN provides and whatever subnet the VPN gives when the VPN is active.
Back at the house, the router has a public WAN IP and 64K ports, but only 1 port is used by the VPN. Hopefully it is UDP and all that traffic goes into the VPN server for a specific subnet.  If any other ports are used, then that traffic would be forwarded to whichever internal LAN IP requested.

When it comes time to respond to traffic requests, the source will be either the client-VPN or the client WAN-IP ... which will never be on the same subnet.  Right?  Did I miss something?

See how I'm unclear why 2 NICs are desired?  It won't matter at all for WAN traffic.

VPNs will have overhead, since every packet needs to be encrypted. Is that CPU upto the task?  I wouldn't use the consumer-router as the VPN server.

First of all, the VPN (OpenVPN) client is running on the server, and not on the router.  I have DD-WRT as previously indicated, but I do not need OpenVPN running at the router level (because I'd need to add a routing table to have all other devices bypass the VPN tunnel).

Okay, so let's see if I'm clear with what you're saying.  With the above stated, I should be able to utilize port forwarding on the router to specify say port 65534 to egress via x.x.1.x, which is the local IP address of the interface and not the tunnel itself, technically?  So with gw of 1.1, and interface IP of 1.x, port forwarding 65534 should be forwarded to 1.x and not 1.1 which is the gw addr?

My current routing table on the server:

0.0.0.0/1 via 10.8.x.x dev tun0 
default via 192.168.1.1 dev eth0  proto static (**This is the default route correct?)**
10.8.x.x via 10.8.2.117 dev tun0  metric 1 
10.8.x.x dev tun0  proto kernel  scope link  src 10.8.x.x 
128.0.0.0/1 via 10.8.x.x dev tun0 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.x  metric 1 
193.138.x.x via 192.168.1.1 dev eth0 (**This I assume is the route passing VPN traffic via the internal gateway IP) **

Thanks again for imparting knowledge.  I appreciate it greatly! :)

---

### Post by cliff-peeples on 2014-03-04
A bit of an update:

I did some more research with the openvpn config file provided by the VPN provider.  One of the lines in the config was "nobind" so I commented it out, and added a line "local host" where host is the IP address that the VPN should bind to.

With that done, the VPN script runs however doesn't fully come up as the IP address I gave it does not have access to an outside route.  This can be accomplished by modifying the routing table at some point.  

Needless to say I haven't fully completed the task yet, but I've got a great starting point.  FWIW, the ISP I utilize provides their own router (which I'm not fond of), but would assist with "physical" network segregation.  

Rather than have the VPN tunnel via the interface that connects to my primary router, and then to the ISP router for an outside connection, I will have the VPN connect to the interface on the ISP router.  Then, my important connections that require VPN can be tunneled, while standard traffic (such as PMS) can be routed normally.

---

