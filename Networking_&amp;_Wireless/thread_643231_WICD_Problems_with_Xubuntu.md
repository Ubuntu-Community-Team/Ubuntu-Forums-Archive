---
title: "WICD Problems with Xubuntu"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by dbanas001 on 2007-12-17
Hi,

I did some searching and I couldn't find anything to solve my problem so I decided to post my problem.  I have an old HP and I decided to install Xubuntu 7.10 to give Linux a try.  I was able to use ndiswrapper to get Xubuntu to read my wireless.  I then tried network manager and wifi radar to get my wireless to work with no success.  They always found the networks but would not connect.  I then uninstalled both of those and installed wicd.  When i first installed it and followed the instructions it worked perfectly.  When I restarted my computer my wicd cannot find any networks.  Any ideas?  Thanks.

Dave

---

### Post by csat on 2007-12-17
It is hard to say without enough information so please give us more details about your computer, like model, and which network card is in use.  You can find lots of details going through a console terminal and typing lspci -v

---

### Post by dbanas001 on 2007-12-17
I have an HP Pavilion 8565C.  I typed in lspci -v and this is what I got for network cards:

```
00:09.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: Linksys, A Division of Cisco Systems WPC54G ver. 4
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at d000 [size=32]
        Memory at e0800000 (32-bit, non-prefetchable) [size=32]
        Memory at e0000000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: ADMtek Unknown device 0574
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at b800 [size=256]
        Memory at df800000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

Thanks

---

