---
title: "Network card disabled"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by OKinVA on 2009-09-01
Just upgraded from 8.04 to 8.10.  I have a Thinkpad T42, and the wireless card wasn't recognized by 8.04.  8.10 sees the wireless card, but it is disabled.  Currently I'm using a Belkin USB card.  This is what I get when I run lshw -c network:
*-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:2e:2a:80
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:0e:9b:48:7f:df
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 module=airo multicast=yes wireless=IEEE 802.11-DS
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:d4:6a:1e:3e:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:fd:91:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

When I remove the Belkin card, I can still see my wireless network.  I get a message asking for authentication for my network, but the 'security' dropdown and 'connect' button are both greyed out.  My only option is 'cancel'.

---

### Post by ponto18 on 2009-09-02
I've had that same problem... My solution was to add my wireless connection manually.
Right click in the networkmanager -> Edit connections -> Wireless -> Add

and set up your connection.

Hope it helps.

---

