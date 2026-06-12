---
title: "IPV6 LAN router network design help."
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by 1clue on 2015-03-26
Hi,

I need to ask questions about IPV6 for the network described below.

Background:

[LIST=1]
[*]I've been a self-educated IPV4 network admin for literally decades.
[*]I've used Cisco and Linux gear as routers and firewalls, but I use it so seldom that I have to pretty much look it up every time.
[*]I've designed several multi-vlan networks in IPV4 for business scenarios up to about 150 people.  So that part I'm fine with.
[*]I've read IPV6 tutorials from Hurricane, various Linux distros and several RFC's trying to figure out some of the IPV6 stuff, and frankly it's still confusing.
[/LIST]

IPV6-based comments/questions:

[LIST=1]
[*]I know that global-unique addresses work the same as ipv4 classless with respect to routing, based on the network and the node.
[*]I know that allocations are at least a /64, and why.  I'm aiming for a /56 or so.
[*]I know site-local addressing is deprecated but I don't see any replacement.
[*]Speculation:  link-local addresses cannot be used for routing.  Is this true?
[*]Speculation:  A 'link' is a collision domain.  (this network uses gigabit ethernet and will be using a managed switch and a couple dumb switches)
[*]Question:  Do I need to use global unique addresses for routing inside the LAN?
[*]Question:  Do I need to do a huge amount of reconfiguration everywhere if my prefix changes?
[/LIST]

The network:
I am setting up a LAN router at my home, which has an office.  I have an atom c2758-based access point, for firewall, VPN, router and UTM.  Here are the VLANs:

[LIST=1]
[*]Outside
[LIST=1]
[*] Currently 60/7, can currently upgrade to 200/15 but will be gigabit shortly.  So I'm aiming at gigabit performance.
[/LIST]

[*]Home
[LIST=1]
[*]This will be hooked to a SOHO router appliance with wifi.
[*]This will have full Internet access but no access to anything else, except maybe the printer.
[*]TVs/blu-ray, phones, any guests, all wifi, anything that you find in a normal house.
[/LIST]

[*]DMZ
[LIST=1]
[*]Firewalled from outside to allow only desired access.
[*]Home is treated as 'outside'
[*]VPN gets more access to these boxes.
[/LIST]

[*]Business
[LIST=1]
[*]Will contain a couple boxes which will be reachable from the Internet but only through VPN.
[*]Mostly VM guests but also physical hardware.
[/LIST]

[*]Private
[LIST=1]
[*]Will contain one physical workstation plus VM hosts, meaning access to the base operating system.  No outside-to-inside access at all, no matter what.  Will have limited outside access for updates.  The workstation is there to connect to VM hosts for maintenance, will be minimal.
[/LIST]
[/LIST]

Thanks.

---

### Post by robsoles on 2015-03-27
I have only ever played IPv4 games before too. I figure I could  subscribe using thread tools but if I bump you back to the top we get to  repeat the social experiment where we see if anybody will actually  reply with anything all that helpful if the thread is very prominent for a while.

Maybe this will help;

> **1clue said:**
> ...

IPV6-based comments/questions:

[LIST=1]
[*]I know that global-unique addresses work the same as ipv4 classless with respect to routing, based on the network and the node. 
[*]I know that allocations are at least a /64, and why.  I'm aiming for a /56 or so. 
[*]I know site-local addressing is deprecated but I don't see any replacement. 
[*]Speculation: [SIZE=2] **link-local addresses cannot be used for routing.  Is this true?**[/SIZE] 
[*]Speculation:  A 'link' is a collision domain.  (this network uses gigabit ethernet and will be using a managed switch and a couple dumb switches) 
[*]Question:  **Do I need to use global unique addresses for routing inside the LAN?** 
[*]Question:  **Do I need to do a huge amount of reconfiguration everywhere if my prefix changes?** 
[/LIST]

...

---

### Post by The Cog on 2015-03-27
[LIST=1]
[*]I know site-local addressing is deprecated but I don't see any replacement.
These three links are interesting. It seems that unique local addresses are a replacement:
[https://4sysops.com/archives/ipv6-tutorial-part-6-site-local-addresses-and-link-local-addresses/](https://4sysops.com/archives/ipv6-tutorial-part-6-site-local-addresses-and-link-local-addresses/)
[http://4sysops.com/archives/ipv6-tutorial-part-7-zone-id-and-unique-local-ipv6-unicast-addresses/](http://4sysops.com/archives/ipv6-tutorial-part-7-zone-id-and-unique-local-ipv6-unicast-addresses/)
[http://en.wikipedia.org/wiki/Unique_local_address](http://en.wikipedia.org/wiki/Unique_local_address)
[*]Speculation:  link-local addresses cannot be used for routing.  Is this true?
Yes
[*]Speculation:  A 'link' is a collision domain.  (this network uses gigabit ethernet and will be using a managed switch and a couple dumb switches)
Depends on the link architecture. Most gig ethernet is full duplex and therefore cannot collide. Neither can token ring, fddi...
[*]Question:  Do I need to use global unique addresses for routing inside the LAN?
No - you can use unique-local addresses.
[*]Question:  Do I need to do a huge amount of reconfiguration everywhere if my prefix changes?
Probably not - autoconfiguration should take care of most of it. Your name resolution will need some attention. 
[/LIST]

---

### Post by 1clue on 2015-03-30
Sorry to be so late getting back.

Actually the wikipedia link is the most helpful.  I get it now.  Much better conceptually than site-local addresses.

Now I just have to set it up....

---

