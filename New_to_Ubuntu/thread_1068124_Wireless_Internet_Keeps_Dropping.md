---
title: "Wireless Internet Keeps Dropping"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by dankalmar on 2009-02-12
So I'm running Ubuntu 8.10 on a Sony Vaio VGN-N130G.  The problem is that my internet keeps dropping.  Actually, the problem isn't so much that the internet drops, but that it drops and when I right click on the internet in my system tray the Enable Wireless thing is no longer clickable.  This problem has been occurring more and more often.  At first I though that I was having a problem with my internet, which I sometimes do have, but it's that it drops and it's like there's a problem with the wireless driver on the computer.  I have this same problem with other wireless internets, not just the one at my house.  It drops and I can't reconnect and then sometimes it will reconnect in a bit, sometimes I just have to restart my computer and it will work.

---

### Post by sleepyjon on 2009-02-13
What wireless card & driver do you have?

Post the output of
```

sudo lshw -C network

```

---

### Post by dankalmar on 2009-02-13
*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:7f:c2:21
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:8c:5f:c5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.103 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:fd:f6:3c:25:21
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

