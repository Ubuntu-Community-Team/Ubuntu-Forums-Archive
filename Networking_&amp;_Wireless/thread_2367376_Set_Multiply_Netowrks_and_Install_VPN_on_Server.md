---
title: "Set Multiply Netowrks and Install VPN on Server"
date: 2017-07-29
forum: Networking &amp; Wireless
---

### Post by dredix1978 on 2017-07-29
Hello,

    I'm building my first Linux router using Ubuntu server.  However I came to a small problem, the way my home network is setup.  I want to have and IP address for guest to use.  An IP for my home computer systems and another one for my VPN.  My two questions are how do I get Ubuntu server to broadcast the three different IP.  Everything I have found seems like it will one broadcast one.  I know I will have to get my wifi extenders in the house to each handle the guest IP.  I can set my extenders and AP to handle that with no issue.   I'm just trying to get the Linux router to broadcast all three and everything I have tried or read.  Doesn't help it keeps either shutting down my other two IP schemes I use in my house.  The IP schemes I use are as follows.

10.10.10.XXX -- Guest
192.168.1.XXX -- Home Network
2.15.16.XXX -- Will be the VPN side (The next question is how can I set up the Linux router to use like IPVanish or ExpressVPN) on the router box just for this IP.

Thanks for all your help

---

### Post by TheFu on 2017-07-29
Welcome to the forums.

2.15.16.x is owned by France Telecom. You just can't pick IPs. Ok, you _can_, but that will make any attempts to reach those IPs fail and it causes security issues, since your router will treat any coming from that subnet as local and provide access you probably didn't intend.  Or do I misunderstand?

I use 3 different subnets.
* Guests - 10.1.10.x - no DHCP reservations
* Secured - 172.22.22.x - static and DHCP reservations
* Servers - 172.22.33.x - static IPs only

I'm lazy and have 3 different NICs on the router, each is tied to the specific subnet and only that subnet.  They are 3 physically separate networks.  Guests are wifi-only.  Secured is mostly wired, but a few wifi devices (thanks to a nice AP), servers are wired only.

I don't have any AP extenders.  Use an AP that uses PoE and is centrally placed to cover the entire house.  Guest coverage is limited to half the house - using an old N-only router as an AP for that subnet.

My pfSense router handles all the subnetting easily.  While I've not done it with Linux, it shouldn't be hard - just tie the subnets to the specific NIC port.

Oh ... and if I wanted a VPN server that wasn't my router, I'd use one in the "server" subnet and add another subnet to make all the rules easier. Probably 172.22.23.x/24 so all my firewall rules could be /23-based and simple.

I forgot to mention, I have multiple WAN IPs (valid public, static, IPs), so it would be good to understand that part of your setup too.

Did I miss something?

So ... to get help, if you could please clearify your neteworking - you say "IP address", but I think you mean subnets, correct?

---

