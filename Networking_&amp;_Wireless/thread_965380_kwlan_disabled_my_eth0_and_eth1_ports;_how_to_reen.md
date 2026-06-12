---
title: "kwlan disabled my eth0 and eth1 ports; how to reenable?"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by moly on 2008-10-31
I just upgraded to 8.10 on kubuntu, and noticed that the old wireless manager "wireless assistant" I was using has no KDE4 version, so I downloaded kwlan. It did not recognize the eth0 port (with ethernet cable plugged in to Broadcom MCM4401-B0 100Base-TX ethernet socket) or eth1 port (with Broadcom MCM4318 AirForce One 54g card). When it was over, both were disabled.

Afterwards, I ran lshw -C network, and the result was:

  *-network:0 DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:92:30:ae
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no module=ssb multicast=yes port=twisted pair
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:16:ce:0b:2c:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 2a:15:c6:c7:d1:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


It disabled both ports! How do I get them reenabled?

---

### Post by moly on 2008-10-31
I just tried the following, and it did not work:

```
sudo /etc/init.d/NetworkManager restart
```

---

### Post by moly on 2008-10-31
I seem to have fixed it. I went to /etc/network/interfaces and found ```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

So I uncommented out the last line, and added ```

# The wireless network interface
auto eth1
iface eth1 inet dhcp
```

and then I restarted the network with ```
/etc/init.d/networking restart
``` and the wired ethernet came back online. Using ifconfig, I could see a connection, and I can ping outside websites.

WiFi Radar detects my wireless network now. I still can't get the wireless card to use my WEP key and connect to my wireless network. Any good WiFi managers out there? Recommendations would be appreciated.

---

