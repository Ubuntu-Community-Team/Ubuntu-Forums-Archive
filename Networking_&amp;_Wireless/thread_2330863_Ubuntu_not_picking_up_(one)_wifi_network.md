---
title: "Ubuntu not picking up (one) wifi network"
date: 2016-07-15
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2016-07-15
Hi,

I do a lot of my work in a local coffee shop on my Ubuntu laptop. Recently the owner upgraded his wifi and Ubuntu can't detect the new wifi network (it doesn't show up under network manager) I tried 15.10, 16.04 and Fedora 23. The network just not showing. It picks up other local networkd without problems though including the old wifi network of the coffee shop which is now no longer for the customers. Other people on Windows and Mac are picking it up with no issue. I asked the owner and he doesn't really know why, all he knows is that he gets the most expensive high speed package by Rogers. 

I know it is kind of vague so I don't expect detail trouble shooting tips. I just want to get an idea what might the problem be. 
```

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f5500000-f5503fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: enp11s0
       version: 10
       serial: 78:2b:cb:ce:1d:92
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5761e-v3.73 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f2d10000-f2d1ffff memory:f2d00000-f2d0ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlp2s0b1
       serial: 68:a3:c4:2f:07:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.5.2-040502-generic firmware=610.812 ip=192.168.0.30 link=yes multicast=yes wireless=IEEE 802.11bgn
```

```

 lspci

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```


Thanks

---

### Post by jeremy31 on 2016-07-16
Is the network on a channel higher than 11 on 2.4GHz?  Either the broadcom module or firmware seems to prevent those wireless cards from using those channels

---

