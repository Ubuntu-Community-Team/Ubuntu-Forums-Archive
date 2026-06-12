---
title: "Via-rhine don't up"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by gianrubio on 2007-04-05
Hello:

I'm running ubuntu

```
uname -a
Linux 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 i686 GNU/Linux
root@servidor:~#
```

and have a problem to up  via-rhine .

my dmesg

```
[42949389.290000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[42949389.290000] **** SET: Misaligned resource pointer: cea5cea2 Type 07 Len 0
[42949389.290000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[42949389.290000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[42949389.290000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IR
Q 201
[42949389.290000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[42949389.290000] eth2: VIA Rhine II at 0x1e000, 00:0d:87:7b:2d:60, IRQ 201.
[42949389.290000] eth2: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
```

```
root@servidor:~# lsmod |grep via_rhine
via_rhine              26756  0
mii                     7040  4 sis900,via_rhine,8139cp,8139too
root@servidor:~#
```

```
llspci -vv

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB
2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR-
 <PERR-
        Latency: 32 (750ns min, 2000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 201
        Region 0: I/O ports at e000 [size=256]
        Region 1: Memory at e3003000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

```
ifconfig -a (don't report eth2)
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:0A:A9:AC
          inet addr:192.168.1.203  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe0a:a9ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:197300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291630 errors:0 dropped:0 overruns:8 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14752539 (14.0 MiB)  TX bytes:407983395 (389.0 MiB)
          Interrupt:193 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:0D:87:7B:2D:60
          inet addr:192.168.0.203  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe7b:2d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11564008 errors:0 dropped:314 overruns:0 frame:0
          TX packets:30243488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1575887105 (1.4 GiB)  TX bytes:4099136184 (3.8 GiB)
          Interrupt:201 Base address:0xe000

eth3      Link encap:Ethernet  HWaddr 00:30:4F:2E:FE:B1
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6024 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:923654 (902.0 KiB)  TX bytes:923654 (902.0 KiB)

```


```
root@servidor:~# ifconfig eth2 up
eth2: ERROR while getting interface flags: No such device
root@servidor:~#
```

How i fix it?
Thanks

---

