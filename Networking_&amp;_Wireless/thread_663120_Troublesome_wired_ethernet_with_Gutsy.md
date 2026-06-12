---
title: "Troublesome wired ethernet with Gutsy"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by MarkTBSc on 2008-01-09
My ethernet port isn't working for some strange reason. It's only come on of late and is rather annoying since wireless is a lot slower.

I'm using a Fujitsu Siemens Amilo, dual booting between Gutsy and XP. It may or not be worth noting that this problem showed up at the same time as an update for Gutsy that has stopped the boot and shutdown *Ubuntu* graphics from showing. All I see is the system text scrolling past. 

Ok. Precise description of the problem... When using Gutsy, my machine will not connect to the network via the ethernet port/cable. It will connect via my external wireless card. It will also connect via my cabled network when I boot into Windows. If I go into network options, it will allow me to set things like roaming, dhcp, static etc, but will not work with any settings. 

lspci gives me:
"06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)"

and ifconfig gives me:
"eth0      Link encap:Ethernet  HWaddr 00:03:0D:49:09:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xcc00 "

I've tried taking the network down and up again. I've tried resetting the network services. That doesn't work. My Windows install can use the wired network to contact the net and to contact other machines on my network. The other machines on the network can access everything and my Ubuntu install is fine working via wireless (It's a tad unstable but survivable).

Any suggestions guys?

---

