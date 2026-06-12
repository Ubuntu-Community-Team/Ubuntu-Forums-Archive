---
title: "Wireless Connection fails"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by kuberprok on 2006-10-19
Newbie here,

I Installed this magic OS but have not been able to connect wirelessly.

I can connect with my networkcable straight to my router, this is way I can ask this here.

But by using a USB wireless card, an Inventel one, it seems impossible.
I tried to look at various other threads but with no luck, can some-one be so kind to take me through the whole process?


Thanks again
;)

---

### Post by wieman01 on 2006-10-19
Please run these commands from a terminal window & post the output:
> ifconfig
> iwconfig
> iwlist scan
> sudo /etc/init.d/networking restart
> route
> sudo gedit /etc/network/interfaces
> sudo lspci
> sudo lshw
Then we'll see what's going on. Also tell me a bit more about your network: DHCP vs. Static IP, encryption (e.g. WEP, WPA), etc.

---

### Post by kuberprok on 2006-10-24
Thank you for your reply

I am using WEP

How do I copy all the Terminal output to this forum? If I do shift+CtrlC it only copies one line.


Thanks again

---

### Post by wieman01 on 2006-10-24
Just mark the text you want to copy with the mouse pointer (pressing the left button, holding it, and pulling the pointer horizontally & vertically). That's it. To paste you need to press the mouse-wheel (or both button if you don't happen to have a mouse-wheel).

If you have no internet connection, simple paste the stuff into a text file and copy it over to the other machine using a USB storage device.

---

### Post by kuberprok on 2006-10-24
Hi

There you go!

Thanks again!

**albertus@albertus-laptop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:08:02:03:1F:28
          inet addr:192.168.1.93  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe03:1f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2437 (2.3 KiB)  TX bytes:2496 (2.4 KiB)
          Interrupt:11 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:0B:6B:A1:50:89
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

**albertus@albertus-laptop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Wanadoo-3470"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

albertus@albertus-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

**albertus@albertus-laptop:~$ sudo /etc/init.d/networking restart**
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:02:03:1f:28
Sending on   LPF/eth0/00:08:02:03:1f:28
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0b:6b:a1:50:89
Sending on   LPF/eth1/00:0b:6b:a1:50:89
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:08:02:03:1f:28
Sending on   LPF/eth0/00:08:02:03:1f:28
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.93 -- renewal in 35107 seconds.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0b:6b:a1:50:89
Sending on   LPF/eth1/00:0b:6b:a1:50:89
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
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
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ][B]
albertus@albertus-laptop:~$ route[/B]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         WANADOO-3470    0.0.0.0         UG    0      0        0 eth0
albertus@albertus-laptop:~$ sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Wanadoo-3470
wireless-key restricted 4FA7AE8D6F8AADF98EC5B0AC87

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

albertus@albertus-laptop:~$ sudo lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 42)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
albertus@albertus-laptop:~$ sudo lshw
albertus-laptop
    description: Computer
    product: Presario 705EA 470023-560
    vendor: Compaq
    version: 0F03
    serial: 1V1BKDH8V4JM
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
  *-core
       description: Motherboard
       product: 0760h
       vendor: Compaq
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 4.06CJ15 (10/05/2001)
          size: 105KB
          capacity: 192KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket A
          size: 498MHz
          capacity: 2GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capabilities: asynchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 384MB
          capacity: 1536MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: ec000000
          bus info: pci@00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e8100000-e817ffff iomemory:f0000000-f7ffffff irq:5
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:1840-184f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HITACHI_DK23CA-20
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 00H1A0J1
                   serial: 123JZZ
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 17GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 807MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-R2002
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1Q35
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: Cohiba 3887 rev0
                   vendor: GlobespanVirata
                   physical id: 1
                   bus info: usb@1:1
                   version: 10.20
                   capabilities: usb-2.00
                   configuration: driver=islusb maxpower=500mA speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             resources: irq:10
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:1000-10ff ioport:1854-1857 ioport:1850-1853 irq:5        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:e8000000-e800ffff ioport:1858-185f irq:4
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:ffbfe000-ffbfefff irq:11
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth0
             version: 10
             serial: 00:08:02:03:1f:28
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.93 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:1400-14ff iomemory:e8010000-e80100ff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0b:6b:a1:50:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.

---

