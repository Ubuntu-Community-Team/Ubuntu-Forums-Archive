---
title: "Cannot get wireless to work"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by SoDak on 2008-01-18
I'm new to linux and now have Ubuntu installed on a HP ze4220 laptop.  I like it very much but I have been unable to get the wireless to work.  I'm using a D-Link DWL-G650 wireless PC card.

I've tried accomplishing the troubleshooting but cannot follow it.  The troubleshooting instructions (para 3.2.1. Check for device recognition) wants me to open the "device manager" but I don't have that listed in the administration menu.

I did go to the terminal and check for driver with the following displayed for the wireless;
 02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: D-Link System Inc D-link DWL-G650 (Rev B3,B5) Wireless cardbus adapter
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 24000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

I have tried an open network (hidden SSID) and my home network with WEP.  With the network manager I can see wireless networks but still no success.

I need help.

Dazed and confused new Ubuntu user.

---

### Post by PhaderSYD on 2008-01-18
dont know if it will help but i always have trouble connecting with network-manager, it would allow me to see the available networks but when i try and connect it halts with only one green light showing. i managed to get it to connect by entering: sudo iwconfig wlan0 essid any while connecting resulting in two lights then connection

dont know why it is like this it just is.

like i said probably no help at all but maybe someone might see my ordeal and correct me on the mistakes i am making

---

