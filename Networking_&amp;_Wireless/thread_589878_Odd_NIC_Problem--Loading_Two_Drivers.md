---
title: "Odd NIC Problem--Loading Two Drivers?"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by kc8hr on 2007-10-24
Hi Guys,

I ran the upgrade from Feisty to Gutsy yesterday, and there is now an odd error message on boot:

[   24.557732] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.557781] 8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   24.557838] 8139cp 0000:00:0a.0: Try the "8139too" driver instead.
[   24.560568] 8139too Fast Ethernet driver 0.9.28
[   24.561705] eth0: RealTek RTL8139 at 0xd0816000, 00:40:f4:a5:ab:03, IRQ 10
[   24.561710] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'


How do I tell it to load the correct driver? I think this could help cure my slow connection.

Off-topic: If a brand-new install takes about 30 minutes, why does an upgrade take 3 hours? ;-)

Tim

---

### Post by noob12 on 2007-10-24
This is fine.  It looks like you are getting the right driver.   Your card matches the patterns for both drivers, the 8139cp driver decides it isn't appropriate.  The 8139too driver loads and it looks like it claims the device.  Type **sudo lshw -C network** and look at the configuration line to see which driver has claimed the card.

You may have other issues causing the network slowness.

---

### Post by kc8hr on 2007-10-24
> **noob12 said:**
> This is fine.  It looks like you are getting the right driver.   Your card matches the patterns for both drivers, the 8139cp driver decides it isn't appropriate.  The 8139too driver loads and it looks like it claims the device.  Type **sudo lshw -C network** and look at the configuration line to see which driver has claimed the card.

You may have other issues causing the network slowness.

Thanks for the help. Here is the result of sudo lshw -C network:

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:a5:ab:03
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.16.1.34 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

Everything seems to be normal, the right driver is claiming the NIC, so I am going to leave things alone.

Thanks again!
Tim

---

### Post by samwisgg on 2007-10-28
The reason why you have the slow connection speed is because you have your speed set at 100 Mbps. You should set it to 10 Mbps. I had the same problem with my realtek 8139 under win XP.

---

