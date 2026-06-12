---
title: "dhcp problems with Realtek 8139C"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by slaroy on 2007-01-09
I used to run Fedora 3, and my network card worked fine. I put the old box away for a few months, then pulled it out and installed Ubuntu. Now the card seems to come up fine, but it won't see or accept dchp offers from the router.

ifconfig shows that the network card is receiving packets, but has no ip address
(I disabled ipv6)

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:39:07:1D 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:274180 (267.7 KiB)  TX bytes:12996 (12.6 KiB)
          Interrupt:10 Base address:0x2000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

"dmesg | grep eth" shows that the card is functional
[   79.542869] eth0: RealTek RTL8139 at 0xcc9f2000, 00:e0:4c:39:07:1d, IRQ 10
[   79.542944] eth0:  Identified 8139 chip type 'RTL-8139C'
[   83.073924] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

"lsmod |grep 8139" shows that the appropriate module is installed
8139too                26752  0
mii                     6016  1 8139too

"sudo dhclient" gives this...
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4c:39:07:1d
Sending on   LPF/eth0/00:e0:4c:39:07:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

rebooting with the noapci apci=off flags doesn't help, as suggested in other posts. Any suggestions?

Thanks!

Steve

---

### Post by slaroy on 2007-01-12
Any takers?

One more piece of data: I can ping the localhost loopback address, but nothing else, even when I set a static IP address.

Steve

---

### Post by qualjyn on 2007-01-12
Hi Steve

I think I have the same problem - and then again not. You can see a bit of info here: 
[http://ubuntuforums.org/showthread.php?t=337094](http://ubuntuforums.org/showthread.php?t=337094)

What disturbs is, that you report a different output than mine, on your lsmod | grep 8139. I get:

8139cp   22528 0
8139too  26880 0
mii         5888   2, 8139cp, 8139too

Do I have "double drivers" or something like that?

And I don't get any return packets - so it might not be the same at all...

---

### Post by slaroy on 2007-01-12
I went in and blacklisted the 8139cp driver, which is apparently newer and which some posts suggested may cause a conflict. I see the same behaviour both before and after the removal of this module, so that's not the cause. I found another post that suggested booting with the "pci=routeirq" flag. I'll try that tonight.

---

### Post by sudenaz on 2007-01-12
[http://linux-wless.passys.nl/query_alles.php?](http://linux-wless.passys.nl/query_alles.php?)

that page should help. I've had a lot of success with atheros chipset.

[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by slaroy on 2007-01-12
It won't help me because it's an 802.3 ethernet card, not an 802.11 wireless ethernet card.

---

### Post by slaroy on 2007-01-13
> **slaroy said:**
> I went in and blacklisted the 8139cp driver, which is apparently newer and which some posts suggested may cause a conflict. I see the same behaviour both before and after the removal of this module, so that's not the cause. I found another post that suggested booting with the "pci=routeirq" flag. I'll try that tonight.

Well, this caused new issues. This time when I tried to ping the router I got ICMP messages saying that the network was unreachable, rather than no messages at all. Better? Perhaps. But still broken.

---

### Post by slaroy on 2007-01-13
Some new info...

I dug out a small hub and connected my windows box to it, as well as my Ubuntu box, and connected them both to the router. 

I can ping the win box with Ubuntu, and Ubuntu with win. I can ping the router with Windows, but not with Ubuntu. I captured the packets using Ethereal, and the ICMP request from the Ubuntu machine goes unanswered by my D-Link DI-604 router. Any ideas?

---

### Post by slaroy on 2007-01-14
Solved!

I poked around at the dhcp packets for Windows and Ubuntu, and I noticed they differed slightly. I tried making the Ubuntu packets the same using /etc/dchp3/dhclient.conf, but that didn't work. So I moved on to the router...

The problem was an old firmware in the D-Link DI-604 router. I upgraded from version 2.18 to 2.20, and "sudo dhclient" worked immediately!

Good luck!

Steve

---

