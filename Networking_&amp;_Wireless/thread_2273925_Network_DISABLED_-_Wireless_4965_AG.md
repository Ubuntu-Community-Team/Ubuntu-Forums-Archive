---
title: "Network DISABLED - Wireless 4965 AG"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by marc_s2 on 2015-04-16
Beginer in Ubuntu. HP Compaq 6910p  Ubuntu 12.04 LTS 

I had been away from this machine for several months after having reinstalled Ubuntu 12.04 LTS and I remember the WLAN went off
Airplane is constantly on. Button on LT does not seem to react although it goes on and imidiatly off at boot and shut down.
I would appreciate your help.

sudo lshw -C network
[sudo] password for marcs: 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:fe:c7:d8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.3-0 ip=192.168.178.21 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:e4620000-e463ffff memory:e4640000-e4640fff ioport:4060(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:34:4b:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.11.0-26-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e4000000-e4001fff
-----------------------------------------------------------------------
$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
-------------------------------------------------------------------------
find /lib/modules/$(uname -r)/kernel/drivers/net/     did show the driver as in hereunder
/lib/modules/3.11.0-26-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko

---

