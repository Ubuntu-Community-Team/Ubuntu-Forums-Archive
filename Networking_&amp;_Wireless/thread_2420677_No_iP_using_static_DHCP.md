---
title: "No iP using static DHCP"
date: 2019-06-08
forum: Networking &amp; Wireless
---

### Post by webmiester on 2019-06-08
Hi everyone,

I am using my switch to do the DHCP and give IP addresses.  It is set to static, with each device having a MAC address binded to a specific iP.

Now my problem is this...  The switch turns on and gives IP addresses to all the computers it finds is connected to the network at the time it is turned on.  When I connect my device at a later time, the switch doesn't give it an IP since it already gave out IP earlier.  It isnt like in dynamic DHCP setting where the DHCP server is always on the lookout for a new discoverable device.  It seems that in static, it just gives the IPs once and that's it.  Since my computer wasn't on at the time the IPs were issued, mine didnt get an IP even if I connect to the network later on.  The solution so far is to reset the switch so that it will go and give out IPs again, but this of course is quite a hassle.

So here are my questions:

Will this also happen if I use ubuntu as my DHCP server still set at static?
What can I do to make it operate like a dynamic DHCP, but still have the security of a static IP with MAC binding?

I was thinking one of the things I could do was simply MAC bind all the IP addresses I need and then MAC bind the unused ones to "fake" MAC Addresses then set the system to dynamic DHCP.  In this way, when a device we haven't registered yet becomes discoverable network, the DHCP cant give it any addresses because all its addresses have already been reserved.  

Our IP addresses have already been mapped out:  e.g. all computers are at 1-100, all mobile phone at 101-120, printers are 120-150, etc.  So in this way, I can't simply reduce the range.

What do you guys think?  What other solutions do we have?  Now, my switch only handles up to 65 reserved IP addresses, so I might need to really switch to an ubuntu machine.

---

### Post by TheFu on 2019-06-08
Perhaps you are confusing a switch with a router?  Switches don't have IP address management, to my knowledge.

Also, reserved IPs need to be outside the range for dynamic IPs.  A proper DHCP server can be configured that way and most routers that support DHCP will do that too.

Computers that don't move should have static IPs set inside them. Those IPs must be outside the DHCP ranges controlled by the DHCP server.

Of course, other people will have different opinions on setting the static IPs inside each computer that doesn't move vs setting static DHCP reservations in the DHCP server. Regardless - static IPs must be outside the normal Dynamic IP range giving to random devices.

---

### Post by kpatz on 2019-06-08
What kind of switch is it?  Switches don't generally act as DHCP servers, so they don't hand out IPs, or even work with them (except layer 3 switches, which can do some rudimentary filtering and routing based on IP).

Unless you're talking about a router, not a switch.  Consumer grade routers have a layer 2 switch built in (to provide the multiple LAN ports + WiFi), but they also route to the internet and provide DHCP for the LAN, and a wireless access point for WiFi.

If you want to give static IPs to your computers, like TheFu said, you'll have to see what range of IPs your DHCP server (router?) hands out, and then assign static IPs outside that range to avoid conflicts.  For example, a router using 192.168.1.x IPs for the LAN side often assign .1 for themselves, then hand out .100-254 for DHCP addresses, meaning you could use 2-99 for static IP assignments.  Alternatively, you can tell the DHCP server to hand out a specific IP to a specific MAC address, essentially giving that computer a static IP on your network, but still using DHCP.  This is handy for a laptop where you want a static IP on your network, but still want to use it elsewhere with a dynamic IP on other networks.

---

### Post by plasmex on 2019-06-08
Exactly, are you dealing with consumer grade or enterprise grade equipment?  Consumer grade equipment to be much more cookie cutter, while enterprise grade will be entirely malleable requiring you to know a great deal of networking concepts to configure.

Please specify so we can be of greater assistance.  Not sure why your switch would be limited to 65 IPs unless that's what it's configured for.

---

### Post by webmiester on 2019-06-11
I think this is consumer grade.

You guys are right, it is more of the router.  I am confused, and tend to interchange them.

Well about setting static IP outside the DHCP range... Is static DHCP the same as reserving an IP with MAC Binding?  I didnt know we can set a static IP outside the dhcp range.  Ill go try that out.  Thanks

---

### Post by kpatz on 2019-06-11
What make and model device (router) is it?  If it has a WAN (or "internet" or "modem") port and LAN port(s), it's a router.  And if it's consumer grade, it probably has WiFi built in too.

