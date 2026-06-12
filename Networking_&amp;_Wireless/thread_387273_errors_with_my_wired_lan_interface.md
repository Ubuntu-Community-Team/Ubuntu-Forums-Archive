---
title: "errors with my wired lan interface"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by mastersnow on 2007-03-18
Hello all,

For a while I had been running breezy badger on a server of mine and everything worked well. However, recently the system just stopped connecting to networks. When I look at ifconfig, I notice that under RX packets it says "RX packes: 0 errors: 111." When I pop in other network cards, I get the same problem. I also tried mii-tool on eth1 and it gave me "eth1: negotiated 100baseTx-FD, link ok."

So, I reinstalled Ubuntu to use edgy eft (v6.10). It worked while I had the live cd running. It also appeared to work for a little bit on my first startup of the system - however, it was very slow. I restarted and now it's back to giving me errors and not getting an IP address.

I looked at dmesg next, and found "eth1: no IPv6 routers present." Naturally, I started thinking that there must be an incompatibility with IPv6, so I go to /etc/modprobe.d/blacklist and blacklist the IPv6 module (I don't have a bad_list file for some reason, so I can't disable the alias). So now eth1 has no inet6 address. Still, I get errors in my RX packets. I'm running out of ideas. :( 

I'm not sure if the system is actually using any IP module at all after I blacklisted ipv6. Any ideas from you guys would be most welcome, as this has been a nagging problem for a while.

---

### Post by Kobalt on 2007-03-18
Do you have an output when you type in 
```
ip a | grep inet6
```
If so, then there's still an IPv6 active protocol...

---

### Post by mastersnow on 2007-03-18
There is no output. The module is disabled and no longer listed by lsmod. dmesg also no longer mentioned the "no ipv6 router found" error. Still, dhclient can't connect me to anything, and I see 442 errors listed when I run ifconfig (perhaps taking down the ipv6 module is causing some of these?)

---

