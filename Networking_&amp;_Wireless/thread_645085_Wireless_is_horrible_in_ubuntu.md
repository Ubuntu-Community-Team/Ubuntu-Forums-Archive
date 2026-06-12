---
title: "Wireless is horrible in ubuntu"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by MONODA on 2007-12-19
Hi after many problems in ubuntu I decided to renstall for the 4th time. After that I did not install ANTHING at all except hal of the updates. The reason I only installed half of them was becase thats all I was able to do becuase I was disconected from m wireless network. I tried to restart to and reconnect but could not. What happens when I try to connect is  click on the network but nothing happens, I tried connecting manualy also. Also the network seting windows also crashes, I hvent been able to view it once. What is going on I really need help I reall want this to work.

---

### Post by chalewa on 2007-12-19
what kinda wireless card do you have?

---

### Post by MONODA on 2007-12-20
I am not sure but wireless has worked fine before.

---

### Post by Presto123 on 2007-12-20
It's a bit challenging without the card info. I have been posting this basic question all night tonight (LOL) so, I feel a little redundant, but...

1) It worked for a bit in Ubuntu? 
2) Did you enable it in "Restricted Drivers Manager"?

Not wanting to make you feel stupid here, it's just to make sure those two are covered.

---

### Post by ugm6hr on 2007-12-20
> **MONODA said:**
> I am not sure but wireless has worked fine before.

The following will tell you what card you have, and what driver is being used:
```
lspci
lshw -C network
```

Post the outputs here so someone can help.

Also - what encryption are you using?  And are you using Ubuntu 7.10?

---

### Post by MONODA on 2007-12-20
It worked perfectly before and it is working again now and yes I enabled the driver. The driver I am using is Intel(R) PRO/Wireless 3945 Network Connection driver for Linux.

---

### Post by MONODA on 2007-12-20
I got this:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:0b:f4:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.2.37 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:1b:24:0c:fa:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 module=e1000 multicast=yes

I am using 7.10 but have not installed all the updates yet because they stopped downloading half way through

---

