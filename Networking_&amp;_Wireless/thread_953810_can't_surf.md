---
title: "can't surf"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by gianniman on 2008-10-20
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
eth0      Link encap:Ethernet  HWaddr 00:16:17:72:cd:7c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe72:cd7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:119046 (116.2 KB)  TX bytes:48251 (47.1 KB)
          Interrupt:19

---

