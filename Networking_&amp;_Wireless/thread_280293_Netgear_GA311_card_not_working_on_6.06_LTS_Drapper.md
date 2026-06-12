---
title: "Netgear GA311 card not working on 6.06 LTS Drapper Drake"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by Biggle on 2006-10-19
I added the Netgear GA311 card to the above Ubuntu build along side an existing motherboard based NIC (intel I think). When I booted up and using System -> Administration -> Networking it showed 2 Ethernet cards (eth1 & eth2), but I cant get the Netgear card (eth2) to work whilst the original one works fine (eth1).

I have tried configuring it with DHCP and static IP addresses to no avial.  The same configuration on the original NIC works fine.  I'm not a Linux expert and I'm a bit stumped what to do next.  I have downloaded all the latest patches/fixes etc so the build is up to date software wise.  Internet searches show that it should be compatible out of the box.

Anyone got any ideas what I could do?

Thanks, Mark

---

### Post by Biggle on 2006-10-22
I have done some additional diagnostics - can anyone spot the problem:

Network interfaces file, the old Nic was on eth1 and the new Netgear nic on eth2:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#auto eth0

# The primary network interface
#iface eth0 inet dhcp

auto eth2

iface eth2 inet static
address 192.168.1.241
netmask 255.255.255.0
gateway 192.168.1.1

iface eth1 inet static
address 192.168.1.241
netmask 255.255.255.0
gateway 192.168.1.1

********************** ifconfig *****************

mrej@Server:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:14:6C:86:65:79
          inet addr:192.168.1.241  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1001024 (977.5 KiB)  TX bytes:1001024 (977.5 KiB)


*************************************************************
******************************* lspci ***********************

mrej@Server:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 01)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 01)
0000:02:04.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:02:04.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:02:04.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


**************************************************************
***************************** lshw ***************************
mrej@Server:~$ lshw
WARNING: you should run this program as super-user.
server
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.10
          size: 850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:44000000-47ffffff iomemory:40500000-4057ffff irq:5
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@02:04.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master cap_list
                configuration: driver=uhci_hcd
                resources: ioport:1440-145f irq:177
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 2.6.15-27-386 uhci_hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 4.1
                bus info: pci@02:04.1
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: uhci bus_master cap_list
                configuration: driver=uhci_hcd
                resources: ioport:1460-147f irq:185
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 2.6.15-27-386 uhci_hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: 4.2
                bus info: pci@02:04.2
                version: 63
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:40100000-401000ff irq:193
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.15-27-386 ehci_hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
           *-network:0 DISABLED
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth1
                version: 01
                serial: 00:02:a5:7e:0a:3b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 ip=192.168.1.241 multicast=yes
                resources: iomemory:40000000-40000fff ioport:1400-143f irq:201
           *-network:1
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@02:09.0
                logical name: eth2
                version: 10
                serial: 00:14:6c:86:65:79
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 ip=192.168.1.241 multicast=yes
                resources: ioport:1000-10ff iomemory:40200000-402000ff irq:185
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:2460-246f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: ST3500630A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 465GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: LTN485
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:2440-245f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:2000-20ff ioport:2400-243f irq:209

**********************************************************************************
*************************** route ************************************************

mrej@Server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth2

********************************************************************************
************************ ping **************************************************

mrej@Server:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.241 icmp_seq=2 Destination Host Unreachable
From 192.168.1.241 icmp_seq=3 Destination Host Unreachable
From 192.168.1.241 icmp_seq=4 Destination Host Unreachable
From 192.168.1.241 icmp_seq=6 Destination Host Unreachable
From 192.168.1.241 icmp_seq=7 Destination Host Unreachable
From 192.168.1.241 icmp_seq=8 Destination Host Unreachable
From 192.168.1.241 icmp_seq=10 Destination Host Unreachable
From 192.168.1.241 icmp_seq=11 Destination Host Unreachable
From 192.168.1.241 icmp_seq=12 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
13 packets transmitted, 0 received, +9 errors, 100% packet loss, time 12012ms
, pipe 3

Many thanks

---

### Post by silverado on 2007-01-21
I am trying to get my GA311 to work right now too.  It sort of works when it is direct connected to the router without being connected through my switch.  Are you trying to connect through an unmanaged switch?  

Try using this command:

# sudo ethtool eth0

It should tell you what speed the GA311 is at and if it is full or half duplex.  I think there might be a problem with the autonegotiation of the speed and it cannot connect.

---

