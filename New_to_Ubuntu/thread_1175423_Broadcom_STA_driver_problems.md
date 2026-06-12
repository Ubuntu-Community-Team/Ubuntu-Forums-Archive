---
title: "Broadcom STA driver problems"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by chucujaunty on 2009-06-01
Hi everybody,

I've just installed Ubuntu 9.04 Jaunty Jackalope in a Dell computer (Inspiron 1545) and there seem to be some problems with the wireless connection. Although the ethernet connection began working without problems since the beginning, I haven't been able to establish any wifi connection.

I've been reading a lot of posts, but I cannot figure out what the problem is. Any help would be appreciated.

In 'Hardware Controllers" option I can see that Ubuntu has installed a privative driver called "Broadcom STA". It also says it's currently in use.

The command lspci says (I'll only paste the part related to wireless device):

```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Dell Device 000c
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 24-00-a0-ff-ff-2c-0b-bc
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl
```And iwconfig says:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
```The command "sudo lshw -C network" says:

```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2c:a0:bc:0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:33:c8:30
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.129 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:59:76:cb:16:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```Although it seem to me that everything is ok, wifi-radar keeps on returning me a "eth1      Failed to read scan data : Invalid argument" message error.

Even the command "iwlist eth1 scanning" returns me a "eth1      Interface doesn't support scanning." error.

Do you think the problem is the Broadcom STA driver Ubuntu installed? I don't know what to do. As I said, any help or comment would be really appreciated.

Regards,

---

### Post by superprash2003 on 2009-06-01
add a sudo to the iwlist command and post outputs

---

### Post by janaha on 2009-06-01
@chucujaunty

I have the same card in a HP pavilion dv6000 and it worked flawless with the STA driver.The "hacked" drivers I previously used, had some connections/slow speed issues.

Just some info that the drivers worked with that card...

---

