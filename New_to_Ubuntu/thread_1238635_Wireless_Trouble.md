---
title: "Wireless Trouble"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by sideverteuil on 2009-08-12
Hello, my system seems to be detecting my wireless card, but I am unable to view or connect to any networks. I have a RaLink RT2800 802.11n card.

I know the system is detecting the card because when I type **$ lspci** in terminal, the card is listed.
**05:02.0 Network controller: RaLink RT2800 802.11n PCI** 

However, typing **$ sudo lshw -C network **in terminal shows that the network is unclaimed and disabled.
[B]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.70 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:31:ef:34:cb:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[/B]Following some troubleshooting steps, I have installed the Windows Wireless Drivers package, installed the .inf file, but to no avail.

Overall, the card is being detected but for some reason, it is not picking up any wireless signals or broadcasts. Does anyone have any ideas that can help remedy this situation?

---

