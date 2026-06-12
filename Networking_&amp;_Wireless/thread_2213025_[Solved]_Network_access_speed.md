---
title: "[Solved] Network access speed"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by UBUminJ on 2014-03-24
I am using Ubuntu 12.10 (until the next LTS comes out).
I never checked just wondered why I couldn't stream 1080p videos from youtube anymore - but now found out that my wired access desktop->router->LAN is only 10 MB/s.
At the same time, my dualboot WinXP in the same PC has an access speed of 100MB/s. So, it is not a router limitation.

1. question: why did this happen at the install of Ubuntu 12.10 ?

2. question: when I change the settings by using
ethtool -s eth0 speed 100 duplex full    (I have now 10 duplex full)
access to websites is very slow at the beginning, it looks as if it is hesitating to connect.

3. question: when I try to make this change permanent by using
post-up ethtool -s eth0 speed 100 duplex full       in /etc/network/interfaces
it can take ages after a restart until I am connected

Thanks for your help.

Michael

---

### Post by varunendra on 2014-03-26
Try adding "autoneg off" at the end of the command -
```
post-up ethtool -s eth0 speed 100 duplex full autoneg off
```

I may not have anymore suggestions if this doesn't help, but I'd still be interested in seeing which card/driver you are using, which you can show us with the output of -
```
sudo lshw -numeric -C network
```

---

### Post by UBUminJ on 2014-04-21
*-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection [8086:10C0]
       vendor: Intel Corporation [8086]
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:12:a0:27
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.1-2 ip=192.168.11.3 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)

---

### Post by UBUminJ on 2014-04-26
I have now installed Ubuntu 14.04 - and it is still the same problem.

---

### Post by UBUminJ on 2014-04-26
Seems to be a problem also of others.
[https://www.mail-archive.com/kernel-packages%40lists.launchpad.net/msg05069.html](https://www.mail-archive.com/kernel-packages%40lists.launchpad.net/msg05069.html)

However, I didn't find any discussion about it.

---

### Post by UBUminJ on 2014-04-30
The problem was a totally different one. I could solve it.

When I looked at the network speed under Ubuntu, it displayed 10 MB/s. When I looked at it under Windows XP (dualboot), it displayed 100 MB/s. 
Due to the end-of-life of WinXP, I reinstalled my dualboot system. I have now Win Vista installed. And now looking at the network speed, it showed only 10 MB/s. 
=> Router problem !!
I installed a hub between the router and my LAN and I am running my wired PC parallel to the router - and now both Vista and Ubuntu display 100 MB/s.

---

