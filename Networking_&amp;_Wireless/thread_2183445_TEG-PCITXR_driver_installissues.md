---
title: "TEG-PCITXR driver install/issues"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by InvadeD on 2013-10-24
Good Evening,

I'm having some issues in regards to upload speeds on ubuntu server, recently I've started to notice my upload speeds aren't going as high as it should be. I've confirmed on speed tests that my isp is fine. Till I realized it's possible ubuntu hasn't noticed the new nic installed not too long ago.


```
eth0      Link encap:Ethernet  HWaddr 00:14:d1:29:dc:78
          inet addr:192.168.2.21  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40197072 errors:0 dropped:59 overruns:0 frame:0
          TX packets:69093518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4225397289 (4.2 GB)  TX bytes:97112813479 (97.1 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:78758 (78.7 KB)  TX bytes:78758 (78.7 KB)

lspci -vv

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at d000 [size=256]
        Region 1: Memory at ef000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

*-network
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:14:d1:29:dc:78
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.21 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:d000(size=256) memory:ef000000-ef0000ff memory:40000000-4001ffff


```

I'm not too sure how to proceed further as I tried to install drivers but having no luck at all finding a guide as it's supposed to be a trendnet nic not realtek. Can someone assist on this pretty please? :confused:

---

### Post by InvadeD on 2013-10-25
bump someone please?

---

### Post by varunendra on 2013-10-26
> **InvadeD said:**
> Till I realized it's possible ubuntu hasn't noticed the new nic installed not too long ago.
....
.... it's supposed to be a trendnet nic not realtek.

Do you mean you have two NICs installed in the system? Or just confused between the name "Trendnet" and "Realtk"?

As far as I know, Trendnet DOES NOT manufacture network chips. They are just OEMs who take chips from manufacturers like realtek, ralink, intel etc. and just package them with other components to produce working cards/modules. The system will show these cards by the name of the vendor who manufactured the Chip, not who packaged it. Because it is the chip that talks to the system.

The outputs you posted show only one card. That is a Realtek card (chip) and seems to be working at its full capacity. The ifconfig stats show no significant errors *(59 packet drops against 40197072 received is NIL! And in upload there are no errors at all!!)*, and lshw output shows the connection speed to be 1Gb/s, which is its full capacity.

If you do have a second NIC installed, the system is not able to even 'see' it yet, check your BIOS settings and its physical connectivity at motherboard. And if you are talking about this same card in the posted outputs, it already has a suitable driver installed and everything regarding it looks solid.

By the way, how much speed you are expecting and how do you know it is not delivering that much? Any practical observations that suggest it is not fast enough?

---

### Post by howefield on 2013-10-26
Thread moved to the "Networking & Wireless" forum.

---

