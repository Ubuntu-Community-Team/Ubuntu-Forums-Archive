---
title: "Tracking down network congestion"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by sovietfunk on 2007-06-21
I take care of the network at an arts centre with about 30 wired and 5 wireless access points, of which 2 are unencrypted. The number of users varies, but can be up to about 20 clients at the most. Our connection is DSL with 2mbps in and out. I run kubuntu on my machines, gentoo on a few servers. The rest of the network is as mixed as can be. 

From time to time, we experience severe or intermittent network lag. Right now it has been fluctuating between normal and no connection from minute to minute since yesterday afternoon. No connection means that we don't even get a DNS response. 

I have forbidden P2P services, but it is impossible to keep track of whether the users take this seriously. I have also found looped network cables (connecting two ports on the same switch), which can bring the entire network down. 

What I'm hoping to get here is some tips on how to track down the sources of these problems. Since the entire network is switched, wireshark only shows my own or broadcast/ARP traffic. In order to monitor all network traffic, the only option I know of is to insert a linux machine with two interfaces between the DSL router and the main network switch, set it up with iptables and then monitor with wireshark. Other options might be readymade firewall switches with monitoring. 

Does anyone have experiences to share? Readymade or selfbuilt solutions, software, hardware, tips, pointers? I favor the simple and cheap, since i have little of both time and money... 

Cheers!

---

### Post by sovietfunk on 2007-06-26
Okay, then.

---

