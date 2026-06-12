---
title: "Sis191 Ethernet: link not detected?"
date: 2018-03-01
forum: Networking &amp; Wireless
---

### Post by iarspider2 on 2018-03-01
I was asked to give a new life to an old PC with Asus p5sd2-vm motherboard with SIS-191 ethernet controller. It was working perfectly under Windows XP, but refuses to work under Ubuntu (17.10). 

```

$ uname -a
Linux krugPC 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

$ lshw -C network
  *-network
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: enp0s4
       version: 02
       serial: 00:1d:60:c9:a7:f1
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=sis190 driverversion=1.4 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 memory:feafcc00-feafcc7f ioport:dc00(size=128)

$ dmesg | grep sis190
[    2.575828] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    2.577372] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    2.577376] sis190: 0000:00:04.0: Error EEPROM read 0
[    2.577379] sis190: 0000:00:04.0: Read MAC address from APC
[    2.648116] sis190: 0000:00:04.0: Atheros PHY AR8012 transceiver at address 1
[    3.392079] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    3.440401] sis190 0000:00:04.0 eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at ffff971f00006c00 (IRQ: 19), 00:1d:60:c9:a7:f1
[    3.440405] sis190 0000:00:04.0 eth0: GMII mode.
[    3.440417] sis190 0000:00:04.0 eth0: Enabling Auto-negotiation
[    3.506521] sis190 0000:00:04.0 enp0s4: renamed from eth0
[   39.952502] sis190 0000:00:04.0 enp0s4: mii ext = 0000
[   39.988262] sis190 0000:00:04.0 enp0s4: mii lpa=c5e1 adv=01e1 exp=000b
[   40.012135] sis190 0000:00:04.0 enp0s4: link on unknown mode
[   40.072311] sis190 0000:00:04.0 enp0s4: auto-negotiating...

$ ethtool enp0s4
Settings for enp0s4:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: off
    Current message level: 0x00000037 (55)
                   drv probe link ifdown ifup
    Link detected: no

```

I can see that the orange LED on the ethernet socket is on, and the LED on the switch it's connected to is also on. I have tried swapping cables, ports - nothing changes. Other devices connected to that switch work just fine. Any idea how can I get this card to work?

---

### Post by slickymaster on 2018-03-01
Thread moved to **Networking & Wireless** for a better fit

---

