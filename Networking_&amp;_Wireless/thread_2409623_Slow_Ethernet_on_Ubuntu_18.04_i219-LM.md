---
title: "Slow Ethernet on Ubuntu 18.04 i219-LM"
date: 2019-01-04
forum: Networking &amp; Wireless
---

### Post by takeawaydave on 2019-01-04
Fresh install of Ubuntu 18.04 on Dell Precision 7510 laptop.

```
    $ lspci  | grep -i net
    00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
    02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
    $ lsmod | grep 1000
    e1000e                249856  0
    ptp                    20480  1 e1000e
```


More detail:

```
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
	Subsystem: Dell Ethernet Connection (2) I219-LM
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 134
	Region 0: Memory at dd400000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee00418  Data: 0000
	Capabilities: [e0] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: e1000e
	Kernel modules: e1000e
```


and an extract of lshw:

 ```
$ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 3a
       serial: e4:a4:71:19:d7:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-43-generic firmware=34.0.1 ip=192.168.1.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:137 memory:dd300000-dd301fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 28:f1:0e:0e:86:6a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:134 memory:dd400000-dd41ffff

```


The Network Settings show connected but only 10 Mb/s/

---

### Post by takeawaydave on 2019-01-05
Steps towards fixing:

```
apt install ethtool
```

set configuration attributes:

```
ethtool -s enp0s31f6 speed 1000 duplex full autoneg off
```

With a re-pluggin of cable however this drops back down to 10 Mb/s and the above command needs to be re-run.

What is the syntax to set these attributes in my etc/NetworkManager/system-connections/Wired\ connection\ 1 file or somewhere else ?

---

### Post by takeawaydave on 2019-01-05
Strange issue seems more to be down to the auto negotiation doesn't work between my intel nic port and the unifi switch port.

If I set the switch port to manual negotiation and 1gB/S then reconnect fine.... expert opinion most appreciated.

---

