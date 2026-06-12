---
title: "BCM5723 DUAL PORT second port doesn't run in 18.04 LTS"
date: 2018-07-09
forum: Networking &amp; Wireless
---

### Post by castilhosr on 2018-07-09
Hi, I have a 18.04 LTS fresh install in HP Proliant server.
So, this server has a BCM5723 DUAL PORT ethernet adapter, but, only one port has identified by linux.
How can I do to see both ports ?

**ifconfig**
enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet x.y.z.t  netmask 255.255.252.0  broadcast x.y.z.255
        RX packets 467757  bytes 81053756 (81.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20951  bytes 1877260 (1.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2904  bytes 177454 (177.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2904  bytes 177454 (177.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[B]
 lshw -C Network[/B]
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: 78:e7:d1:73:b8:ba
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.137 duplex=full firmware=5723-v3.35, IPMILITE v8.02  ip=x.y.z.t latency=0 link=yes multicast=yes port=twisted pair  speed=1Gbit/s
       resources: irq:40 memory:fbef0000-fbefffff

**lspci -vvnn**
04:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)
        Subsystem: Hewlett-Packard Company NC107i Integrated PCI Express Gigabit Server Adapter [103c:705d]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 40
        Region 0: Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [40] Vital Product Data
                Product Name: HP NC107i PCIe Gigabit Server Adapter
                Read-only fields:
                        [PN] Part number: BCM95723
                        [EC] Engineering changes: 106679-15
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 34 65 34
                        [RV] Reserved: checksum good, 37 byte(s) reserved
                Read/write fields:
                        [YA] Asset tag: XYZ01234567
                        [RW] Read-write area: 107 byte(s) free
                End
        Capabilities: [60] Vendor Specific Information: Len=6c <?>
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee004b8  Data: 0000
        Capabilities: [cc] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset- SlotPowerLimit 10.000W
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag+ PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <1us, L1 <64us
                        ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [13c v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [160 v1] Device Serial Number 78-e7-d1-ff-fe-73-b8-ba
        Capabilities: [16c v1] Power Budgeting <?>
        Kernel driver in use: tg3
        Kernel modules: tg3

---

### Post by StrategV on 2019-05-23
[COLOR=#000000]Hi, I have the same problem with Ubuntu Server 18.04 LTS fresh install in HP Proliant ML150 G6 server.
[/COLOR][COLOR=#000000]NC107i Integrated PCI Express Gigabit Server Adapter (on [/COLOR][COLOR=#000000]Broadcom NetXtreme BCM5723 Gigabit Ethernet PCIe chip) has Dual Port, [/COLOR][COLOR=#000000]but only one port has identified by OS.
[/COLOR]&#8203;The printouts of the commands are identical (with a few exceptions).
Both ports worked fine on the old version Ubuntu Server 10.04 LTS.

I would be very grateful if someone could help with the solution of this problem.

---

