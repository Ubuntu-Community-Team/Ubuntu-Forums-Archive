---
title: "Netgear FWG114P problems"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by lelandpaul on 2005-04-12
Hi, all. I'm a brand-new Ubuntu user (well, I'll be frank: while I know my way around, for the most part, I'm new to linux in general). I installed it yesterday, and except for one major problem, I love it.

I installed Ubuntu yesterday, and all went well... I shut it down for the night, turned it back on this morning, and found that the internet connection, which had been autoconfigured prefectly fine the day before, was apparently not working. Absolutely nothing: I've rebooted both the machine and the router several times, and get nothing... I'm writing this from a secondary computer.

Now, I've hunted around these forums and found similar topics, and yet none of them have helped me at all, either because I don't have the ability to download the packets they suggest or because, having tried them, they simply don't address the problem. So, here I am, asking for help.

As the title of this post says, I'm using a Netgear FWG114P router for DHCP.
The first thing I noticed when I started poking around was that the 'Network Tools' panel said that the computer was configured for a loopback interface network device... Eth0 has address, multicast, MTU, and state 'not available'. The 'Network Tools' panel says that the interface eth0 is active... It also lists no DNS hosts... And, as far as I know, I don't have any that I normally use (my other computers, of other operating systems, list nothing in this regard, and they all work fine...)

That's pretty much where I stand, currently. I've attempted to edit various files (including /etc/resolv.conf), but, as I'm not really sure what I should be putting in there, it ain't working so well... :) 

The only other piece of information I can think to offer up is the result of an 'ifconfig' for eth0.... Which reads thus:

[FONT=Courier New]
eth0   Link encap:Ethernet HWaddr 00:07:E9:C1:7C:A5
          BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes: 20592 (20.1 KiB)[/FONT]

Any help would be greatly appreciated.

-lelandpaul

---

### Post by lukem on 2005-04-12
Under 
System> Administration> Networking
do you have a listing for "eth0" that is listed as active?
If you select it, and check properties is it set to DHCP?

---

### Post by lelandpaul on 2005-04-12
Yes and yes. It is active (I have deactivated and reactivated it a few times, as well), and it is apparently set to DHCP.

-lelandpaul

---

