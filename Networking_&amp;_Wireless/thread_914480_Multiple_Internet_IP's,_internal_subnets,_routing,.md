---
title: "Multiple Internet IP's, internal subnets, routing, and SSL's help please"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by rodneykaeding on 2008-09-08
I have a client with a single Ubuntu 7.10 Server with 3 websites on it that need to be available on the Internet.  2 of the 3 sites have shopping carts and have separate SSL certificates bought through GoDaddy.  We have a package of 5 outside (Internet) IP’s from the ISP, Comcast.  I’ve added 2 more NIC’s to the server assigning the 3 NIC’s to 3 inside subnets (192.168.1.15, 192.168.2.15, 192.168.3.15).  Apache is configured to use the separate inside IP’s for the 3 sites for both port 80 and 443.  DNS on the server is configured for the 3 websites and all 3 resolve properly.  Outside DNS point to the appropriate Public IP we have for the 3 sites and they all resolve properly.  2 Linksys routers are added to the network along with the original bringing the total to 3 Linksys routers between the Comcast router (which is set up as a bridge), and the server, (and all computers on the network). The Linksys routers are setup for NAT for the 3 different corresponding subnets on the server NICs and plugged into the appropriate NIC on the server.  

I’ve setup a static router between the 3 routers so anyone within any of the 3 subnets can see each router and all 3 server NICs.  And I have all 3 routers connected to a common switch along with the rest of the network. And finally all 3 routers’ WAN connections are connected to the Comcast router.  

Internally, everything works great; everyone within any subnet can see all 3 sites and the proper SSL certificate is used for the 2 shopping carts.  However, it does not work on the Internet.  Once I hook up a second and/or a third router to the Comcast router, surfing on the first website becomes slowed down significantly and then finally will timeout and none of the 3 sites will be available.  At no time does any of the 2 additional sites become available on the Internet so long as another router is plugged in to the Comcast router. I can make any of the 3 sites become live on the Internet so long as the other 2 Linksys routers are unplugged from the Comcast router. From the Internet I can ping all 3 routers no problem though.   During this time the internal network connections remain solid and PC’s can still browse all 3 sites.  Then when I disconnect the 2 additional Linksys routers from the Comcast router and about 2 minutes later, the main website comes back and is available on the Internet again.  

Through several calls with Comcast and escalating the problem to tier 2 tech support I’m confident the problem is not their router.  I am missing something in my configuration on the server.  I say this because I temporarily setup 2 of the 3 server NIC’s with 2 Public static IP’s for the 2 shopping cart sites and hooked them directly to the Comcast router and the same thing happens, all 3 sites timeout.  

I use iptables as a firewall within the server and this problem exists with or without it on, (meaning populated with the port restrictions or flushed out so no restrictions exist).

I have searched high and low on the Internet for a solution but can’t find anything that works for my particular situation.  I believe the problem is within the network configuration, via routing table or something else.  Is there another component that needs to be configured in the mix?  Do I need IPv4 Forwarding to be enabled even though the server is not acting as a router?  Do I need to setup an extra route between NIC’s or something?  Is there a configuration in iptables that needs to be set for this to work on the Internet?  I’ve look at the server logs but see nothing to indicate what the problem is.  The Apache logs don’t show any connection attempts so the requests aren’t getting that far.

I just need some direction to follow.  Maybe a better link to a website that explains how to do this.  I’ve talked at length with a Cisco engineer about this scenario and even though I’m using 3 internal routers it should work.  Buying a single Cisco router to replace the 3 Linksys routers is definitely doable but I’m afraid we’ll have the same problem.  I want to make what we have work before spending a lot of money on a Cisco router.  

Any ideas would be appreciated.

Thanks in advance - Rodney

---

### Post by rodneykaeding on 2008-09-10
Update - After some experimentation we have narrowed down some of what's happening. As it turns out, the Ubuntu server will only use one of the 3 routers at any one time.  It will for reasons unknown at this point, direct all traffic through, say router 2, even though router 1 is sending packet requests to it.  It's as if the server makes a selection to use one of the 3 routers and ignores the other 2.  

I believe the solution may lie in a more deliberate means of controlling packet flow from within the server.  It must be told to listen to all 3 routers and reply back to the originating router to keep the packet traffic proper for each NIC/website.

Any suggestions, anyone?  

Thanks - Rodney

---

