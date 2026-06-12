---
title: "Reinstalled 14.04 on laptop, now it doesn't recognize my wireless network card"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by matbluvenger on 2015-02-22
So I started going back to school and needed to bust out my old laptop. I haven't used it for a while and wanted to add some things that would make it more useful for school. Long story short, I did some stuff that made me think I should reinstall. When installing every other version of Ubuntu it detected the built-in laptop wireless NIC but now it won't. Here's the rundown on what happened to make the info easier:

[LIST]
[*]Dell Inspiron 3520 laptop
[*](Before problem) 14.04 LTS installed probably a year ago, dual-boot with Windows 7
[*]Reinstalled with 14.04.2 in the "/" partition to leave my files alone. Couldn't detect the NIC, couldn't read the files from the Windows partition like it could before
[*]Said screw it, formatted the whole thing and installed 14.04.2
[*]Can't detect NIC
[*]14.10, Lubuntu, and Ubuntu-Mate couldn't detect the NIC either
[*]Works with my tiny USB network adapter for a while but after enough activity it stays connected to the network but I can't go to any sites or ping anything
[*]Wired connection also works just fine
[/LIST]

Here's the output I get for ```
lshw -C network
``` with no extra adapter or wired connection:

```
*-network
   description: Network controller
product: BCM43142 802.11b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:07:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=bcma-pci-bridge latency=0
resources: irq:19 memory:f7c00000-f7c07fff
*-network
   description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 05
serial: e0:db:55:8e:09:26
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
configuration: broadcast=yes driver=r8169 latency=0 multicast=yes
resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

---

### Post by Hadaka on 2015-02-22
Hi, from a working wired connection please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