MAC Binding is simply telling the DHCP server in the router: "When you see *this* MAC address, give it *that* IP."  Then the client with that MAC still uses DHCP but will always get that IP from that router.

Depending on the router, it may let you reserve an IP within the DHCP range, or outside it, or both.  Give it a try and see how it works.  If it's inside the DHCP range, the router needs to "know" not to give any other client that IP, or else there could be a conflict.  The universally safest route is to use an IP outside the DHCP range.

If you assign a static IP manually, not reserving it in the router but by setting it on the client, then you must choose an IP outside the DHCP range.

---

### Post by plasmex on 2019-06-11
Consider D.O.R.A.:
D - DHCP client *Discovers DHCP server
O - DHCP server *Offers IP address the DHCP client
R - DHCP client *Requests IP address from DHCP server
A - DHCP server *Acknowledges the negotiation and the DHCP client should have an IP address without conflict

Further reading:
[https://www.networkingsignal.com/dhcp-dora-process/](https://www.networkingsignal.com/dhcp-dora-process/)

---

### Post by webmiester on 2019-06-11
Thank you plasmex and kpatz.  

As for the DORA...  we started with a TP-link TL-R470T load balancer as the DHCP provider then now we are using one of their jetstream managed switches/router to do it.  The TP-link jetstream has the feature.  My problem is that when it is set to static IP, it seems to only offer IP addresses to clients on bootup.  So after boot-up, it stops offering IPs.  So it seems to stop at the "O" process of the D.O.R.A.  If it is set to plain static IP, and If my device wasn't attached to the network when the TP-link router booted up, it wont receive any IP anymore when I do attach it.  So far, we needed to reboot the TP-link router in order for my device to be given an IP.

has anyone encountered anything like this?

---

### Post by plasmex on 2019-06-11
Perhaps you're missing an IP helper.  TP Link seems to call that a DHCP Relay:

DHCP Relay Information:
[https://www.tp-link.com/us/support/faq/1630/](https://www.tp-link.com/us/support/faq/1630/)

Load Balancer Manual:
[https://www.tp-link.com/us/support/download/tl-r470t%252b/](https://www.tp-link.com/us/support/download/tl-r470t%252b/)

---

### Post by TheFu on 2019-06-11
That's a small biz router/modem.  A step up from consumer stuff.   I'd check that the latest firmware is installed. Newest appears to be released  August 2018. It has a number of bug fixes.
> 
12. Fix the bug that DHCP server will hang when modifying it after assigning IP to clients with the same name.

There are some older versions of that model that are out of support, which is typical for the cheaper network stuff.  If you don't have the latest model, might want to consider replacing the WAN-facing connection with a solution that will be supported for 10+ yrs.  If new firmware hasn't been released in the last year, time to move on.

I have a consumer TP-Link wifi router. Since they stopped patching the firmware, it was pulled from the WAN and now it is just used as an AP outside the secure network - only for guests. No routing, no security assumed.

---

### Post by Doug S on 2019-06-12
> **webmiester said:**
> 
Will this also happen if I use ubuntu as my DHCP server still set at static?No.

> **webmiester said:**
> What can I do to make it operate like a dynamic DHCP, but still have the security of a static IP with MAC binding?If you use Ubuntu as your DHCP server, everything should be good.

> **webmiester said:**
> I was thinking one of the things I could do was simply MAC bind all the IP addresses I need and then MAC bind the unused ones to "fake" MAC Addresses then set the system to dynamic DHCP.  In this way, when a device we haven't registered yet becomes discoverable network, the DHCP cant give it any addresses because all its addresses have already been reserved.I have never done that. I reserve a pool for visiting computers and phones, so they get an IP adress, but it never ever conflicts with my MAC based (static) IP addresses.

> **webmiester said:**
> Our IP addresses have already been mapped out:  e.g. all computers are at 1-100, all mobile phone at 101-120, printers are 120-150, etc.  So in this way, I can't simply reduce the range.Well, myself I would still allocate a pool for stuff that hasn't been registered yet. If there are no addresses available just expand you LAN, say at bit mask of /23 instead of /24 or whatever.

> **webmiester said:**
> What do you guys think?  What other solutions do we have?  Now, my switch only handles up to 65 reserved IP addresses, so I might need to really switch to an ubuntu machine.I love my Ubuntu server that is my router/gateway/dhcp server/firewall/...

For reference I suggest the [Ubuntu server guide]("https://help.ubuntu.com/lts/serverguide/dhcp.html"), although it is missing some detail for the MAC based stuff.

---

