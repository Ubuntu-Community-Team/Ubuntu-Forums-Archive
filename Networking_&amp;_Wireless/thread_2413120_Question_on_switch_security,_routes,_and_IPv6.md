---
title: "Question on switch security, routes, and IPv6"
date: 2019-02-21
forum: Networking &amp; Wireless
---

### Post by AR_Kozz on 2019-02-21
Ubuntu 18.04

I live in an apartment building with comcast broadband provided to all tenants, who are all connected to an ethernet switch connected to the modem.

The modem has been dropping connections over IPv4 recently after only a few minutes. When this happens, with my pc connected directly to the switch, the metric on the default route through the switch's internet-connected port jumps from 100 to 20100 under $route -n. The switch's network is also listed and the metric there remains at 100. This looks like routes to other devices on the switch will now be preferred to the unreachable modem port.

Before this, I had a router connected successfully to the switch statically using its internet port as gateway. Now when it tries to connect to the switch it gets errors of someone else's router refusing to connect. I'm sure of this because the address refusing the connection is not in the switch's network range, and it's not my router refusing to connect to itself. 

The effect for IPv4, of course, is a lot of nxdomains and timeouts. But some sites still work fine. nslookup made it plain that those that work all had IPv6 addresses, while those that didn't all had only IPv4. What really blows my mind is I can delete every route but IPv6 still works. 

So, the questions:

1) due to the lower metric, and my router's "failure to connect" to another router address, am I correct that the bad modem is causing traffic to seek the internet through the other connected devices? Using the network map feature on a windows 7 device, for example, I was able to identify another route to the internet through two routers and a gateway. 

1a) if so, is this a security risk, and how can I preclude my own internet traffic from being thus diverted? The switch network resurrects itself if I delete the route, and I don't see why the switch wouldn't redirect my traffic to the best, or only, route to the internet regardless of how I configure my own routing table.

2) since IPv6 doesn't follow IPv4 routing rules, what rules does it follow, and is it more likely that I'm connected through the otherwise-malfunctioning modem, or some unknown person's router?

thanks for reading this long question.

---

### Post by #&amp;thj^% on 2019-02-21
I'm not going to have a complete solution for you, but just some good reading for you.
for this part of the question, "since IPv6 doesn't follow IPv4 routing rules, what rules does it follow"

Some information from Cisco:[https://www.cisco.com/c/en/us/about/press/internet-protocol-journal/back-issues/table-contents-4/ipj-archive/article09186a00800c830a.html](https://www.cisco.com/c/en/us/about/press/internet-protocol-journal/back-issues/table-contents-4/ipj-archive/article09186a00800c830a.html)
> 
Connecting IPv6 Routing Domains Over the IPv4 Internet
by Brian E. Carpenter, IBM & iCAIR
Keith Moore, University of Tennessee
Bob Fink, Energy Sciences Network

A next-generation Internet Protocol [1] , known first as IPng and then as IPv6, has been under development by the Internet Engineering Task Force (IETF) for several years to replace the current Internet Protocol known as IPv4. The reasons behind the need for IPv6 are not covered here, but interested readers are encouraged to read "The Case for IPv6" [2] for this background.

Of major importance during the development of IPv6 has been how to do the transition away from IPv4, and towards IPv6. The work on transition strategies, tools, and mechanisms has been part of the basic IPv6 design effort from the beginning. The current transition efforts, taking place at the IETF IPng Transition Working Group (ngtrans) [2] , will continue until it is clear that the transition will be successful.
"Comcast" is a subject that I will just remain silent on.

I guy I follow a bit for my information, well i'll just quote him:
> 7.  Security Considerations

   Tunneling is not known to introduce any security holes except for the
   possibility to circumvent ingress filtering [13].  This is prevented
   by requiring that decapsulating routers only forward packets if they
   have been configured to accept encapsulated packets from the IPv4
   source address in the receive packet.  Additionally, in the case of
   automatic tunneling, nodes are required by not forwarding the
   decapsulated packets since automatic tunneling ends the tunnel and
   the destination.
This is found here: [https://tools.ietf.org/html/rfc2893](https://tools.ietf.org/html/rfc2893)

---

### Post by AR_Kozz on 2019-02-21
thanks, that's very informative. Unfortunately the information is that there's apparently no equivalent to traceroute to figure out how the IPv6 packets are getting through on the broken IPv4 infrastructure. 

If I'm reading that second link right, the endpoints of a tunnel must both be IPv6 compatible, so presumably I could rule out the modem as the path if it turns out not to be.

But even if it is, I suspect the originating IPv6 device would still prefer to build the tunnel through some other connected, IPv6 compatible router that has an alternative internet connection with a lower metric. I hypothesize that the IPv4 infrastructure of such a device may be either rejecting or failing to deliver ordinary IPv4 traffic, but willing/able to deliver IPv4-encapsulated IPv6 packets between the alternative internet source and everyone on the switch. Even if that rerouting doesn't introduce a potential attack vector, I wouldn't want the extra traffic if it were my router.

I'm unable to precisely interpret the metric shown by $route -n, as there are apparently, according to Cisco, many different ways to calculate the metric, and the documentation for $route doesn't say which one it uses. Does 20100 mean "entirely unreachable," or just a very bad value of whatever the metric is measuring?

---

### Post by AR_Kozz on 2019-02-25
Using wireshark, I've identified the normal Comcast gateway device, and confirmed that when IPv4 goes down, my IPv6 traffic is arriving via a different device. There is no IPv4 route information in the packets, but the source appears to be a private router of a make not likely to be part of Comcast's infrastructure. Is there a relatively simple way to block traffic via this route, at least outgoing?

---

### Post by AR_Kozz on 2019-02-26
wireshark further confirms that there are two devices using the gateway's LAN address. The suspect router periodically polls the range of addresses in the LAN and receives responses, including from my PC, that apparently lead to great confusion.

I tried using 

sudo iptables -A INPUT -m mac --mac-source di:eb:ad:ro:ut:er -j DROP

to block what's diverting traffic from the real gateway, and found I completely lost internet connectivity, and yet my PC was still not only sending IPv6 packets to said router, but even querying it in TCP to confirm it was the real (gateway LAN address).

How else can I instruct my machine to ignore that router and not send anything toward it?

---

