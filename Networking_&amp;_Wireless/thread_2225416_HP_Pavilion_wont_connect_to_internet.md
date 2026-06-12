---
title: "HP Pavilion wont connect to internet"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by Philip_Moynihan on 2014-05-21
[TABLE]
[TR]
[TD="class: votecell"]              
[/TD]
              [TD="class: postcell"]                I have replaced my windows installation with Ubuntu 12.04 on  my HP notebook but now the wireless doesnt work. I can connect to the  internet using an ethernet cable but thats it. The wireless button is  also displaying amber but wont change to blue when pressed. Can anyone  help me with this?


  outputs:

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.
```


sudo lshw -C network
 ```
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 07
       serial: a0:48:1c:20:6b:b7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:78 ioport:3000(size=256) memory:f0104000-f0104fff memory:f0100000-f0103fff memory:f0110000-f011ffff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0200000-f0203fff

```






[/TD]
[/TR]
[/TABLE]
rfkill returns nothing because I added hp-wmi to the  blacklist.conf file in etc/modprobe.d/ dir.

Thanks in advance,
Philip

---

