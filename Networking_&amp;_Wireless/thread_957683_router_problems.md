---
title: "router problems"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by gianniman on 2008-10-24
Hi, I've got ubuntu 8.04 I've got an msi k8n sli motherboard and I'm trying to setup the internet connection (that works perfectly under xp) via a router.

I did the setup using network-admin and I setup a static ipaddress (192.168.1.6), the gateway (192.168.1.1) and the dns (using the router address, the opendns ones and the provider supplide ones).

After all these operations using firefox I am only able to surf on mozilla.org website and apparently no other site. In firefox I am not able to connect to the router.....

Doing a ping in the shell the result is correct for all sites, including the router, which I can telnet to.

One of the network icons in the taskbar (don't remember which one) when I try to configure eth0, gives me this error:
"the interface does not exist.... check that it is correctly typed......."

thanks for the help


here is the output

Sudo lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)


ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:16:17:72:cd:7c
inet addr:192.168.1.6 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::216:17ff:fe72:cd7c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:156 errors:0 dropped:0 overruns:0 frame:0
TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:119046 (116.2 KB) TX bytes:48251 (47.1 KB)
Interrupt:19

---

### Post by cariboo on 2008-10-24
Can you post the output of:

```
sudo lshw -C bridge
```

Your nic shows up as a bridge device so using **-C network** won't work. I have have an MSI mb and mine is the same way, except of course it works. :)

Jim

---

### Post by gianniman on 2008-10-26
Hi, thanks for your suggestion, here is the output:

  *-isa
       description: ISA bridge
       product: CK804 ISA Bridge
       vendor: nVidia Corporation
       physical id: 1
       bus info: pci@0000:00:01.0
       version: a4
       width: 32 bits
       clock: 66MHz
       capabilities: isa bus_master
       configuration: latency=0
  *-pci:0
       description: PCI bridge
       product: CK804 PCI Bridge
       vendor: nVidia Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pci subtractive_decode bus_master
  *-bridge
       description: Ethernet interface
       product: CK804 Ethernet Controller
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a3
       serial: 00:16:17:72:cd:7c
       size: 100000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.6 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-pci:1
       description: PCI bridge
       product: CK804 PCIE Bridge
       vendor: nVidia Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: a3
       width: 32 bits
       clock: 33MHz
       capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
       configuration: driver=pcieport-driver
  *-pci:2
       description: PCI bridge
       product: CK804 PCIE Bridge
       vendor: nVidia Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: a3
       width: 32 bits
       clock: 33MHz
       capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
       configuration: driver=pcieport-driver
  *-pci:3
       description: PCI bridge
       product: CK804 PCIE Bridge
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a3
       width: 32 bits
       clock: 33MHz
       capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
       configuration: driver=pcieport-driver
  *-pci:4
       description: PCI bridge
       product: CK804 PCIE Bridge
       vendor: nVidia Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       version: a3
       width: 32 bits
       clock: 33MHz
       capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
       configuration: driver=pcieport-driver
  *-pci:5
       description: Host bridge
       product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
       vendor: Advanced Micro Devices [AMD]
       physical id: 100
       bus info: pci@0000:00:18.0
       version: 00
       width: 32 bits
       clock: 33MHz
  *-pci:6
       description: Host bridge
       product: K8 [Athlon64/Opteron] Address Map
       vendor: Advanced Micro Devices [AMD]
       physical id: 101
       bus info: pci@0000:00:18.1
       version: 00
       width: 32 bits
       clock: 33MHz
  *-pci:7
       description: Host bridge
       product: K8 [Athlon64/Opteron] DRAM Controller
       vendor: Advanced Micro Devices [AMD]
       physical id: 102
       bus info: pci@0000:00:18.2
       version: 00
       width: 32 bits
       clock: 33MHz
  *-pci:8
       description: Host bridge
       product: K8 [Athlon64/Opteron] Miscellaneous Control
       vendor: Advanced Micro Devices [AMD]
       physical id: 103
       bus info: pci@0000:00:18.3
       version: 00
       width: 32 bits
       clock: 33MHz
       configuration: driver=k8temp module=k8temp

---

### Post by ianhaycox on 2008-10-26
Daft question, but in Firefox the File->Work Offline option is not checked is it ?

---

### Post by gianniman on 2008-10-26
Yes, it's not checked, thanks anyway

---

