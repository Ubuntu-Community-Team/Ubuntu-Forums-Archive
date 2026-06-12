---
title: "Wireless adapter &quot;disappeared&quot; from my Lenovo 3000 N200"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by nchankov on 2008-06-10
Hi,

today I've seen there are some software updates and I just start them. Look like they also affect my Kernel, because I was with 2.6.24-17 while now I am with 2.6.24-18.

After the restart, my wireless card was "disappeared" and I cannot use it. On the Network Icon I can see only Wired Network and that's it. I suspect it comes from the kernel, but I really dont know how to see or solve the issue.

Using the command:
sudo lshw -C network

return me this output:
*-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:0f:b0:d5:33:2c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s



Is there somebody who experienced such problem?

Please help me :(

Thank you in advance
Nik

---

### Post by nchankov on 2008-06-10
Ok, I found the reason

instead of normal - 2.6.24-18-generic Kernel I was forced /from Grub/ to use 2.6.24-18-server. Switching by grub to generic solve the wireless problem.

Strange why this is happened I installed Ubuntu Desktop edition on my computer, so why I should have server - dont know.

Anyway, hope this helps somebody

---

