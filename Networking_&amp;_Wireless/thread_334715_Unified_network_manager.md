---
title: "Unified network manager?"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Kensey on 2007-01-09
Does an integrated network autoconfigurator exist for Linux?  By "integrated network autoconfigurator" I mean something that will recognize the location from the network characteristics (IP, wireless ESSID, DHCP lease info), and customize the network settings the way the user specifies, and works with both wireless and wired networks.  Here's an example:

I deal with three work networks and one at home.  The home network (O) may be wireless or wired depending on whether my neighbor's running a microwave (or that seems to be the issue anyway -- whatever it is knocks out all active wireless NICs and networks for up to 5 minutes at a time).  The work networks are one wireless (S) that covers both locations, and a wired network at each location (C and A).  What would be really spiffy is if I had a single utility that would automatically look at the networks and notice the following things:

O (wireless): Uses ESSID "O----", subnet 192.168.1.0/24 and DNS specific to my ISP.
O (wired): Uses subnet 192.168.1.0/24 and DNS specific to my ISP.
S: Uses ESSID "s-------", subnet 172.X.Y.0/24 (where X and Y vary by the physical location you're in) and main DNS for the institution.
C: Uses subnet 10.182.A.0/24 and main DNS.
A: Uses subnet 10.182.B.0/24 and main DNS.

In addition there are various public wireless networks I connect to that mostly use 192.168.0.0/24 or 192.168.1.0/24, but nothing should be done in those cases.

What I want to have is custom DNS server entries and search domains added ahead of the defaults *depending on* the network I'm currently connected to.  Each work and home site has its own local DNS that should be contacted before the defaults served from DHCP, and likewise its own local domain suffix not visible from outside that network.  Adding them all as permanent entries in /etc/resolvconf/resolv.conf.d or /etc/dhcp3/dhclient.conf doesn't really solve the problem because I'll end up with two or three or four DNS lookups that fail before one succeeds for every internal lookup I do.

I wrote a VBScript (go ahead and laugh if you want :)) to do something similar to this for our Windows clients at work based on the network subnet -- does such a thing exist on Linux?

---

