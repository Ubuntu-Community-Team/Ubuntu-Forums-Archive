---
title: "“Activation of network connection failed” ethernet message under Ubuntu 18.04"
date: 2019-09-23
forum: Networking &amp; Wireless
---

### Post by statisticianlinux on 2019-09-23
[COLOR=#242729][FONT=Arial]I am currently running dual boot with Ubuntu 18.04 and Windows 10, and the ethernet connection is working in neither operating systems. Under Windows 10, it complains that "an ip address cannot be assigned", while under Ubuntu, it gives the "Activation of network connection failed" error.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Doing the command ```
sudo lshw -C network
``` yields

[/FONT][/COLOR]
```
*-network:0               
       description: Wireless interface
       product: Wireless-AC 9560 [Jefferson Peak]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 10
       serial: 50:76:af:62:2b:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-29-generic firmware=43.95eb4e97.0 ip=10.250.165.119 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:a4234000-a4237fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Ethernet Connection (7) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:a4200000-a421ffff

```

Does anyone have any idea how I can fix this? I can attach the pastebin as well of the wireless-info text file if that helos.

---

### Post by SeijiSensei on 2019-09-24
Since it fails on both sides, I'm guessing there's a problem with the DHCP server which is probably running on your router. Do you have other devices in your home that get valid network addresses when they boot?  Smartphones with wifi, for instance?

---

### Post by Yellow Pasque on 2019-09-26
```
network:1 UNCLAIMED
       description: Ethernet controller
       product: Ethernet Connection (7) I219-V
```

The "e1000e" module should be loaded for this adapter. What happens when you try and load it manually?
```
sudo modprobe -v e1000e
```

---

### Post by Autodave on 2019-09-28
Can we have some specs on your machine?

---

