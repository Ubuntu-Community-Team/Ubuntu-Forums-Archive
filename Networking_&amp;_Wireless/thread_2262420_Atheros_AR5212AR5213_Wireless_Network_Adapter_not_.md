---
title: "Atheros AR5212/AR5213 Wireless Network Adapter not working."
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by david330 on 2015-01-24
I have dual-boot with Windows 7 and there it works.

lspci -vv:
```

04:01.0 Non-VGA unclassified device: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter (rev 01)
    !!! Invalid class 0000 for header type 02
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
    Region 0: Memory at <ignored> (32-bit, non-prefetchable)
    Bus: primary=00, secondary=00, subordinate=02, sec-latency=0
    Memory window 0: 00020000-001326ab
    Memory window 1: 82920022-02021020
    I/O window 0: 0000a830-00000023 [disabled]
    I/O window 1: 00000020-00000023 [disabled]
    BridgeCtl: Parity- SERR+ ISA- VGA- MAbort- >Reset- 16bInt- PostWrite-
    16-bit legacy interface ports at 0001

```

lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: bc:5f:f4:e2:0e:71
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-4 ip=192.168.2.16 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:f5a00000-f5a1ffff memory:f5a39000-f5a39fff ioport:f040(size=32)
  *-network UNCLAIMED
       description: FDDI network controller
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 mingnt=2
       resources: iomemory:829200220-82920021f

```

dmesg | grep ath
```

[    4.501803] ath5k 0000:04:01.0: cannot remap PCI memory region
[    4.501896] ath5k: probe of 0000:04:01.0 failed with error -5

```

Thanks.

---