### Post by wieman01 on 2006-10-24
> albertus@albertus-laptop:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 No scan results
sit0 Interface doesn't support scanning.
That's not a good sign. If your driver was installed correctly, there should be scan results.

What card have you got? And what have you done to install the drivers?

---

### Post by kuberprok on 2006-10-24
Hi

The CD I got from my ISP doesn't work on Linux. 

It is a USB card on my laptop. Inventel model: UR054g(R01) V1.1

I don't have any paper work with it, when I used it in my laptop when I was still runnig XP. it work well.

Sorry to be so criptic but this is all I have!

---

### Post by wieman01 on 2006-10-24
Ok, can you do one more thing please:
> lsusb
Want to see if your USB device is recognized.

Then we'll to use "ndiswrapper" which is a piece of software that let's you install your Windows driver. It's fairly simply to do that... Are you in?

---

### Post by kuberprok on 2006-10-25
Hi

Thanks for your reply!

I'll have a look asap and get back to you!

---

### Post by kuberprok on 2006-10-25
This is the output

~$ lsusb
Bus 001 Device 002: ID 1435:0427
Bus 001 Device 001: ID 0000:0000
~$

---

### Post by wieman01 on 2006-10-25
This won't tell me if it has been recognized or not. Can you identify your USB device when you run 'lshw'? Do you see it?

---

### Post by kuberprok on 2006-10-26
Hi

When I look in Device Manager, I can see the device there, when installed in XP it comes up with the same name ie, Cohiba 3887 rev0.

When click on it in DM it just says unknown in all the fields.


Here is the lshw output

I appreciate your help!


lsalbertus@presario700:~$ lshw
WARNING: you should run this program as super-user.
presario700
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 368MB
     *-cpu
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.6.2
          size: 498MHz
          capacity: 498MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: ec000000
          bus info: pci@00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e8100000-e817ffff iomemory:f0000000-f7ffffff irq:5
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:1840-184f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: TOSHIBA MK6015MAP
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 5729MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TOSHIBA DVD-ROM SD-R2002
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                  [B] description: Generic USB device
                   product: Cohiba 3887 rev0
                   vendor: GlobespanVirata
                   physical id: 1
                   bus info: usb@1:1
                   version: 10.20
                   capabilities: usb-2.00
                   configuration: driver=islusb maxpower=500mA [/B]speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             resources: irq:10
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:1000-10ff ioport:1854-1857 ioport:1850-1853 irq:5        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:e8000000-e800ffff ioport:1858-185f irq:4
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:ffbfe000-ffbfefff irq:11
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth0
             version: 10
             serial: 00:08:02:03:1f:28
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too ip=192.168.1.93 multicast=yes
             resources: ioport:1400-14ff iomemory:e8010000-e80100ff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:0b:6b:a1:50:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

---

### Post by wieman01 on 2006-10-26
Ok, that's good news at least. It seems we need to start using "ndiswrapper". Do you have all Windows drivers on hand? We need them. I'll work out the exact steps tonight & guide you through it.

See you later!

---

### Post by kuberprok on 2006-10-26
Let me put it this way, I have all the cds sent to me by the ISP.
This in the folder "driver"

/media/cdrom0/Drivers/USB/BlueDSL.inf
/media/cdrom0/Drivers/USB/dw200-0A5C.inf
/media/cdrom0/Drivers/USB/dw200-0F4F.inf
/media/cdrom0/Drivers/USB/InventelGateway.inf
/media/cdrom0/Drivers/USB/resc_dwb.sys
/media/cdrom0/Drivers/USB/RescueDrv.inf
/media/cdrom0/Drivers/USB/rndismp.sys
/media/cdrom0/Drivers/USB/RNDISMPK.sys
/media/cdrom0/Drivers/USB/rndismpm.sys
/media/cdrom0/Drivers/USB/rndismpw.sys
/media/cdrom0/Drivers/USB/usb8023.sys
/media/cdrom0/Drivers/USB/usb8023k.sys
/media/cdrom0/Drivers/USB/usb8023m.sys
/media/cdrom0/Drivers/USB/usb8023w.sys
 

