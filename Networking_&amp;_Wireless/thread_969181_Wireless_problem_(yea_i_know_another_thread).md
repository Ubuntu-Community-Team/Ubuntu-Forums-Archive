---
title: "Wireless problem (yea i know another thread)"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by ElysiumY2K on 2008-11-03
Well i decided to download and install Ubuntu 8.10 the other day (upgrading from Linux). I recently brought a Asus Eee PC 901 Linx.

Like the title said, i have not wireless internet. There is no option for wireless (only for Wired Network and i can connect to the internet using a cat5 wire).

My wireless router does work (since all my other laptops and my iPhone can connect to it). Just can't seem to work out what's wrong...

I have a feeling i may need to update my driver wireless driver, since holding FN + F2 seems to do nothing. My Network Controller is a RaLink Device 0781 (if that's any help) and i've been searching around for an answer a while now but with no luck.

Any help is appreciated. Thanks.

---

### Post by mister_pink on 2008-11-03
Check out [www.array.org/ubuntu](www.array.org/ubuntu)

There is a custom kernel there with installation instructions. This will sort it out.

---

### Post by superprash2003 on 2008-11-03
if you still have trouble go to the terminal and type lshw -C network and post output here

---

### Post by ElysiumY2K on 2008-11-03
I went to that site minster_pink and tried to install the custom kernel, but still no luck.

superprash heres the lshw -C network:

[PHP]*-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:09:85:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e ip=192.168.1.64 latency=0 module=atl1e multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:6b:99:2b:23:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[/PHP]

---

### Post by mafi01 on 2008-11-03
Hi, I haven't got an Eee, but my wireless doesn't work with a similar lspci output. So maybe someone can give advice on this?

Thanks.

*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:e0:91:38:05:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.35 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:4b:dd:bf:cf:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mister_pink on 2008-11-04
> **ElysiumY2K said:**
> I went to that site minster_pink and tried to install the custom kernel, but still no luck.


Could you post the output of "uname -r"

---

### Post by prematurebaby on 2008-11-04
I too had problems with wireless with the upgrade to 8.10. I'm sure alot of people did too. I fixed it of course. I found everything I need in this thread. [http://ubuntuforums.org/showthread.php?t=968797]("http://ubuntuforums.org/showthread.php?t=968797")
I'm not sure if we had the same problem. But this is all I can give you.

---

