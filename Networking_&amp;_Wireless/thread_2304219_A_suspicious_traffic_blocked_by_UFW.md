---
title: "A suspicious traffic blocked by UFW"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by coverup1128 on 2015-11-25
Two weeks ago I installed lots of updates (after a long time) on  my Ubuntu 12.04 LTS laptop, which seemed to break my VPN connection. I went to check syslog, and noticed a suspicious traffic blocked by the firewall:

```
Nov 25 18:28:10 <suppressed> kernel: [  205.370726] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:74:da:38:04:10:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
```

This message appears in /var/log/syslog every 30 sec or so. The source IP 192.168.0.1 is my router, and the destination 224.0.0.1 is all-systems.mcast.net (don't know what this is). The laptop has two interfaces, wlan0 is 192.168.0.15, eth0 is 192.168.0.16. I don't quite understand what  MAC=01:00:5e:00:00:01:74:da:38:04:10:48:08:00 means, it looks too long for a legit MAC address. 

Is there way to find out what's causing this messages to appear and why?  

Please help.

---

### Post by Doug S on 2015-11-25
Have a look [here]("http://ubuntuforums.org/showthread.php?t=2258806"), and follow the links therein.

Edit: it is nothing to worry about. as for the MAC= stuff: It is your MAC address and probably the router MAC address and the 08:00 at the end, I can not recall.

---

### Post by coverup1128 on 2015-11-25
An interesting piece of information.... I am attaching the router status. 

[ATTACH=CONFIG]265764[/ATTACH]

Firstly, it appears that 74:DA:38:04:10:48 is the one of the router's MAC addresses, it shows as part of the long MAC string in the message I quoted. Secondly, the MAC address shown under Internet 00:21:CC:6E:2A:C2 is MAC address of my laptop's ethernet card, which is probably why the laptop is getting all those messages. What should be a correct setting there, the router's WAN MAC address I suppose?

Edit: I put all zeros MAC in the Dynamic IP setting, and my MAC address has been replaced by something that is likely the MAC address of the router's WAN (please see the screenshot below). But the messages continue!

[ATTACH=CONFIG]265765[/ATTACH]

---

### Post by coverup1128 on 2015-11-25
Doug S, 

Thank you. You are correct, it was IGMP! I disabled IGMP settings on the router, and these messages stopped.

---

