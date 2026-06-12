---
title: "Cannot connect to home network"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by jstevens87 on 2006-10-29
Im using ubuntu 6.06 dapper drake, and can't seem to connect to my wireless network. If i go into system/administration/networking my wireless card shows so i don't think its a driver issue, though as i am new to linux im sure you know this better than me. My card is a realtek RTL8187. Im using DHCP not a static IP and have WEP encryption, any help you can give me would be much apriciated. Here is some info from the terminal:

john@john-desktop:~$ **ifconfig**
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28852 (28.1 KiB)  TX bytes:28852 (28.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:03:E8:AF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:12 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


john@john-desktop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"Test"
          Mode:Managed  Channel=13  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


john@john-desktop:~$ **iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results
sit0      Interface doesn't support scanning.

john@john-desktop:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


john@john-desktop:~$ **sudo gedit /ect/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eht1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Test
wireless-key 1234567890ABCDEF0987654321


john@john-desktop:~$ **sudo lspci**
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 277c (rev c0)
0000:00:01.0 PCI bridge: Intel Corporation: Unknown device 277d (rev c0)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:01:00.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
0000:01:00.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
0000:01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:00.0 IDE interface: Unknown device 197b:2363 (rev 02)
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 20)
0000:04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 20)
0000:06:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)


**sudo lshw**
          physical id: 5
             slot: L1-Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MB
             capacity: 4MB
             capabilities: pipeline-burst internal varies instruction
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 42
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: c0
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: c0
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@06:00.0
                version: a1
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:fd000000-fdffffff iomemory:d0000000-dfffffff  iomemory:fc000000-fcffffff ioport:cc00-cc7f irq:169
        *-multimedia
             description: Multimedia controller
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:febfc000-febfffff irq:177
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Ethernet interface
                product: 88E8053 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@04:00.0
                logical name: eth0
                version: 20
                serial: 00:17:31:f4:ee:54
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt -fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=sky2 driv erversion=1.4 firmware=N/A link=no multicast=yes port=twisted pair
                resources: iomemory:fa9fc000-fa9fffff ioport:b800-b8ff irq:90
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Ethernet interface
                product: 88E8053 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth1
                version: 20
                serial: 00:17:31:f4:f6:25
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt -fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=sky2 driv erversion=1.4 firmware=N/A link=no multicast=yes port=twisted pair
                resources: iomemory:fa8fc000-fa8fffff ioport:a800-a8ff irq:98
        *-pci:4
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-ide UNCLAIMED
                description: IDE interface
                physical id: 0
                bus info: pci@02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                resources: ioport:9c00-9c07 ioport:9880-9883 ioport:9800-9807 io port:9480-9483 ioport:9400-940f iomemory:fa7fe000-fa7fffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:e480-e49f irq:66
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
                   description: Mouse
                   product: USB Mouse
                   vendor: ARROW STRONG
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.10
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=40mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:e800-e81f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: ASUS DH Remote
                   vendor: T-wins
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:e880-e89f irq:74
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ec00-ec1f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:febfbc00-febfbfff irq:66
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 7
                   bus info: usb@5:7
                   version: 7.02
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0M B/s
                 [B]*-usb
                      description: Generic USB device
                      product: RTL8187_Wireless
                      vendor: Manufacturer_Realtek_RTL8187_
                      physical id: 3
                      bus info: usb@5:7.3
                      version: 1.00
                      serial: 0015AF03E8AF
                      capabilities: usb-2.00
                      configuration: driver=rtl8187 maxpower=500mA speed=480.0MB /s[/B]
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-multimedia:0
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant
                physical id: 0
                bus info: pci@01:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800
                resources: iomemory:f7000000-f7ffffff irq:82
           *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
                vendor: Conexant
                physical id: 0.1
                bus info: pci@01:00.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:f8000000-f8ffffff irq:11
           *-multimedia:2 UNCLAIMED
                description: Multimedia controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                vendor: Conexant
                physical id: 0.2
                bus info: pci@01:00.2
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:f9000000-f9ffffff irq:11
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@01:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:fa6ff800-fa6fffff iomemory:fa6f8000-fa6fbfff  irq:82
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:ffa0-ffaf irq:50
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: EEaKpEx MAPH 104
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 1WS2
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb a iordy audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers  cc=IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:e400-e407 ioport:e080-e083 ioport:e000-e007 iopor t:dc00-dc03 ioport:d880-d88f iomemory:febfb800-febfbbff irq:58
           *-disk
                description: SCSI Disk
                product: ST3320620AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5QF12F67
                size: 298GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 292GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 5938MB
                   capabilities: extended partitioned partitioned:extended
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:400-41f
  [B]*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:03:e8:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g[/B]


john@john-desktop:~$ **ping 192.168.0.1**
connect: Network is unreachable

---

### Post by trubblemaker on 2006-10-30
two things. first posting, wrap your out put in code tags the # sign in the gui for posting will show you what I mean, that makes you post alot easier to read, and hence you'll get alot more answers, faster

second, start with the network, unencrpyted and then move on to the next step.  Can you connect without wep?  that is always the way to start out, if you are unencrypted and you can see your network with ```
 iwlist scan
``` it's a configuration issue, if you still can't see anything then you probably need to search for a howto to setup your driver.  I see your using ndiswrapper, so this command might help give us some more data to work with
```
 ndiswrapper -l
dmesg | grep ndis

```

also I want to say thanks for your the output you did post, it makes it a lot easier to help when you post relevant info like you did.

---

### Post by punkybouy on 2006-10-30
Are you using DHCP to get an IP address from you home network?  I had problems with DHCP after the initial installation.  I just hard coded the IP and it has been running fine ever since.  Of course you will need DNS server entries to connect to the internet.  Those you can get from another machine that can connect to the internet.
Is there a light on the wireless card?  If not the driver might not be loading.

---

