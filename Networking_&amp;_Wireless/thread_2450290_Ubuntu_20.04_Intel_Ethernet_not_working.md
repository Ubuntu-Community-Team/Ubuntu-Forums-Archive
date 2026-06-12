---
title: "Ubuntu 20.04 Intel Ethernet not working"
date: 2020-09-10
forum: Networking &amp; Wireless
---

### Post by mtannamala on 2020-09-10
Ubuntu 20.04 Ethernet not working

    I am using ubuntu 20.04, this network is working previous 18.04
    Code:

    `sudo lshw -C network`
    
    This is the result


    Code:

    *-network UNCLAIMED       
               description: Ethernet controller
               product: Ethernet Connection I1217-LM
               vendor: Intel Corporation
               physical id: 19
               bus info: pci@0000:00:19.0
               version: 04
               width: 32 bits
               clock: 33MHz
               capabilities: pm msi cap_list
               configuration: latency=0
               resources: memory:f7c00000-f2c1ffff memory:f7c3d0000-f7c3dfff ioport:f000(size=32)


    My kernel version is 5.4.0-42-generic

    I tried to install igb driver still same issue

Thinkserver TS140

---

