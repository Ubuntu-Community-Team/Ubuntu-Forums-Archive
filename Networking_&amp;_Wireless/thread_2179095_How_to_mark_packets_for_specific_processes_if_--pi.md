---
title: "How to mark packets for specific processes if --pid-owner is not supported anymore"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by zyHEpEJ on 2013-10-06
Hello,

I have the following problem, that I want to mark/force traffic of specific tools I need to monitor internet routing, for example tools like mtr or traceroute, to go over a specific interface I want to chose between. I have four connections on the same router:

eth1(wan) cable modem (default gw)
tun0 OpenVPN connection
tun1 OpenVPN connection
2nd router with another ISP connection on the same subnet as eth0

The problem now is, I cant force the traffic of these monitoring tools, because they need to be run as root, and the option --pid-owner was taken out of iptables, whatever reason for. I cant use --uid-owner, because like you see the dilemma here, I cant create an extra monitoring user, because these tools I want to force the traffic, always need to be run as root, because they need raw socket access.

So what is the solution here?

---

