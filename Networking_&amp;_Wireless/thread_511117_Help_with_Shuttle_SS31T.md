---
title: "Help with Shuttle SS31T"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by sheetzam on 2007-07-27
Have our Shuttle SS31T working great except for the built in networking.
This is on feisty fawn with2 .6.20-16-server #2 kernel.
Any clues as to how to go about troubleshooting this?

Here's output from lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 662 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 04)
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)
```


relevant piece of kernel log file:
```
Jul 27 11:14:14 iteron kernel: [346420.866615] sis190 Gigabit Ethernet driver 1.2 loaded.
Jul 27 11:14:14 iteron kernel: [346420.866667] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 22
Jul 27 11:14:14 iteron kernel: [346420.906484] 0000:00:04.0: Read MAC address from EEPROM
Jul 27 11:14:15 iteron kernel: [346421.127141] 0000:00:04.0: Unknown PHY transceiver at address 1.
Jul 27 11:14:16 iteron kernel: [346422.493487] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at f89ae000 (IRQ: 22), 00:30:1b:80:6d:59
Jul 27 11:14:16 iteron kernel: [346422.493495] eth1: GMII mode.
Jul 27 11:14:16 iteron kernel: [346422.493500] eth1: Enabling Auto-negotiation.
Jul 27 11:14:16 iteron kernel: [346422.663979] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul 27 11:18:28 iteron kernel: [346890.404776] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by noob12 on 2007-07-27
I think that's normal if there is no cable plugged into that port.  I'm assuming there is?

Do you have link state LEDs on that you can examine on the card as well as whatever switch/hub it is connected to?

---

### Post by sheetzam on 2007-07-27
Link lights on at both ends, and the switch believes it's a gigabit connection, as it should.

---

### Post by noob12 on 2007-07-27
Can you provide the output of the following?

> 
sudo ethtool eth1


You may need to install the ethtool package first (aptitude install ethtool)

> 
ifconfig -a


> 
cat /etc/network/interfaces


---

### Post by sheetzam on 2007-08-01
sudo ethtool eth1:

```
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000037 (55)
        Link detected: no
```

ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:B7:1F:97  
          inet addr:xx.xx.xx.92  Bcast:xx.xx.xx.95  Mask:255.255.255.240
          inet6 addr: fe80::2a0:c9ff:feb7:1f97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:438085 (427.8 KiB)  TX bytes:200621 (195.9 KiB)

eth1      Link encap:Ethernet  HWaddr 00:30:1B:80:6D:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3750 (3.6 KiB)  TX bytes:3750 (3.6 KiB)
```


cat /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

While this shows that it thinks there is no link detected, the link lights on the nic and the switch are definitely lit.  Also, this is a Gigabit capable interface, but it's only reporting 100mb capable.
When I plug it in to a 100MB switch, it still reports no link detected.

I believe the problem is some basic incompatibility in the driver, or the wrong device is being detected.  I fairly certain it's not some basic configuration problem, but I could be wrong.

---

