---
title: "No Wi-Fi Adapter Found - ubuntu 18.04 ThinkPad"
date: 2019-07-21
forum: Networking &amp; Wireless
---

### Post by tzhao2000 on 2019-07-21
A[I]fter some update last week or something else, the wireless is not working anymore in my ubuntu 18.04 ThinkPad.

This is what I see in Wi-Fi settings: No Wi-Fi Adapter Found.  Make sure you have a Wi-Fi adpater plugged and turned on.

I ran lshw -c network command, this is what I got 
[/I]
*-**network DISABLED        **
**       description: Wireless interface**
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 78
       serial: 7c:76:35:15:05:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-54-generic firmware=34.0.1 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:174 memory:e9100000-e9101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 54:ee:75:fc:de:25
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-3 ip=10.20.45.109 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:163 memory:e9200000-e921ffff
  *-network:0
       description: Ethernet interface
       physical id: 3
       logical name: docker0
       serial: 02:42:c8:ea:9b:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 4
       logical name: enx0050b68d81ac
       serial: 00:50:b6:8d:81:ac
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=half link=no multicast=yes port=MII speed=10Mbit/s
  *-network:2
       description: Ethernet interface
       physical id: 5
       logical name: br-c8b0ec09967a
       serial: 02:42:44:b3:92:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.19.0.1 link=no multicast=yes
  *-network:3
       description: Ethernet interface
       physical id: 6
       logical name: br-786a17a7b3aa
       serial: 02:42:f3:04:d6:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.22.0.1 link=no multicast=yes



*I also ran rfkill command, I saw this*


ID TYPE      DEVICE                   SOFT      HARD
 0 bluetooth hci0                unblocked unblocked
 1 bluetooth tpacpi_bluetooth_sw unblocked unblocked
 2 **wlan      phy0                unblocked unblocked**

Not sure why line No.2 has wlan type there, It could be something I did this morning when I tried different way to fix the issue, I am not sure if it is correct or not, I think it should be wlp4s0.

I came to office this Sunday morning, try to fix it but I could not get it solved after I spent few days on it. I'll appreciate if you would help me solve the puzzle.

I can provide more information if needed

Thank you!

Tom

---

### Post by praseodym on 2019-07-21
Please run the wirless script from the sticky thread and show the output

---

### Post by tzhao2000 on 2019-07-23
here is the result from running wireless info script at [http://paste.ubuntu.com/p/TZz5dyM2xp/](http://paste.ubuntu.com/p/TZz5dyM2xp/))

---

### Post by tzhao2000 on 2019-07-23
Please let me know if you need more information, thank you

---

