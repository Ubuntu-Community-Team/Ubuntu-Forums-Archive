---
title: "bcm43xx vs. ndiswrapper"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Prometheum on 2007-03-03
Recently, bcm43xx started working for my 4311 card, much to my delight. However, I cannot connect to the internet or even my router, apparently. Every time I try to connect, I go through all the steps apparently succesfully, and then when I try to ping my router, this happens:

```
ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.166 icmp_seq=1 Destination Host Unreachable
From 192.168.0.166 icmp_seq=2 Destination Host Unreachable
From 192.168.0.166 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4017ms
, pipe 3

```

This happens on bcm43xx every time its used. I can just rmmod bcm43xx and modprobe ndiswrapper to get my internet back, but I dont' like using ndiswrapper as the connection is weaker and I don't have access to monitor mode or a variety of other functions. I have tried changing my MAC address to get a new lease with my router, and I have also set up static IP leases for my eth1 MAC address, but neither of these methods have worked. Also, Network Manager started off seeing that I had bcm43xx when I had it, but now it doesn't seem to acknowledge it. I'm mixed about this because Network Manager edited my sources file to remove wlan0, and didn't work most of the time.

At the moment, bcm43xx only works with extreme cajoling; rebooting my router to wipe the dhcp leases, rebooting ad nauseum, etc. Is this just my 4311 card, or is there something I can do to fix bcm43xx? Have any other 4311 users had this problem?

---

### Post by Prometheum on 2007-03-03
Also, it is worth mentioning that I am running Feisty (I would think its relatively stable to upgrade a month before it's taken out of development) and since upgrading, my lspci have identified my card as:

```
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1363
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

In edgy, this is a 4311 card. What happened exactly?

---

