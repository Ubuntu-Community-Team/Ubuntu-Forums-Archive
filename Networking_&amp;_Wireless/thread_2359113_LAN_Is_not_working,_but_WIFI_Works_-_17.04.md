---
title: "LAN Is not working, but WIFI Works - 17.04"
date: 2017-04-20
forum: Networking &amp; Wireless
---

### Post by daggerx on 2017-04-20
```
andrew@andrew-K52F:~$ sudo lshw -c network
  *-network                 
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250 [Kilmer Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wls1
       version: 5f
       serial: 00:23:15:6f:23:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-19-generic firmware=41.28.5.1 build 33926 ip=192.168.1.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:32 memory:d2c00000-d2c01fff
  *-network DISABLED
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: ens5f5
       version: 03
       serial: 20:cf:30:d3:01:30
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 memory:d0400000-d0403fff ioport:a100(size=128) ioport:a000(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: enx64d4da1370a7
       serial: 64:d4:da:13:70:a7
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no
```

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] (rev 5f)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
04:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 05)

```

```
iwconfig
lo        no wireless extensions.

wls1      IEEE 802.11  ESSID:"Hittite_HD"  
          Mode:Managed  Frequency:5.26 GHz  Access Point: 00:78:CD:00:A2:53   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4866   Missed beacon:0

enx64d4da1370a7  no wireless extensions.

ens5f5    no wireless extensions.

```

Please help and thanks.

---

