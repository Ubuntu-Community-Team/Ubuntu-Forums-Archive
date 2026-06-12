---
title: "Ubuntu can not detect network adapter cause it doesn't find driver"
date: 2022-07-09
forum: Networking &amp; Wireless
---

### Post by federikowsky on 2022-07-09
after updating the nvidia driver, it seems that something went wrong during the update, the ethernet or wifi driver is no longer detected, nor if I use a usb wifi adapter can I use the internet to update. If I boot with an older kernel everything works fine, I have updated && updated the system. When I reboot with the latest kernel nothing has changed. this is output of "sudo lshw -C network" command:
```
*-network UNCLAIMED
description: Network controller
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fc400000-fc403fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fc200000-fc2fffff memory:fc300000-fc303fff
```

what should I do ?

Ps. when system boot with latest kernel give me this error:

[COLOR=#232629][FONT=-apple-system]"__common_interrupt: 1.55 - 10.55 No irq handler for vector" 

why this ?[/FONT][/COLOR]

---

### Post by chili555 on 2022-07-09
What is the kernel version where it does not work?

```
uname -r
```

While booted into the version where it does work, please run:

```
sudo dpkg -s linux-modules-extra-XXXX | grep Status
```... where XXX is the kernel version you found where is does not work. If you find that it is not installed, please run:

```
sudo apt update
sudo apt install --reinstall linux-modules-extra-XXXX
```Again, where XXX is the kernel version you found where is does not work.

Reboot.

---

