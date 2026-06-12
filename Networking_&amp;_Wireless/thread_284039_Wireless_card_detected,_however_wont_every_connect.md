---
title: "Wireless card detected, however wont every connect."
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by jiberwabish on 2006-10-25
I noticed in another post they wanted these results so I'll show them right away.
===============================================================
ifconfig:
===============================================================
eth0      Link encap:Ethernet  HWaddr 00:02:3F:D2:00:14
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fed2:14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1541706 (1.4 MiB)  TX bytes:247772 (241.9 KiB)
          Interrupt:177

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)
===============================================================
iwconfig:
===============================================================
lo        no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:"FortKnox"
          Mode:Master  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

===============================================================
iwlist scan
===============================================================
lo        Interface doesn't support scanning.

ath0      Interface doesn't support scanning : Invalid argument

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


===============================================================
sudo /etc/init.d/networking restart
===============================================================
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:02:3f:d2:00:14
Sending on   LPF/eth0/00:02:3f:d2:00:14
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:02:3f:d2:00:14
Sending on   LPF/eth0/00:02:3f:d2:00:14
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 250151 seconds.

Listening on LPF/ath0/00:90:96:7b:32:42
Sending on   LPF/ath0/00:90:96:7b:32:42
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

===============================================================
sudo lspci
===============================================================
0000:00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 17)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)



===============================================================
sudo lshw
===============================================================
ubuntusatellite
    description: Notebook
    product: Satellite A30
    vendor: TOSHIBA
    version: PSA33C-154M4
    serial: 14333605K
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=D37658E3-4085-11D8-9E04-00023FD20014
  *-core
       description: Motherboard
       product: DFL10
       vendor: TOSHIBA
       physical id: 0
       version: Null
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.20 (01/02/2004)
          size: 101KB
          capacity: 448KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 1600MHz
          capacity: 3200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 8KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 447MB
          capacity: 1GB
        *-bank:0
             description: SODIMM DDR Synchronous [empty]
             physical id: 0
             slot: JP21
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: JP20
     *-pci
          description: Host bridge
          product: RS300 Host Bridge
          vendor: ATI Technologies Inc
          physical id: ea000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          resources: iomemory:ea000000-ebffffff iomemory:e8000000-e8000fff
        *-pci:0
             description: PCI bridge
             product: Radeon 9100 IGP AGP Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: RS300M AGP [Radeon Mobility 9100IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f0000000-f7ffffff ioport:9000-90ff iomemory:e8100000-e810ffff irq:161
        *-usb:0
             description: USB Controller
             product: OHCI USB Controller #1
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e8001000-e8001fff irq:177
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-27-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: OHCI USB Controller #2
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e8002000-e8002fff irq:177
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.15-27-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: EHCI USB Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e8003000-e8003fff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-27-386 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: ATI SMBus
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 17
             width: 32 bits
             clock: 66MHz
             resources: ioport:8060-806f iomemory:e8004000-e80043ff
        *-ide
             description: IDE interface
             product: ATI Dual Channel Bus Master PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE
             resources: ioport:8070-807f irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: TOSHIBA MK6021GAS
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: GA024A
                   serial: Z3N31264S
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 10001MB
                      capabilities: primary bootable
                 *-volume:1
                      description: HPFS/NTFS partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 26GB
                      capabilities: primary
                 *-volume:2
                      description: W95 Ext'd (LBA) partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 19GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-R2412
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1015
                   serial: Z349300367
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-isa UNCLAIMED
             description: ISA bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@02:02.0
                logical name: ath0
                version: 01
                serial: 00:90:96:7b:32:42
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11b
                resources: iomemory:e8200000-e820ffff irq:177
           *-network:1 DISABLED
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth0
                version: 10
                serial: 00:02:3f:d2:00:14
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
                resources: ioport:a000-a0ff iomemory:e8210000-e82100ff irq:177
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:e8211000-e8211fff irq:169
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ATI IXP AC97 controller
             resources: iomemory:e8004400-e80044ff irq:169
        *-communication
             description: Modem
             product: IXP AC'97 Modem
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@00:14.6
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master
             configuration: driver=ATI IXP MC97 controller
             resources: iomemory:e8004800-e80048ff irq:169
  *-battery
       description: Lithium Ion Battery
       product: PA3250U
       vendor: TOSHIBA
       physical id: 1
       version: 08/24/2003
       serial: 3658Q
       slot: 1st Battery
       capacity: 3900mWh
       configuration: voltage=14.8V
===============================================================
===============================================================


I dont know what any of that is, however I do see that it recognizes my Atheros wifi.

I've set up the network manager to enable my card and i set up the SSID and password for my network, it just wont ever connect.

Please help!
-J

---

### Post by jiberwabish on 2006-10-25
PS title should read  'Won't EVER connect.' not 'wont ever connect'.

---

### Post by tubasoldier on 2006-10-25
Have you installed the source from [http://madwifi.org](http://madwifi.org) ?  If not you will never get your Atheros card to connect. At least if I remember correctly, it has been a long time since I installed Ubuntu.

---

### Post by jiberwabish on 2006-10-25
I downloaded it however the installation procedure was WAY over my head.

I guess I'll have to slowly dig my way through it figuring it out.

Thanks for reply!
Still open to more suggestions, or help with madwifi
-J

---

