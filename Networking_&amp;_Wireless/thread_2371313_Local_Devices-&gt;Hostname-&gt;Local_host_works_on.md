---
title: "Local Devices-&gt;Hostname-&gt;Local host works on one router, but not on another."
date: 2017-09-13
forum: Networking &amp; Wireless
---

### Post by SagaciousKJB on 2017-09-13
I have a little surveillance DVR that runs a mobile port on 18004.  In my router settings I have always port forwarded to its local address 192.168.1.3. I have a dynamic IP, so I have setup a No-IP ddns hostname to be able to point to and view the footage remotely, but sometimes I also like to grab my phone real quick and check the cameras to see who is at the door or something like that.

Well, until recently my ISP has supplied me with a Netgear router, and when a local devices such as an Android tablet points towards my No-IP hostname, the routing works just fine and it connects to the local host 192.168.1.3 that's running.

Recently my ISP replaced the Netgear routers with Sagemcom routers, and when a local device such as my Android tablet points toward my No-IP hostname, the routing doesn't work and it seems to try to connect to 18004 on my cable modem instead of routing to the local 192.168.1.3 host the router is configured to forward to.

I'm not really sure what I can do to help this. I remember running into this issue long ago with another ISP and another router and I setup a DNS server and had a rule that addressed it, but I can't really for the life of me remember what it was, or where I found it, and it's such a peculiar situation that I couldn't really Google anything up that remedied the situation other than some information about how some routers handle NAT.

It's interesting to me that the Sagemcom router doesn't handle this better, because it has so many other useful features than the Netgear routers did. I considered just buying my own to replace it, I'd save money on the rental fee and wouldn't need to worry about the DNS and all that.  The one feature I really like about the Sagemcom is that it has a DDNS script built in to use my No-IP hostname.  So I'm considering just finding a Netgear router with that feature, since I know they handle this routing predicament. Unfortunately a quick googling suggests Netgear routers are only compatible with DynDNS.

Any other thoughts or potential solutions are welcome. This router does offer some pretty extensive "routing table" modifications, so maybe there's some kind of rule I could put in there?

---

### Post by TheFu on 2017-09-14
More features aren't always good in a router.  They often blow the security, what little consumer devices have, away.
If you want control, use any x86 machine (low power is perfect) and install your own router software.  Ars has multiple articles on doing this.

This won't help if your ISP is blocking inbound ports.  Cannot tell from what has been said above if that is or isn't the issue.

I would avoid all the popular consumer routers. I've been burned by almost all of them with huge security flaws over the years, including netgear.  Actually netgear wifi has been very problematic for 1 of my customers - we ended up disabling the netgear wifi and hooking up a separate WAP which has performed perfectly even with 50+ concurrent clients.

The best long-term answer is to run a VPN from your home and setup your portable devices to access it.  That would remove the huge security and privacy issue of simple port forwarding that you've used previously and limit access only to those people devices with the VPN certificates.  It also would provide complete access to anything on your LAN from anywhere in the world. That is handy from time to time.  OpenVPN with IPSec should be used, not PPTP, since pptp has been cracked for a very long time.  I would NOT run the VPN on the router.  WAN-facing routers really should do routing and firewall stuff, nothing else.

[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)  I'm using a $140 APU2 device for mine.  Seeing that it can be patched weekly is a huge security comfort.  Any linux device running a kernel prior to March 2017 has a huge, remote access, flaw. This is a kernel flaw and doesn't require any services be running.  So be certain to verify that any router you deploy anywhere running Linux has firmware newer than that time.  There are other flaws since then, but that one was a biggy for any WAN connected or public network connected systems.

---

### Post by SagaciousKJB on 2017-09-17
> **TheFu said:**
> More features aren't always good in a router.  They often blow the security, what little consumer devices have, away.
If you want control, use any x86 machine (low power is perfect) and install your own router software.  Ars has multiple articles on doing this.

This won't help if your ISP is blocking inbound ports.  Cannot tell from what has been said above if that is or isn't the issue.

I would avoid all the popular consumer routers. I've been burned by almost all of them with huge security flaws over the years, including netgear.  Actually netgear wifi has been very problematic for 1 of my customers - we ended up disabling the netgear wifi and hooking up a separate WAP which has performed perfectly even with 50+ concurrent clients.

The best long-term answer is to run a VPN from your home and setup your portable devices to access it.  That would remove the huge security and privacy issue of simple port forwarding that you've used previously and limit access only to those people devices with the VPN certificates.  It also would provide complete access to anything on your LAN from anywhere in the world. That is handy from time to time.  OpenVPN with IPSec should be used, not PPTP, since pptp has been cracked for a very long time.  I would NOT run the VPN on the router.  WAN-facing routers really should do routing and firewall stuff, nothing else.

[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)  I'm using a $140 APU2 device for mine.  Seeing that it can be patched weekly is a huge security comfort.  Any linux device running a kernel prior to March 2017 has a huge, remote access, flaw. This is a kernel flaw and doesn't require any services be running.  So be certain to verify that any router you deploy anywhere running Linux has firmware newer than that time.  There are other flaws since then, but that one was a biggy for any WAN connected or public network connected systems.

No, it's not a port blocking issue, as it's all 100% accessible remotely.  The issue is how accessible it is locally.

So let's say for example my ddns hostname is my.hostname.ddns and it's pointing towards my external IP, which we'll say for example, is 5.5.5.5 ( thanks Hollywood ).  So previously with my old router, if a locally connected device made a connection request to my.hostname.ddns:18004 the router was smart enough to send this to 192.168.1.3:18004 instead of 5.5.5.5:18004.  This current router does not.

So in other words, previously I had my Android tablet to point towards my.hostname.ddns:18004 to view my cameras and I could view them whether I was on a remote network, or connected to the LAN at home.  Now I can only view them by pointing to this hostname if I am on a remote network. If connected locally, I must point directly towards 192.168.1.3:18004.

I use to run a little router box with Shorewall but the problem I had is I never figured out how to run run a wireless access point on it.

The VPN option does sound interesting.  I was thinking about something similar with SSH tunneling but there's not really a lot of software support for that on Android devices.  So basically what you're saying is I could run an OpenVPN server software on this machine, and then connect to that with VPN client software on the Android.  But I'm still not sure that would solve the problem, as it would just be using the same internal networking to try to route towards the hostname.

---

