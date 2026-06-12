---
title: "Linksys Wireless USB Adapter"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by someotherguy582 on 2005-11-09
Hey everyone,

I've seen a lot of topics on getting wireless adapters to work, but most of them dont make sense to me or wont work.  I am asking for the **simplest** way to get my Linksys WUSB54Gv2 USB Adapter to work so I can access the internet using Ubuntu.

I currently have my HD partitioned with Windows XP Home installed to the first partition, and Ubuntu installed to the second.  (I recently just installed Ubuntu, after using XP for a long time).  Let me just say that Ubuntu is very nice and I'm sure I will learn to love it, but I cant live without internet. :P

Anyways, Ubuntu wont recognize my wireless adapter as a network device.  It IS listed in the Device Manager, but it has a bunch of "Unkown" statuses, etc.  So can anyone give me DETAILED instructions on the easiest way to get this to work?  I'm a huge noob to Lunix / Ubuntu, so be patient with me.

EDIT: Oh, and my wireless network is currently secured using WEP.

Thanks!  I look forward to your response. :)

---

### Post by Lambert on 2005-11-09
A couple questions first.

1. Do you have internet access with this box without this adapter(logged into ubuntu)? There are some packages we can download to make this easier.
2. Open a terminal and type this```
ndiswrapper -l
```
you will probably get a command not found  but I wanted to make sure. 
3. from the terminal type 
```
lshw -C network
```and```
lsusb
```and```
lspci
```
and post the out put here.

Quick search looked like most are using ndiswrapper to use this device. ndiswrapper is an application that makes the native windows drivers work in linux for the device.

You will need the cd with the windows drivers on it or go to linksys site to download them.

---

### Post by someotherguy582 on 2005-11-09
Here is the output :)

```
dj@djpc:~$ ndiswrapper -l
Installed ndis drivers:
wusb54gv2       driver present, hardware present
dj@djpc:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 13
       serial: 00:0e:a6:ba:6c:ac
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge ip=192.168.2.103 multicast=yes
       resources: iomemory:feafc000-feafffff ioport:d800-d8ff irq:22
dj@djpc:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 13b1:000a
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 03f0:6004 Hewlett-Packard DeskJet 5550
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
dj@djpc:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
0000:02:05.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
dj@djpc:~$

```

And yes, I have an internet connection right now, because I found a 25 foot ethernet cable and run the wire from my router, but I still need to get my wireless working.

Thanks!

---

### Post by Lambert on 2005-11-09
It looks like the device and driver is present to run the device. 

Have you gone into System>administration>Networking

You should see your device in the list. Highlight the device, click on properties, input your network settings.

Click ok then with the device highlighted click activate

You may want to deactivate the eth0 device first.

After that type the lshw -C network again you should see something like this.

description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: ath0
       version: 01
       serial: 00:11:95:50:be:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci [COLOR="Sienna"]ip=192.168.x.xxx[/COLOR] multicast=yes wire

 except vendor and other info will differ. This will tell you if you were assigned an ip address.

If it doesn't go back to the terminal and type 
```
lsmod
``` you should see ndiswrapper in the list
if not type ```
modprobe ndiswrapper
```

go back to sys>admin>network deactivate and reactivate

if it works  then to make sure it starts at boot go back to terminal and type ```
ndiswrapper -m
```

If you have errors or problems or clarification, come back and post

---

### Post by someotherguy582 on 2005-11-10
Thanks so much!!! It worked! :D  *At least for now* :P If any problems come up later on, I'll let your know.

---

### Post by jamesh on 2005-11-12
I have the same issue. And I typed the commands. The result is:

root@ubuntu:/# lshw -C network
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:04:5a:99:99:50
       size: 100MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=pegasus driverversion=v0.6.12 (2005/01/13) duplex=full ip=73.10.12.33 link=yes multicast=yes port=MII speed=100MB/s
root@ubuntu:/# lsusb
Bus 004 Device 002: ID 2001:3704 D-Link Corp. [hex]
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 066b:400b Linksys, Inc.
Bus 001 Device 002: ID 045e:0083 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
root@ubuntu:/# lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1420
0000:00:04.1 CardBus bridge: Texas Instruments PCI1420
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
0000:00:10.0 Communication controller: Lucent Microelectronics LT WinModem
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
0000:06:00.0 USB Controller: NEC Corporation USB (rev 43)
0000:06:00.1 USB Controller: NEC Corporation USB (rev 43)
0000:06:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
root@ubuntu:/#

In my system->Administration->networking, I can only find my first network adaptor as eth0, but I can't find my USB wireless adaptor.  But I can see the USB adaptor in my Device Manager. Can you tell me how to do the next step.

