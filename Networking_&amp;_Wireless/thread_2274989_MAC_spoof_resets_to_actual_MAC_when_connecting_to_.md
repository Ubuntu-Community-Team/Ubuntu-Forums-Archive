---
title: "MAC spoof resets to actual MAC when connecting to wifi"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by Coder88 on 2015-04-23
I can spoof my laptop's network wifi adapter (wlan0) MAC address using various common command line techniques, e.g.

$ sudo ip link set dev wlan0 down
$ sudo ip link set dev wlan0 address e0:06:e6:00:00:01
$ sudo ip link set dev wlan0 up 

the problem is when I connect to attwifi at a local coffee shop the MAC address somehow is reset to the actual real MAC of the network wifi adapter in the laptop. wtf?  This makes no sense to me, is there some reason the spoofed MAC is being overpowered?

There are several reasons one might want to legally spoof one's MAC address, such as for security reasons (so a black hat hacker bad guy does not hijack my laptop wifi MAC and do nefarious things with his laptop as 'me'), to lessen tracking by advertisers, etc. 

So I want to be able to spoof my laptop network hardware MAC, but I am just not seeing how or why the spoofed MAC is resetting to the actual mac upon connecting to att wifi.

---

