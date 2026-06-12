---
title: "Ubuntu 18.04 Panda Wireless PAU09 adapter not working"
date: 2018-05-30
forum: Networking &amp; Wireless
---

### Post by mangrobot on 2018-05-30
Hello! i'm currently using Ubuntu 18.04 with my newly bought Panda Wireless PAU09 but it seems that there's a problem with the driver. I've researched online to troubleshoot my problem but it seems that the Plug N Play support for the Panda Wireless PAU09 is for 16.04 and 17.10 only. I'm not sure if it's a conflict with the internal wifi so I posted the following results from the research that I've done. I've tried going to the manufacturers website but there's no helpful instructions on how to make it work in 18.04 Ubuntu

running lsusb returns
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:111c Acer, Inc 
Bus 001 Device 005: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

running lshw -C network renders below results
```

*-network                 
       description: Wireless interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 78
       serial: 44:03:2c:7c:47:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-22-generic firmware=34.0.1 ip=192.168.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:129 memory:e1100000-e1101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 54:e1:ad:7b:1c:4c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:123 memory:e1300000-e131ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlx9cefd5fd0e53
       serial: 9c:ef:d5:fd:0e:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.15.0-22-generic firmware=0.36 link=no multicast=yes wireless=IEEE 802.11

```

I hope that the community can help me troubleshoot the problem. 

Thanks in Advance

---

### Post by mc4man on 2018-05-31
If you open up (system)Settings > wireless with the adapter connected do you see it listed at top. i.e. something like 802.11n WLAN ?

---

### Post by jeremy31 on 2018-05-31
Moved to Networking and Wireless from chat and duplicate thread [https://ubuntuforums.org/showthread.php?t=2393202](https://ubuntuforums.org/showthread.php?t=2393202)
This one is closed.

---

