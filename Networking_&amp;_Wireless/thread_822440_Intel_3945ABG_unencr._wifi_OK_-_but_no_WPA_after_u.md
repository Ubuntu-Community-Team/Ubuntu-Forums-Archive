---
title: "Intel 3945ABG: unencr. wifi OK - but no WPA after upgrade to hardy"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by kmads on 2008-06-08
Hi,

After upgrading to Hardy I cannot connect to WPA-enabled networks?

I had some trouble in the beginning with no wifi-connections at all, but installing 'wicd' made me able to connect to unencrypted networks (thanks to chili555).

I have installed 'linux-backports-modules-hardy'.

When I do 'lshw -C network', I get the following output:
```
root@mads-laptop:/home/mads# lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:16:d3:63:77:97
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:77:fd:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.241 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
```

Please help.

Thanks, 
Mads

---

