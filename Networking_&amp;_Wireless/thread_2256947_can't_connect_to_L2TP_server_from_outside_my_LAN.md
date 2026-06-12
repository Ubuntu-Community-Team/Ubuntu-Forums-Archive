---
title: "can't connect to L2TP server from outside my LAN"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2014-12-15
I have set up an L2TP VPN server following the instructions found here [https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_14.04.html]("https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_14.04.html")

If I'm at home on my network I can connect to my L2TP connection from any client devices; OSX, Windows, Linux and Android.  The weird part is that when I try to connect to L2TP from outside my network (my phone's 4g connection for example, which is essentially my end goal here)  I get connection failed.   And this is for EVERY platform.

So my question is, why does PPTP work outside my home network but L2TP does not?

I have the following ports forwarded from my server (static local IP address 192.168.0.2)

443 UDP (ssl)
500 UDP (ipsec)
1701 UDP (l2tp)
1723 TCP (pptp)
4500 UDP (nat)

...so, what am I missing?  I've even tried setting my server as a DMZ host in the router and still no joy.

EDIT:

So I've discovered something else that's strange.  I have been thinking that it is certainly possible that my ISP is blocking some of these ports.  I tried checking at shieldsup [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2") but it only seems to scan TCP ports, not UDP.  I can telnet in to my IP on these ports from outside, so I know that my ISP is not blocking them.

Not only that, but out of curiosity, I started an OSX vpn server and forwarded the ports above to the OSX server instead of my Ubuntu server.  Strangely, I can connect to that server remotely from a Mac or Windows computer, but not Linux or Android (which as I stated above was the intent).  So is this a Linux problem, an Android problem, an ISP problem or something completely different I'm overlooking.

I know already from experience that Apple modifies the standard L2TP configuration to work with Mac computers and iOS devices and its not possible to configure Android to connect to a Mac OS X L2TP VPN server (PPTP does work on the other hand).  Competing products and all... I don't like it but it makes sense in the context of Apple's closed ecosystem.  So my question is, what does OSX server L2TP do differently that Ubuntu isn't doing?

---