These are all the folders on the cd
/media/cdrom0/All
/media/cdrom0/Drivers
/media/cdrom0/EN
/media/cdrom0/Inst
/media/cdrom0/WanadooUK
/media/cdrom0/AUTORUN.INF
/media/cdrom0/Flow.xml
/media/cdrom0/install.swf
/media/cdrom0/Install.cfg
/media/cdrom0/Install.exe
/media/cdrom0/local.xml
/media/cdrom0/Setup.exe
/media/cdrom0/Version.dat


Thanks again

---

### Post by Cynical on 2006-10-26
Heres a translated guide for you.

[http://64.233.179.104/translate_c?hl=en&u=http://lea-linux.org/cached/index/Trucs:Oldid%3D657.html&prev=/search%3Fq%3DUR054g%2Binventel%26start%3D10%26hl%3Den%26lr%3D%26safe%3Doff%26sa%3DN](http://64.233.179.104/translate_c?hl=en&u=http://lea-linux.org/cached/index/Trucs:Oldid%3D657.html&prev=/search%3Fq%3DUR054g%2Binventel%26start%3D10%26hl%3Den%26lr%3D%26safe%3Doff%26sa%3DN)

---

### Post by wieman01 on 2006-10-26
Good. These files will do. Talk to you later then!

N.B.: Can you check out the guide that Cynical has mentioned here?

---

### Post by kuberprok on 2006-10-26
> **Cynical said:**
> Heres a translated guide for you.

[http://64.233.179.104/translate_c?hl=en&u=http://lea-linux.org/cached/index/Trucs:Oldid%3D657.html&prev=/search%3Fq%3DUR054g%2Binventel%26start%3D10%26hl%3Den%26lr%3D%26safe%3Doff%26sa%3DN](http://64.233.179.104/translate_c?hl=en&u=http://lea-linux.org/cached/index/Trucs:Oldid%3D657.html&prev=/search%3Fq%3DUR054g%2Binventel%26start%3D10%26hl%3Den%26lr%3D%26safe%3Doff%26sa%3DN)

Hi

The link is in French and it's greek to me!

I Tried to translate the page with google but it didn't make sense, can you send me the English version of that?

Thanks

---

### Post by wieman01 on 2006-10-26
Ok, let's go ahead then. We basically follow this guide: [http://https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("http://https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

1. Please install "ndiswrapper-utils" which you find in the repository (Synapptic).
2. That done, please tell which driver file (*.INF) is the right one... There are a couple.

---

### Post by wieman01 on 2006-10-26
Next steps are...

1. Make folder in home (you can delete it after the installation):
> mkdir ~/Driver
2. Copy driver files:
> cp /media/cdrom0/Drivers/USB/* ~/Driver/
3. Deploy driver (replace [COLOR="Red"]dw200-0F4F.inf[/COLOR] with the right one):
> sudo ndiswrapper -i ~/Driver/[COLOR="Red"]dw200-0F4F.inf[/COLOR]
4. Check if driver has been loaded successfully (post output):
> ndiswrapper -l
5. Loading driver module:
> sudo depmod -a
sudo modprobe ndiswrapper
6. Loading module at startup:
> sudo ndiswrapper -m
7. Then restart & post your "interfaces" file.

---

### Post by kuberprok on 2006-10-26
Hi
1. Done
2. i think it's dw200-of4f

---

### Post by wieman01 on 2006-10-26
> **kuberprok said:**
> Hi
1. Done
2. i think it's dw200-of4f
Ok, I have replace the relevant section in my previous post ("dw200-0F4F").

---

### Post by kuberprok on 2006-10-26
I copied it in that folder, but after sudo ndswrapper -i ~/Driver/dw200-0F4F.inf output is

coun't copy line 135

---

### Post by wieman01 on 2006-10-26
> **kuberprok said:**
> [QUOTE=wieman01;1666150]Next steps are...



2. Copy driver files:

missing destination file operand after
What's the trouble?

---

### Post by kuberprok on 2006-10-26
4. invalid driver

---

### Post by wieman01 on 2006-10-26
Ok, can you do all the commands one by one & post the output for each step? Then I can validate them & see what's going on.

---

### Post by kuberprok on 2006-10-26
albertus@presario700:~/Driver$ sudo ndiswrapper -i ~/Driver/dw200-0F4F.inf dw200-0f4f is already installed. Use -e to remove it
albertus@presario700:~/Driver$

---

### Post by kuberprok on 2006-10-26
Installed ndis drivers:
dw200-0f4f      invalid driver!

---

### Post by wieman01 on 2006-10-26
> **kuberprok said:**
> albertus@presario700:~/Driver$ sudo ndiswrapper -i ~/Driver/dw200-0F4F.inf dw200-0f4f is already installed. Use -e to remove it
albertus@presario700:~/Driver$
What does this say?
> ndiswrapper -l

---

### Post by wieman01 on 2006-10-26
> **kuberprok said:**
> Installed ndis drivers:
dw200-0f4f      invalid driver!
Are all other driver files (e.g. *.sys) also in the same folder as the *.inf file? That's a must.

---

### Post by kuberprok on 2006-10-26
invalid driver

---

### Post by kuberprok on 2006-10-26
No, sorry

Should I copy it in there?

---

### Post by wieman01 on 2006-10-26
> **kuberprok said:**
> No, sorry

Should I copy it in there?
All files please. Yes. Then remove the driver (ndiswrapper -e file_name) and reinstall it.

---

### Post by kuberprok on 2006-10-26
albertus@presario700:~$ ndiswrapper -e dw200-0f4f.inf
Driver dw200-0f4f.inf is not installed.Use -l to list installed drivers

albertus@presario700:~$ ndiswrapper -l
Installed ndis drivers:
dw200-0a5c      invalid driver!
dw200-0f4f      invalid driver!
inventelgateway invalid driver!

---

### Post by wieman01 on 2006-10-26
> ndiswrapper -e dw200-0f4f]
No *.INF extension. Are your sure these are the right drivers? Are the *.SYS files also in the same folder? They have to.

---

### Post by kuberprok on 2006-10-26
ndiswrapper -e dw200-0f4f
Can't remove directory /etc/ndiswrapper/dw200-0f4f (Permission denied) at /usr/sbin/ndiswrapper line 166
albertus@presario700:~$


I am not sure, but it is the ones MS XP used and its all I have.. 

The sys files are all in there

---

### Post by wieman01 on 2006-10-26
> **[COLOR="Red"]sudo[/COLOR]** ndiswrapper -e dw200-0f4f
Forgot "sudo"...

---

### Post by wieman01 on 2006-10-26
If the removal of the driver does NOT work, then fire up Synaptic and right-click "ndiswrapper-utils" and choose: "Mark for Complete Removal".

That will remove the driver and ALL configuration files. Then reinstall the package & start from scratch.

---

### Post by kuberprok on 2006-10-26
Welll it worked, the driver is now inststalled, I restarted the pc
what next

---

### Post by wieman01 on 2006-10-26
Please show me this file:
> sudo gedit /etc/network/interfaces

---

### Post by kuberprok on 2006-10-26
albertus@presario700:~$ ndiswrapper -l
Installed ndis drivers:
dw200-0f4f              driver present
albertus@presario700:~$

---

### Post by kuberprok on 2006-10-26
> **wieman01 said:**
> Please show me this file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp
wireless-key 4FA7AE8D6F88AADF98EC5B0AC87

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by wieman01 on 2006-10-26
Then do a quick scan:
> iwlist scan
Post the results.

---

### Post by kuberprok on 2006-10-26
> **wieman01 said:**
> Then do a quick scan:

Post the results.

albertus@presario700:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      No scan results
sit0      Interface doesn't support scanning.

---

### Post by wieman01 on 2006-10-26
What happens if you update "interfaces" and restart the computer:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
Then scan:
> iwlist wlan0 scan
I have got the impression that the Linux driver for your card is somehow active & is interfering... Anyway, please restart & scan.

---

### Post by kuberprok on 2006-10-26
> **wieman01 said:**
> What happens if you update "interfaces" and restart the computer:

Then scan:

I have got the impression that the Linux driver for your card is somehow active & is interfering... Anyway, please restart & scan.

albertus@presario700:~$  auto lo
bash: auto: command not found
albertus@presario700:~$ iface lo inet loopback
bash: iface: command not found
albertus@presario700:~$
albertus@presario700:~$ #auto eth0
albertus@presario700:~$ #iface eth0 inet dhcp
albertus@presario700:~$
albertus@presario700:~$ auto wlan0
bash: auto: command not found
albertus@presario700:~$ iface wlan0 inet dhcp
bash: iface: command not found

---

### Post by wieman01 on 2006-10-26
You could also try to use Gnome's Networking Applet... Disable & enable the device "wlan0" and see if it starts working. Sometimes the devices are turned off by default.

Need to hop off line for today. It's late over here. Continue tomorrow.

---

### Post by kuberprok on 2006-10-26
I realy appreciate your time and help!!!!!

---

### Post by wieman01 on 2006-10-26
No problem. :-)

Please open this file:
> sudo gedit /etc/network/interfaces
This is the file that controls your network devices. Then copy & paste this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
When you have done that, save the file & _restart the computer_, then do another wireless scan to detect your network:
> iwlist wlan0 scan
What's the output?

---

### Post by wieman01 on 2006-10-26
BTW: You see I am using AIM. I'll be online tonight (Friday Hong Kong time) so perhaps we can get together by chat... Or tomorrow (Saturday) morning. Makes the whole affair a bit simpler.

---

### Post by kuberprok on 2006-10-27
> **wieman01 said:**
> BTW: You see I am using AIM. I'll be online tonight (Friday Hong Kong time) so perhaps we can get together by chat... Or tomorrow (Saturday) morning. Makes the whole affair a bit simpler.

I have been looking at this thread
[http://ubuntuforums.org/subscription.php?do=addsubscription&t=157180]("http://ubuntuforums.org/subscription.php?do=addsubscription&t=157180") can you maybe look at it?

Thanks again

---

### Post by wieman01 on 2006-10-27
Ok, but also follow my above suggestion. In addition to that, please do this:
> sudo gedit /etc/modprobe.d/blacklist
Then add this to the end of the file & save it:
> blacklist prism54
blacklist islsm
blacklist islsm_usb
blacklist islsm_device
Now restart the computer.

See you tonight. Please try those 2 things in the meantime (post #48 & this one).

---

### Post by kuberprok on 2006-10-27
I have tried that other thread, but this happens.

albertus@presario700:~$ sudo ndiswrapper -i ~/home/albertus/Driver1/driver/drive rs/prisma02.inf
Installing prisma02
couldn't copy /home/albertus/home/albertus/Driver1/driver/drivers/prisma02.inf a t /usr/sbin/ndiswrapper line 135.
albertus@presario700:~$

albertus@presario700:~$ ndiswrapper -l
Installed ndis drivers:
prisma02        invalid driver!
albertus@presario700:~$


albertus@presario700:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

albertus@presario700:~$

---

### Post by wieman01 on 2006-10-27
There is a problem with the path. Look at this:
> couldn't copy **[COLOR="Red"]/home/albertus/home/albertus[/COLOR]**/Driver1/driver/drivers/prisma02.inf a t /usr/sbin/ndiswrapper line 135.
The right command ought to be (no ~):
> sudo ndiswrapper -i **[COLOR="Red"]/home/albertus[/COLOR]**/Driver1/driver/drive rs/prisma02.inf
And please check that all other driver files next to *.INF such as *.SYS are in the same folder. Otherwise you'll receive an error message.

Then scan again.

---

### Post by kuberprok on 2006-10-28
The driver is now installed!!

But if I look in Network under System/applications there is no Wireless adp. There were one before.

The light on the device is also  dead.

Iwlist scan is still gives "interfaces doesn't support scanning.

---

### Post by wieman01 on 2006-10-28
Ok, can you go online? I have added to my Y! buddy list, perhaps we can chat & try to resolve the problem this way. You may have skipped a step or 2.

---

### Post by wieman01 on 2006-10-28
You have blacklisted the device, you also need to remove the old module:
> sudo rmmod prism54
Then restart the PC.

That done, what's the output of:
> ndiswrapper -l
_**EDIT:**_
And what output does this one yield:
> cat /etc/modprobe.d/ndiswrapper

---

### Post by kuberprok on 2006-10-28
albertus@presario700:~$ ndiswrapper -l
Installed ndis drivers:
prisma02                driver present
albertus@presario700:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
albertus@presario700:~$

---

### Post by kuberprok on 2006-10-28
$ sudo rmmod prism54
ERROR: Module prism54 does not exist in /proc/modules

---

### Post by wieman01 on 2006-10-28
What happens if you unplug & plug the device? Lights still off?

Is there a switch to turn it on by chance?

---

### Post by kuberprok on 2006-10-28
I did that but it is still dead. No switch.

Once the blacklist has been done then the device is dead, when I take the blacklist bit out it comes on.

What I konw think, is that this driver is also not the right one.

I am online with AIM now.

---

### Post by wieman01 on 2006-10-28
> **kuberprok said:**
> I did that but it is still dead. No switch.

Once the blacklist has been done then the device is dead, when I take the blacklist bit out it comes on.

What I konw think, is that this driver is also not the right one.

I am online with AIM now.
Yeah, I think we need to chat. Apparently the Windows driver does not do it's job, the Linux driver makes your device flash but the scanning fails. Let's chat & see what we can do about it.

---

### Post by kuberprok on 2006-10-29
Good news!

I got a new driver, 

Installed ndis drivers:
prisma02                driver present, hardware present
albertus@presario700:~$


wlan0     Scan completed :
          Cell 01 - Address: 00:16:CE:26:87:0E
                    ESSID:"WANADOO-3470"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-51 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=3
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

But, it's still not working!

The light on the device gets on and then shuts off. It flickers, but thats that.

Is there more I should do?

---

### Post by wieman01 on 2006-10-29
Great, man. You are almost there. So it was the driver after all. Can you tell me which one you have used?

Can you turn encryption off for a moment? Then scan shows that it's turned on & that may complicate this at this stage. Want to keep it simple in the first place.

[COLOR="Red"]I am assuming that you have DHCP enabled & encryption/authentication turned off.[/COLOR]

Please edit your interfaces file:
> sudo gedit /etc/network/interfaces
Then paste this:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]WANADOO-3470[/COLOR]
Then restart network:
> sudo /etc/init.d/networking restart

---

### Post by kuberprok on 2006-10-30
> **wieman01 said:**
> Great, man. You are almost there. So it was the driver after all. Can you tell me which one you have used?

Can you turn encryption off for a moment? Then scan shows that it's turned on & that may complicate this at this stage. Want to keep it simple in the first place.

[COLOR="Red"]I am assuming that you have DHCP enabled & encryption/authentication turned off.[/COLOR]

Please edit your interfaces file:

Then paste this:

Then restart network:


How do I turn the encryption off?

When I copy that bit in the device does not scan, again. When I take that bit out it scans again,

---

### Post by wieman01 on 2006-10-30
You need to configure the router. The router is set to WEP which is your encryption/authentication setting. 

Do you have access to the router? Do you see the WEP option somewhere? If yes, turn it off and choose "open" or "no encryption".

---

### Post by kuberprok on 2006-10-31
AT LAST!!!!!!

Its Working!!!!!!

There is someone out there!!

Thanks for all your help, this is a true example of the TRUE meaning of UBUNTU!



I found the driver from here
[http://www.unex.com.tw/web1/English/download/dl_search.asp#](http://www.unex.com.tw/web1/English/download/dl_search.asp#)
Without your help this would not have been possible at all!



Thanks again!

---

### Post by wieman01 on 2006-10-31
Wow, great. I am glad to hear it myself. :-) If you need help with WEP (encryption, authentication) drop me a line. Enjoy Ubuntu!

---

### Post by kuberprok on 2006-10-31
> **wieman01 said:**
> Wow, great. I am glad to hear it myself. :-) If you need help with WEP (encryption, authentication) drop me a line. Enjoy Ubuntu!


It is working with the WEP key, and thanks again for your offer!

---

### Post by wieman01 on 2006-10-31
> **kuberprok said:**
> It is working with the WEP key, and thanks again for your offer!
Even better. :-) Should you ever need WPA or WPA2 then feel free to let me know... Lol! 

Fun talking to you!

---

### Post by GoyoNeuff on 2006-11-30
Hi all !!!

I'm in the same situation: Trying to install ur054g(r01) v1.1 drive so this old wireless dongle works!!! That's until I get a 3COM XJACK Wireless Land PC Card, which I hope will be way to easier to install and get running!
I got Xubuntu installed into an IBM X24. I've tried to follow this thread to accomplish the wireless connection, but I'm very confused with all that have been written here.
Can any of you guys please make/write a summary of the steps to follow to accomplish such as noble task!:) 
Thanks a lot,
Camilo.

---

### Post by kuberprok on 2006-12-07
Hi

I only had to get the right driver, after that Ubuntu was picking it up and working eversince.

Refer to post 66 for the driver I used.

---

