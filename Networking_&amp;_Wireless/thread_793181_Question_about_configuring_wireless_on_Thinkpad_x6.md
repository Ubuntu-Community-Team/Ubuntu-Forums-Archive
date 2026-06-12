---
title: "Question about configuring wireless on Thinkpad x61"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by nkcser on 2008-05-13
Hi there,

I'm now using an X61 thinkpad laptop, the wireless card is PRO/Wireless 4965 AG or AGN Network Connection and my ubuntu is 8.04. Actually after I upgraded to 8.04 from 7.10, i can use my wireless, it suddenly stopped working this morning.

After the command "sudo lshw -C network", i got the following output:

===============================
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:16:d3:c2:cf:6d
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=172.16.135.170 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
===============================

I'm a newbie to ubuntu, could someone please help me out with this problem? 

Many thanks,

Billy

---

### Post by pytheas22 on 2008-05-13
Please be a little more specific about how the wireless stopped working.  Can you see networks but not connect?  Can you see no networks at all?  Did you try rebooting?  Are you using NetworkManager?

Please also post the output of:

```
iwconfig
```

and

```
ifconfig
```

---

