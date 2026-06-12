---
title: "netw4v32.inf ndiswrapper invalid driver"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by redprag on 2007-12-22
Can't get my wifi working.
 I use LG's E500 laptop with ubuntu 7.10 and here is what I have done so far:


sudo lshw -C network

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ed:4a:9b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.102 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


after that I installed ndiswapper from synaptic and i found the windows driver which is netw4v32.inf given from the manufacturer on a cd. 

On that cd I found out that it's intel's drivers. maybe it's the chipset or something. I don't know

I run ndiswapper from system--> admin --> windows wireless drivers

When I give it the location of the driver and try to install  it, it only gives me: "invalid driver"

Is there another way to get it working?

thank u

---

