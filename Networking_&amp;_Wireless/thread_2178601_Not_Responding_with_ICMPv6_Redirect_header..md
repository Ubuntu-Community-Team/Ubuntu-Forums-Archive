---
title: "Not Responding with ICMPv6 Redirect header."
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by hrisikeshsahu on 2013-10-04
Hi All,

I have a setup with two routers( one is Ubuntu ( Router 1)and another one is FreeBSD( Router 2)).It is test setup equivalent to the IPV6 Ready logo InterOperability test 1.5.

**Network 1**
--------------
Ubuntu(eth0)----------------> Connected via Hub to the ---------------->Our target Board( HOST1 - IPv6 Stack) + One interface of FreeBSD IPv6 router ( re0) which does not transmit Route Advertisement. That is radvd is disabled in re0 interface of FreeBSD.
I add a static route to the Router 1 indicating Router2's Link local address as the next Hop for Network 2. 

**Network 2**
---------------
Another interface of FreeBSD ( rl0) is connected to the Windows XP.Here rl0 interface transmits route advertisement to  the Windows XP device.

**Network 1**  -ICMPv6 request from eth0 to HOST1 and re0 interface of FreeBSD works with global and link local address.

Network 2 - ICMPv6 request from Windows Xp to rl0 ( FreeBSD) works with global and link local address. ICMPv6 Request from windows XP to re0 of FreeBSD is working fine.


Problem - 
----------
While Sending ICMPv6 request to HOST1( Network 1) from Windows xp(Network 2), HOST1 is able to understand the packet and is able to send a reply to the Router1 ( ubuntu), Now Ubuntu should send a _**ICMPv6 Redirect**_ message to the HOST1( target board) . But Router1 is sending a ICMPv6 message with **No route to Destination.**

Please help me what is missing in ubuntu , that it is not able to send ICMPv6 Redirect message.

For this TOplogy Map I have attached a win word doc to the attachment.

Regards

---

