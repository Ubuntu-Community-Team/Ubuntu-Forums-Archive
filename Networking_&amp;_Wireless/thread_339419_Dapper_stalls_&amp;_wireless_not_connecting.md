---
title: "Dapper stalls &amp; wireless not connecting"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by Sierra_Dave on 2007-01-15
Hi,

I have installed ndiswrapper and my ehome driver, but when Ubuntu loads [dapper], it stalls on network, but finally loads fully "ok".  The card lights up both power on and signal indicator go solid...then the wireless card signal goes off and w/c power light flashs.

I find the car installed on system manager and the box on left screen title bar show wlan0 but no signal strength.

When I configure it, it all goes in fine, but it does not retain wlan0 as default gateway, despite setting it so.

Any help would be appreciated! 

Thanks,
Dave](*,)

---

### Post by Metaljaz on 2007-01-15
try running from a terminal window the following commands to make sure you have
the right driver installed. You are checking for the chipset of the card you are using.
lshw
Your results should look something like this. The product should be your nic card
and the vendor will be your chipset.

 *-network
          description: Wireless interface
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.

lspci
Your results again will look something like this.

0000:07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by Sierra_Dave on 2007-01-15
This is the info I got:

carol@carol-laptop:~$ *-network
bash: *-network: command not found
carol@carol-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:0e.0 USB Controller: NEC Corporation USB (rev 41)
0000:02:0e.1 USB Controller: NEC Corporation USB (rev 41)
0000:02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
carol@carol-laptop:~$ *-network
bash: *-network: command not found
carol@carol-laptop:~$ lshw
WARNING: you should run this program as super-user.
carol-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 255MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.4
          size: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82845 845 (Brookdale) Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 60000000
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          resources: iomemory:60000000-6fffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 (Brookdale) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:48000000-4fffffff ioport:3000-30ff iomemory:40400000-4040ffff irq:11
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant
                physical id: 4
                bus info: pci@02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:40000000-4000ffff ioport:2040-2047 irq:5
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@02:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:40300000-403007ff iomemory:40080000-40083fff irq:11
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@02:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:40100000-40100fff irq:11
           *-network DISABLED
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 42
                serial: 00:08:02:b9:aa:36
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 multicast=yes
                resources: iomemory:40180000-40180fff ioport:2000-203f irq:10
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: e
                bus info: pci@02:0e.0
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:40200000-40200fff irq:10
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-26-386 ohci_hcd
                   physical id: 1
                   bus info: usb@1
                   logical name: usb1
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: e.1
                bus info: pci@02:0e.1
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:40280000-40280fff irq:10
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-26-386 ohci_hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: e.2
                bus info: pci@02:0e.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:40380000-403800ff irq:10
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.15-26-386 ehci_hcd
                   physical id: 1
                   bus info: usb@3
                   logical name: usb3
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:4440-444f iomemory:22000000-220003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: FUJITSU MHR2030AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 27GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SD-R2102
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:4000-40ff ioport:4400-443f irq:5
     *-network
          description: Wireless interface
          product: 88w8335 [Libertas] 802.11b/g Wireless
          vendor: Marvell Technology Group Ltd.
          physical id: 0
          bus info: pci@03:00.0
          logical name: wlan0
          version: 03
          serial: 00:19:5b:03:fe:40
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper multicast=yes wireless=IEEE 802.11FH
          resources: iomemory:24000000-2400ffff iomemory:24010000-2401ffff irq:11
carol@carol-laptop:~$

It looks like everything is installed.  Some setting though is not right with the world!  Any ideas?
Thanks,
Dave

---

### Post by Metaljaz on 2007-01-15
Ok. based on the output looks like you have a marvell technology chipset. You need a 
driver that matches the chipset.

0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

description: Wireless interface
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.

sounds like you will need to use ndiswrapper and the winxp drivers for Marvel Technology Group Ltd.

---

### Post by Metaljaz on 2007-01-15
read thru this thread. there is a walkthrough that maybe helpful to you.
take your time, ask questions and be patient.You will learn a lot. Don't
give up.
Good Luck

[http://www.ubuntuforums.org/showthread.php?p=1806138](http://www.ubuntuforums.org/showthread.php?p=1806138)

---

### Post by Sierra_Dave on 2007-01-15
This is where I have my problem:

*-network
description: Wireless interface
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@03:00.0
logical name: wlan0
version: 03
serial: 00:19:5b:03:fe:40
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper multicast=yes wireless=IEEE 802.11FH
resources: iomemory:24000000-2400ffff iomemory:24010000-2401ffff irq:11

I went through that post but each time I do iwconfig, the values :

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Frequency: GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
         ...

I checked etc/ndiswrapper and the driver is present.  It is mrv8335.inf .  
If ndiswrapper is loading only this driver, it should be ok.  However, I cant get the driver up with the qouted post.  Any ideas?

Thanks,
Dave

---

### Post by Metaljaz on 2007-01-16
scan for networks:
# iwlist wlan0 scan 

If your network is not found then set ssid first, and then scan again:
# iwconfig wlan0 essid <ssid>
# iwlist wlan0 scan 

configure and activate the wlan0 interface in the network settings, using the dialog reached from the Ubuntu System menu:
select the Ubuntu menu: System-Administration-Networking

select the Connections tab

select Properties for the Wireless Connection
in the “Interface Properties” dialog that appears
check the box “This device is configured”
in the field “Network Name (ESSID)” enter your SSID, the network name as configured in your wireless router (ex: homenet)
in the “Configuration” field select Static IP address or DHCP.
if you selected DHCP leave the rest of the fields empty and press “OK”.
if you selected Static IP address:
enter your IP address in the “IP address” field (ex: 10.0.0.200), make sure that your IP address does not overlap with the range of IP addresses that can be assigned by DHCP by our router, and that no other host on your network has got the same IP address
enter your subnet mask in the “Subnet mask” field (ex: 255.0.0.0)
enter your gateway address in the “Gateway address” field (ex: 10.0.0.138)
press the “OK” button 

wlan0 may have to be replaced for whatever network connection name you should have. Mine is ath0. Others use eth1.

post back

---