Thanks...

---

### Post by Lambert on 2005-11-13
What does ```
ndiswrapper -l
``` give you?

Have you tried to use ndiswrapper and install the drivers?

---

### Post by jamesh on 2005-11-13
I tried, but I got:

root@ubuntu:~# ndiswrapper -l
-su: ndiswrapper: command not found

How can I get the ndiswrapper command? 

Thank you...

---

### Post by Lambert on 2005-11-13
put your install disk back in your cdrom. Go to System>admin>synaptic

Click search and look for ndiswrapper (you may have to click reload first)

Click on the icon and choose mark for installation. Click apply in the toolbar. this will install the app ndiswraper.

Then you have to go through the steps to install ndiswrapper.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")



If you have internet access with the box while logged onto ubuntu, you can open synaptic, click reload, search for ndisgtk, install that, then click on system>admin>windows wireless drivers. If you can't find it then you'll have to make sure the correct repositories are set up.

Some help on installing and adding repositories
[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")
[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

ndisgtk is a graphical method to install the drivers where the link above uses the command line.

Another ndiswrapper link.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

Once you get the driver installed you should be able to open up networking, enter properties and activate.

---

### Post by jamesh on 2005-11-13
In the "Window Wireless Drivers", I installed the wireless adaptor driver by using my windows driver in the Manufacture CD. I could see the wireless adaptor in the networking window. I entered the ESSID and WEP key. Then I could ping the wireless adaptor itself  IP address, but when I tried to ping the Router IP address, I got the error:  Destination Host Unreachable.

What's the problem?

I typed iwconfig and got:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:32 dBm
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:187   Missed beacon:0

I'm using a laptop. And I installed a PCMCIA card to extend 4-port USB 2.0. The wireless adaptor supports USB 2.0, so it's pluged in  one of the USB2.0 port in PCMCIA card. I remember when I installed PCMCIA card in windows, it needed me to install a driver to support USB 2.0. Do I need to install the PCMCIA driver in ubuntu as well? And how to do this?

Can you give me the next instruction?

I really appreciate your help.

---

### Post by jamesh on 2005-11-14
I couldn't get answer for my above questions. So I tried to find a way to resolve it. I tried a lot of things, such as changing /etc/network/interfaces, runing ndsiwrapper -e, ndsiwrapper -i, removing and reinstalling the driver in Windows Wirless Driver window.
Finally, I can't see the wireless adaptor in my Networking window!!! I reboot the machine many times, but nothing worked. 

Can anybody give me an idea how to resolve the problem. Thank you...

---

### Post by Lambert on 2005-11-14
You had the device so it could be seen by the network manager but couldn't access the router so I don't believe there is a driver needed for the pcmcia device.

So let's go back to step one.

Post the out put of 

```
ndiswrapper -l 
and
sudo lshw
```

If you can find just the sections that look like the pcmcia card and the usb wireless adapter post those. If not just post the whole output here.

---

### Post by jamesh on 2005-11-14
[PHP]
root@ubuntu:~# ndiswrapper -l
Installed ndis drivers:
prisma02        driver present, hardware present
[/PHP]

I can find PCMCIA section, but cannot find wireless adaptor:
[PHP]
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:c000000-c000fff irq:10
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@00:04.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:c001000-c001fff irq:10
[/PHP]

---

### Post by jamesh on 2005-11-14
Here is my whole output:
```

root@ubuntu:~# lshw
ubuntu
    description: Notebook
    product: Satellite 1730/1750
    vendor: TOSHIBA
    version: PS170Q-0008R
    serial: 51039595
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook
  *-core
       description: Motherboard
       product: 888F2
       vendor: Null
       physical id: 0
       version: Null
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.20 (03/07/01)
          size: 81KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootsele ct int13floppytoshiba acpi usb agp ls120boot smartbattery
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: JP18/JP19
          size: 700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KB
             capacity: 512KB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 192MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: Internal
             size: 64MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: JDIM1
             size: 128MB
             width: 32 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: JDIM2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
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
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff ioport:2000-20ff iomemory: fc100000-fc100fff irq:10
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:c000000-c000fff irq:10
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@00:04.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:c001000-c001fff irq:10
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
             resources: ioport:1090-109f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHM2100AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 5823
                   serial: 01138908
                   size: 9590MB
                   capacity: 9590MB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma2 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: TOSHIBA CD-ROM XM-7002Bc
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1M10
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb a iordy audio
                   configuration: mode=udma2
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
             resources: ioport:1060-107f irq:10
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Basic Optical Mouse
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Generic USB device
                   product: LINKSYS USB Adapter
                   vendor: LINKSYS Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   serial: 999950
                   capabilities: usb-1.10
                   configuration: driver=pegasus maxpower=156mA speed=12.0MB/s
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: Crystal CS4281 PCI Audio
             vendor: Cirrus Logic
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CS4281
             resources: iomemory:fc010000-fc010fff iomemory:fc000000-fc00ffff ir q:5
        *-communication UNCLAIMED
             description: Communication controller
             product: LT WinModem
             vendor: Agere Systems (former Lucent Microelectronics)
             physical id: 10
             bus info: pci@00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:fc011000-fc0110ff irq:10
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 1
          bus info: pci@06:00.0
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:d000000-d000fff irq:10
        *-usbhost
             product: NEC Corporation USB
             vendor: Linux 2.6.12-9-386 ohci_hcd
             physical id: 1
             bus info: usb@3
             logical name: usb3
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@06:00.1
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:d001000-d001fff irq:10
        *-usbhost
             product: NEC Corporation USB (#2)
             vendor: Linux 2.6.12-9-386 ohci_hcd
             physical id: 1
             bus info: usb@4
             logical name: usb4
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@06:00.2
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:d002000-d0020ff irq:10
        *-usbhost
             product: NEC Corporation USB 2.0
             vendor: Linux 2.6.12-9-386 ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
           *-usb UNCLAIMED
                description: Generic USB device
                product: Cohiba 3887 rev0
                vendor: GlobespanVirata
                physical id: 3
                bus info: usb@2:3
                version: 10.50
                serial: 3887-0000
                capabilities: usb-2.00
                configuration: maxpower=500mA speed=480.0MB/s
  *-battery
       description: Nickel Metal Hydride Battery
       product: PXBAS008
       vendor: SANYO
       physical id: 1
       version: 08/28/2000
       serial: 3658Q
       slot: 1st Battery
       capacity: 4500mWh
       configuration: voltage=9.6V
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:04:5a:99:99:50
       size: 100MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autone gociation
       configuration: autonegociation=on broadcast=yes driver=pegasus driververs ion=v0.6.12 (2005/01/13) duplex=full ip=73.10.12.58 link=yes multicast=yes port= MII speed=100MB/s


```

---

### Post by Lambert on 2005-11-14
*-usb:1
                   description: Generic USB device
                   product: LINKSYS USB Adapter
                   vendor: LINKSYS Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   serial: 999950
                   capabilities: usb-1.10
                   configuration: driver=pegasus maxpower=156mA speed=12.0MB/s

I believe this is the section we need to look at. Notice the driver=pegasus

> driver for ADMtek based USB-Ethernet adapters

You don't have any other linksys device connected to your pc do you?

If not then there is a driver conflict. Try this.

```
sudo modprobe -r pegasus

then

sudo modprobe -r ndiswrapper

then

sudo modprobe ndiswrapper

then 

sudo lshw
```

Look for this device to see what drive it's using now. If it says ndiswrapper then go back to network manager to see if it's listed.

Try to connect, if not come back and post what happened up to this point.

---

### Post by jamesh on 2005-11-14
Sorry, I have to clarify that the LinkSys is my another wired USB adaptor and it's currently working well.  My USB wireless adaptor is D-Link DWL-G122, which is not presented in the list.

After I ran the commands, I got:
```

root@ubuntu:~# sudo modprobe -r pegasus
root@ubuntu:~# sudo modprobe -r ndiswrapper
root@ubuntu:~# sudo modprobe ndiswrapper
root@ubuntu:~# sudo lshw
ubuntu
    description: Notebook
    product: Satellite 1730/1750
    vendor: TOSHIBA
    version: PS170Q-0008R
    serial: 51039595
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=oem-specific chassis=notebook
  *-core
       description: Motherboard
       product: 888F2
       vendor: Null
       physical id: 0
       version: Null
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.20 (03/07/01)
          size: 81KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootsele ct int13floppytoshiba acpi usb agp ls120boot smartbattery
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: JP18/JP19
          size: 700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KB
             capacity: 512KB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 192MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: Internal
             size: 64MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: JDIM1
             size: 128MB
             width: 32 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: JDIM2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
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
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff ioport:2000-20ff iomemory: fc100000-fc100fff irq:10
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:c000000-c000fff irq:10
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@00:04.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:c001000-c001fff irq:10
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
             resources: ioport:1090-109f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHM2100AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 5823
                   serial: 01138908
                   size: 9590MB
                   capacity: 9590MB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma2 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: TOSHIBA CD-ROM XM-7002Bc
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1M10
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb a iordy audio
                   configuration: mode=udma2
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
             resources: ioport:1060-107f irq:10
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Basic Optical Mouse
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: LINKSYS USB Adapter
                   vendor: LINKSYS Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   serial: 999950
                   capabilities: usb-1.10
                   configuration: maxpower=156mA speed=12.0MB/s
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: Crystal CS4281 PCI Audio
             vendor: Cirrus Logic
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CS4281
             resources: iomemory:fc010000-fc010fff iomemory:fc000000-fc00ffff ir q:5
        *-communication UNCLAIMED
             description: Communication controller
             product: LT WinModem
             vendor: Agere Systems (former Lucent Microelectronics)
             physical id: 10
             bus info: pci@00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:fc011000-fc0110ff irq:10
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 1
          bus info: pci@06:00.0
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:d000000-d000fff irq:10
        *-usbhost
             product: NEC Corporation USB
             vendor: Linux 2.6.12-9-386 ohci_hcd
             physical id: 1
             bus info: usb@3
             logical name: usb3
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@06:00.1
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:d001000-d001fff irq:10
        *-usbhost
             product: NEC Corporation USB (#2)
             vendor: Linux 2.6.12-9-386 ohci_hcd
             physical id: 1
             bus info: usb@4
             logical name: usb4
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@06:00.2
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:d002000-d0020ff irq:10
        *-usbhost
             product: NEC Corporation USB 2.0
             vendor: Linux 2.6.12-9-386 ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
           *-usb
                description: Generic USB device
                product: Cohiba 3887 rev0
                vendor: GlobespanVirata
                physical id: 3
                bus info: usb@2:3
                version: 10.50
                serial: 3887-0000
                capabilities: usb-2.00
                configuration: driver=ndiswrapper maxpower=500mA speed=480.0MB/s
  *-battery
       description: Nickel Metal Hydride Battery
       product: PXBAS008
       vendor: SANYO
       physical id: 1
       version: 08/28/2000
       serial: 3658Q
       slot: 1st Battery
       capacity: 4500mWh
       configuration: voltage=9.6V
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:95:c3:6e:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes link=no multicast=yes wireless=IEEE 802.11g


```

From the network list, I could only see the wireless adaptor but lost my LinkSys USB ethernet adaptor.  When I tried to active the wireless adaptor, nothing worked. So I had to run modprobe -i pegasus to get my LinkSys connection back to connect to internet and post the message.

---

### Post by Lambert on 2005-11-14
(because of title of thread thought you had a linksys device and I wasn't clear about not removing the pegasus module if you did have another device, sorry for that)

So your wireless adapter is showing up again in network manager which is good.

a couple thoughts. First I see through a search there are different chipsets used. Because of the prisma02 it sounds like a prism chipset. Check lsmod to see if there is a prism module loaded. There may be a conflict

When you installed the drivers did you do it directly from the disk (include .sys and .dll files if present)? You may want to copy the entire folder to your drive and reinstall the drivers pointing to that folder.

Sudo modprobe -r ndiswrapper

sudo ndiswrapper -r prisma02

go through the steps again

Lastly search and verify the chipset for the version you have. There are also 28 other threads where a dwl-g122 is involved. Some have different chipsets but maybe you'll find something there.

---

### Post by emptymind on 2006-03-13
Hi

I am having trouble with getting my DWL G122 driver working. I have installed ndiswrapper as per in the instructions posted. 
However, when I do 
$ ndiswrapper -l
I get
Installed ndis drivers:
prisma02        driver present
I don't see a "hardware present". Do I have to compile a new kernel? (I use Kubuntu Breezy).

Under NetworkSettings, I only see eth0. There is no wlan0 device listed.

Thanks.

---

### Post by emptymind on 2006-03-15
[QUOTE=emptymind]Hi

I am having trouble with getting my DWL G122 driver working. I have installed ndiswrapper as per in the instructions posted. 
However, when I do 
$ ndiswrapper -l
I get
Installed ndis drivers:
prisma02        driver present
I don't see a "hardware present". Do I have to compile a new kernel? (I use Kubuntu Breezy).

Under NetworkSettings, I only see eth0. There is no wlan0 device listed.

Thanks.[/QUOTE]

UPDATE:
I have figured out this problem. Until now, I was using the drivers from Dlink's website. The procedure works after using the drivers supplied on the Dlink CD that comes with the hardware. I am wireless now (finally). Hope this helps someone.

---

### Post by gosia on 2006-04-15
Hi,

I've got problem with my Wireless USB Adapter.
I've tried to do what you said, but when I do 'sudo modprobe ndiswrapper' the program suspends. I don't know what to do.
Here is my output:
```
cara@ubuntu:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
wlanuzg driver present, hardware present

cara@ubuntu:~$ sudo lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 079b:004a Sagem
Bus 001 Device 001: ID 0000:0000

cara@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:05.0 Communication controller: Analog Devices SM56 PCI modem
0000:00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:14.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)

cara@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  0
nls_cp437               5888  0
vfat                   12288  0
fat                    46492  1 vfat
sd_mod                 17424  0
usb_storage            64704  0
scsi_mod              124872  2 sd_mod,usb_storage
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
i2c_viapro              7696  0
via686a                17816  0
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
pci_hotplug            24628  0
via_agp                 9472  1
agpgart                32328  1 via_agp
dm_mod                 50364  1
evdev                   9088  0
tsdev                   7616  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104316  3 usb_storage,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  789
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

cara@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 383MB
     *-cpu
          product: AMD Duron(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.3.1
          size: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 64KB
     *-pci:0
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: d8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d8000000-dbffffff
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
                product: NV11DDR [GeForce2 MX 100 DDR/200 DDR]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:dc000000-dcffffff iomemory:d0000000-d7ffffff irq:11
        *-communication UNCLAIMED
             description: Communication controller
             product: SM56 PCI modem
             vendor: Analog Devices
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:de000000-de0000ff irq:10
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@00:14.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@00:14.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:d000-d00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD800JB-00ETA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: LITE-ON DVDRW SOHW-1653S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-cdrom:1
                   product: E-IDE CD-ROM Max 50X
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@00:14.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:5
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: 802.11b/g USB WLAN
                   vendor: ZyDAS
                   physical id: 2
                   bus info: usb@1:2
                   version: 43.30
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@00:14.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:5
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.5
             bus info: pci@00:14.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:dc00-dcff ioport:e000-e003 ioport:e400-e403 irq:10
     *-pci:1
          description: Host bridge
          product: VT82C686 [Apollo Super ACPI]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:14.4
          version: 30
          width: 32 bits
          clock: 33MHz

cara@ubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.


cara@ubuntu:~$ sudo modprobe ndiswrapper


```

Thanks for any help

---

### Post by Tombo5150 on 2007-12-28
Ok. I'm trying to get my parents wireless to work. I couldn't find a driver that supports the card they have at the NDISwrapper list [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
I was following instructions from this page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and got hung up when I couldn't find drivers. 

```
user@-desktop:~$ lsusb
Bus 005 Device 005: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0781:8889 SanDisk Corp. SDDR-88 Imagemate 8-in-1 Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000 
```

Its pretty clear that the device is the Linksys WUSB11.

```
user@-desktop:~$ lshw
WARNING: you should run this program as super-user.
-desktop         
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 447MB
     *-cpu
          product: AMD Sempron(tm)   2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
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
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8378 [S3 UniChrome] Integrated Video
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=2
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE latency=32 module=via82cxxx
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   product: ST340014A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 37GB
              *-disk:1
                   product: WDC WD400BB-00DEA0
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 37GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: LITE-ON COMBO SOHC-5232K
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 656MB
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:11:09:cb:70:a7
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.102 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-scsi:0
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:0e:58:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.4-84 wireless=IEEE 802.11b

```

Help?

---

### Post by Lambert on 2007-12-29
tombo,

> 
*-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:0e:58:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=at76_usb driverversion=0.14beta1** firmware=1.101.4-84 wireless=IEEE 802.11b

this part shows the device is recognized and a driver loaded for the device so you shouldn't have to use ndiswrapper.

Now all you should have to do is configure a connection. If you're using ubuntu and not kubuntu or another version, there is a wireless icon on the top, you can click on that to bring up a menu for options.

There is also a good post around here from kevdog on connecting from the command line. Search his name in the networking section.

---

### Post by rustybronco on 2007-12-29
> **Lambert said:**
> tombo,
There is also a good post around here from kevdog on connecting from the command line. Search his name in the networking section.[http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

---

### Post by Tombo5150 on 2007-12-29
Hey thanks for the link and the help. I couldn't get it to work however, following kevdog's instruction. I understood what he wanted me to do, however I think it was something that was getting messed up with the wep encrypted key. I know that Ubuntu uses a 64 bit hex or whatever, but I think thats where I was getting tripped up. ..........any ideas?

---

### Post by Tombo5150 on 2007-12-29
Got it working! But I find that this is only a temporary fix. I need to find some way to make it permanent. My folks wouldn't understand all the commands and having to type it into terminal everytime they boot the computer-especially my mom. Any Ideas?

---

