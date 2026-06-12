---
title: "Enabling Netgear WG111T for usage"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by L2wis on 2006-11-06
Hey all, My laptop (Thinkpad T21) works great when plugged into my ethernet adapter but i want it to use my wireless side of the router. My USB device is called WG111T, it came with my router and worked well when i used to use windows. So far I've:

[LIST]
[*]Installed ndiswrapper thingy
[*]Transfered across the driver folder from the windows wg111t installation disc
[*]Tried (I think?) to install the .inf file in ndiswrapper
[/LIST]
conclusion of what i've done so far is:
[LIST]
[*]No wireless adapter has appeared in network manager?!
[*]In ndiswrapper it says hardware isn't present?!
[/LIST]

It's one of the last things i'd like to get functioning on my laptop. All contributions are more than welcome!

Regards

Edit*: I missed off some other things that maybe can help some1 help me:
[LIST]
[*]output from iwconfig is: 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[*]output from iwlist scan is:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
[/LIST]

---

### Post by wieman01 on 2006-11-07
Have you followed this guide?

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111")

---

### Post by L2wis on 2006-11-07
Hi yeh, i've gone through the guide too. Humm its an odd one tbh. ndiswrapper seems to install the drivers fine but when i ifup the device i get nothing but errors 

'wlan0: ERROR while getting interface flags: No such device'.

I have heard that it's nessecary to install the latest ndiswrapper drivers. I downloaded them but after tar'in it i couldn't 'make install' it I kept getting errors along the lines of 'unknown command make'? However i have tried 

'sudo apt-get install ndiswrapper' and it says it's up2 date?!

nagging me now. Thanks for the responce.

Edit*: The make install problem is solved now and im gonna try with a more up to date ndiswrapper.

Edit**: The new version of ndiswrapper has made no difference. It's still reporting:

sudo ndiswrapper -l
installed drivers:
netwg11t                driver installed

---

### Post by wieman01 on 2006-11-08
> sudo ndiswrapper -l
installed drivers:
netwg11t driver installed
That's good news. Please post this file:
> sudo gedit /etc/network/interfaces
And this one:
> sudo gedit /etc/modprobe.d/ndiswrapper
Then we'll see.

What does this command do:
> iwlist scan

---

### Post by L2wis on 2006-11-08
> **wieman01 said:**
> That's good news. Please post this file:

And this one:

Then we'll see.

What does this command do:

Quote:
sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        hostname MyNetwork
        wireless_mode managed
        wireless-essid MyNetwork

Quote:
sudo gedit /etc/modprobe.d/ndiswrapper

alias wlan0 ndiswrapper

Quote:
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

Thanks!

---

### Post by wieman01 on 2006-11-08
Which version of Ubuntu are you using?

Please update "/etc/network/interfaces" according to this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
Then scan again & post the output:
> iwlist scan
And what do "lshw" or "lsusb" say?
> lshw
> lsusb

---

### Post by L2wis on 2006-11-08
> **wieman01 said:**
> Which version of Ubuntu are you using?

Please update "/etc/network/interfaces" according to this:

Then scan again & post the output:

And what do "lshw" or "lsusb" say?

I'm running dapper drake, after i changed the file to what you posted i recieved the same message from 'iwlist scan':

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

lshw =

 sudo lshw
l2wis-laptop
    description: Notebook
    product: 2647CCG
    vendor: IBM
    version: Not Available
    serial: 550P4H6
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=995D9A01-4511-11CB-90FB-8BC5F7A08057
  *-core
       description: Motherboard
       product: 2647CCG
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1GGK155AMR
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: KZET22WW (1.04a) (01/19/2001)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.8.6
          slot: None
          size: 650MHz
          capacity: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 128MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 11
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f0000000-f7ffffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1450
             vendor: Texas Instruments
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:50000000-50000fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1450
             vendor: Texas Instruments
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:50100000-50100fff irq:11
        *-network
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             logical name: eth0
             version: 09
             serial: 00:10:a4:8f:9a:fd
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.0.10 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:e8120000-e8120fff ioport:1800-183f iomemory:e8100000-e811ffff irq:11
        *-communication
             description: Serial controller
             product: Mini-PCI V.90 56k Modem
             vendor: Xircom
             physical id: 3.1
             bus info: pci@00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: 16550 cap_list
             configuration: driver=serial
             resources: ioport:1840-1847 iomemory:e8121000-e8121fff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]             vendor: Cirrus Logic
             physical id: 5
             bus info: pci@00:05.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Sound Fusion CS46xx
             resources: iomemory:e8122000-e8122fff iomemory:e8000000-e80fffff irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1850-185f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HITACHI_DK23BA-20B
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 00E0A0B4
                   serial: 114XPX
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
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
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: HITACHI DVD-ROM GD-S200
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 0034
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: WG111T
                   vendor: Atheros Communications Inc
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=12.0MB/s
        *-bridge:1 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             resources: irq:9

and 'sudo lsusb' =
Bus 001 Device 002: ID 1385:4251
Bus 001 Device 001: ID 0000:0000

---

### Post by wieman01 on 2006-11-08
Ahem... Pull the Ethernet cable please & retry:
> *-usb UNCLAIMED
description: Generic USB device
product: WG111T
vendor: Atheros Communications Inc
This indicates that your ethernet connection is active. That's a problem, you cannot have both at the same time.

Or have you turned off your wireless adapter?

---

### Post by L2wis on 2006-11-08
> **wieman01 said:**
> Ahem... Pull the Ethernet cable please & retry:

This indicates that your ethernet connection is active. That's a problem, you cannot have both at the same time.

Or have you turned off your wireless adapter?

ah right okay, i didn't realise i cud get this sorted whilst connected via lan. When i unplugged mind... nothing came up as wireless in admin>networkin and i was disconnected?

---

### Post by wieman01 on 2006-11-08
Can you do another scan?
> iwlist scan
Second, have you blacklisted the Linux driver for "WG111T"? Isn't it "prism54" or something?

---

### Post by L2wis on 2006-11-09
> **wieman01 said:**
> Can you do another scan?

Second, have you blacklisted the Linux driver for "WG111T"? Isn't it "prism54" or something?

I've unplugged my cable and put in the usb adapter and tried iwlist scan but it just says the same as before. Do i need to disable my lan connection in admin>networking?

I think i've blacklisted the linux driver from following a different guide.

Regards!

---

### Post by wieman01 on 2006-11-09
Can you tell me which driver you have blacklisted?

Also... It looks to me as if you may have used the wrong Windows driver. Some people say that they had to use the most recent one to get their card working. Perhaps this helps.

---

### Post by L2wis on 2006-11-09
I don't remember how i goto the blacklist?

I've installed netgears latest 1.2 drivers (couldn't get 1.3) and the latest ndiswrapper.

---

### Post by wieman01 on 2006-11-09
The blacklist is here:
> gedit /etc/modprobe.d/blacklist
_**EDIT:**_
These are the drivers you'll have to blacklist:
> blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb

---

### Post by L2wis on 2006-11-10
okay, those were on the list already :S Any other ideas?

---

### Post by wieman01 on 2006-11-10
I am afraid I don't have any other smart idea. The lines in "lshw" suggest that some hardware component have not installed or are disabled. Does removing the card from the computer & plugging it back in help?

---

