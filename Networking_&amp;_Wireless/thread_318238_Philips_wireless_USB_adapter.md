---
title: "Philips wireless USB adapter"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by Ers on 2006-12-13
Hi all!

Okey, this is it. I have spent many nights searching info on this problem. I have tried so many ways to fix it. I just can´t ](*,) :( 

My OS is edgy eft and my wireless networking card is "Philips wireless USB adapter". The real need is help from the base since nothing so far has worked. But pleas, post anything that could possibly help me. I realy don´t want to waste my time on Windows anymore and I´m realy sad I can´t get the wireless internet conection going but I won´t give up and I can´t describe how happy I would be if someone could help me solve this problem :-| 

With tears in my eyes, pleas help me :neutral:

---

### Post by tturrisi on 2006-12-13
What model Phillips? (exact model & version)

---

### Post by Ers on 2006-12-14
Hi tturrisi! Thanks for helping :D

Here´s a link to my wireless card:

[http://www.consumer.philips.com/consumer/catalog/tree/PC_PRODUCTS_GR_GB_CONSUMER/PC_NETWORKING_CA_GB_CONSUMER/product/SNU6500_00_GB_CONSUMER/catalog.jsp?language=en&country=GB&catalogType=CONSUMER&proxybuster=TOFU2BUE1GB4LJ0RMRCSHP3HKFSESI5P](http://www.consumer.philips.com/consumer/catalog/tree/PC_PRODUCTS_GR_GB_CONSUMER/PC_NETWORKING_CA_GB_CONSUMER/product/SNU6500_00_GB_CONSUMER/catalog.jsp?language=en&country=GB&catalogType=CONSUMER&proxybuster=TOFU2BUE1GB4LJ0RMRCSHP3HKFSESI5P)

Thanks again!

---

### Post by Ers on 2006-12-14
Isn´t there anyone who can help me in any way? I have spent so much time trying to figure this out but it seems like I will need a pro on this one. Someone pleas help me :confused:

---

### Post by tturrisi on 2006-12-14
open a terminal, type:
lsusb
post results here.

---

### Post by tturrisi on 2006-12-14
After looking at the windows drivers for the card, it appears to be an Atheros chipset.  This is good!  Open Synaptic, enable the Universe & MultiUniverse repositories, install the Restricted modules for your kernel.  They contain the madwifi driver used for atheros chipsets.  Also, do post the results of lsusb.

---

### Post by FrodoB on 2006-12-14
If it is Atheros and USB then mAdWiFi will not work, you have to use ndiswrapper:

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

The device is not on the ndiswrapper compatibility list either, so you will just have to try the NDIS drivers that came on the CD with it or download a newer one from Philips if possible. You can also try drivers from other manufacturers Atheros USB devices on the list if necessary.

As was asked the output of lsusb could be very helpful.

---

### Post by tturrisi on 2006-12-15
> **FrodoB said:**
> If it is Atheros and USB then mAdWiFi will not work, you have to use ndiswrapper:

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

The device is not on the ndiswrapper compatibility list either, so you will just have to try the NDIS drivers that came on the CD with it or download a newer one from Philips if possible. You can also try drivers from other manufacturers Atheros USB devices on the list if necessary.

As was asked the output of lsusb could be very helpful.
That's not necessiarily true, madwifi does work with usb atheros devices.  It all depends upons what version and what atheros chipset.  There are several atheros chipsets, most work except one.  Just because the Phillips is not on the compatability list does not mean it is not compatable.  That list gets updated as users turn in reports.

---

### Post by Ers on 2006-12-16
Wow! Thank you very much for helping me, I realy appreciate it :D

Now... Here's the result of lsusb:

Bus 004 Device 002: ID 083a:5501 Accton Technology Corp.
Bus 004 Decive 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. Intelli Mouse Optical
Bus 002 Device 001: ID 0000:0000

I have also enabled the Universe and MultiUniverse repositories. But, and I´m sorry for that, I didn't know what you meant with "install the Restricted modules for your kernel" tturrisi?

Concerning Ndiswrapper I have already installed the drivers from the wireless card CD and they don´t have any newer on Philips home page. I haven´t tried installing "drivers from other manufacturers Atheros USB devices on the list". But if you think it´s worth a shot and there's a chace they will work with my usb card then I can try.

Yet again thanks for helping me :D

---

### Post by tturrisi on 2006-12-16
OK, not yet certain if it's an atheros chipset.  We need to identify the exact chipset of the card:
Here's some chipsets & relevant drivers:
[http://linux-wless.passys.nl/query_part.php?brandname=Accton](http://linux-wless.passys.nl/query_part.php?brandname=Accton)

post results of:
~# lshw

also see this:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Ers on 2006-12-17
Hi again :D

Here is the result of lshw:

ers                       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MB
     *-cpu
          product: AMD Athlon(tm) XP 2700+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
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
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: d0000000
          bus info: pci@00:00.0
          version: 80
          width: 32 bits
          clock: 66MHz
          resources: iomemory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e0000000-e0ffffff iomemory:d8000000-dfffffff irq:11
        *-firewire
             description: FireWire (IEEE 1394)
             product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
             vendor: NEC Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394
             resources: iomemory:e2003000-e2003fff irq:185
        *-communication
             description: Modem
             product: HSP56 MicroModem
             vendor: PCTel Inc
             physical id: a
             bus info: pci@00:0a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic bus_master cap_list
             configuration: driver=serial
             resources: iomemory:e2002000-e2002fff ioport:d000-d0ff irq:169
        *-network:0 DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: b
             bus info: pci@00:0b.0
             logical name: eth2
             version: 03
             serial: 00:11:50:35:93:cf
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:e2000000-e2001fff irq:201
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 5-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@2:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e2004000-e20040ff irq:193
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   vendor: Accton Technology Corp.
                   physical id: 1
                   bus info: usb@4:1
                   version: 2.02
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:e000-e00f irq:177
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   product: HL-DT-ST DVDRAM GSA-4082B
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 185MB
                   capabilities: packet
              *-disk
                   product: Maxtor 90320D2
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 3079MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk:0
                   product: Maxtor 6Y120L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 114GB
              *-disk:1
                   product: Maxtor 6B200P0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capacity: 189GB
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:e400-e4ff irq:217
        *-network:1 DISABLED
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:50:8d:51:50:3f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine multicast=yes
             resources: ioport:e800-e8ff iomemory:e2005000-e20050ff irq:209´

I hope this will help.

In the troubleshoting guide it sais that if you don't get an output when comanding "sudo pccardctl ident" then "the memory on the card can not be read which could be the problem". I don't get an output. Maybe this doesn't have anything to do with my problem but I tought that it can't hurt to let you know this.

Many thanks / Ers

---

### Post by tturrisi on 2006-12-17
This is the wireless device:

description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: b
bus info: pci@00:0b.0
logical name: eth2
version: 03
serial: 00:11:50:35:93:cf
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:e2000000-e2001fff irq:201

As well as:
*-usb UNCLAIMED
description: Generic USB device
vendor: Accton Technology Corp.
physical id: 1
bus info: usb@4:1
version: 2.02
capabilities: usb-2.00
configuration: maxpower=500mA speed=480.0MB/s

I would suggest getting a new wifi pcmcia card that is known to work.  Broadcom wifi devices are crappy on linux because there is no opensource driver for broadcom that is (1)stable, (2)works w/ enough different devices & (3)is dependable.  Broadcom devices can be made to work on linux using the windows driver and ndiswrapper (sometimes).

If the Philips wireless USB adapter is a separate plugged in usb device, then unplug it & do lshw again but this time w/out the usb device connected.  It the Phillips is built into the comp then you will be SOL until linux can recognize and supply firmware for the Accton device and ndiswrapper won't work either.

I have a similar situation, my laptop has an onboard usb wifi device, the usb is Airvast and the wifi has a prism chipset.  Prism chipsets are well supported by linux but the Airvast usb is not. :-(  Thus I have sevaral pcmcia wifi cards that I use.

There are lots of guides here re ndiswrappper & broadcom, you have nothing to lose by trying them to see if it can be made to work.  Search the forums for:
broadcom ndiswrapper howto.

---

### Post by Ers on 2006-12-17
Okej. Yea... I thought I had to buy a new card :( But for Ubuntu it's worth it :D

I have tried, I think, all guides similar to my cards and nothing has worked so this seems like the only solution left.

What did you mean by "built into the comp then you will be SOL"?

Just to avoid this problem next time, do you have any tips on good, cheap cards that will work with Ubuntu as soon as I pop them in to my computer? The computer is about 2 years old.

And not to forget. Thank you realy realy much for all the help and support I've got from you tturrisi. I doubt it, but if you ever have a problem I can help you with I will be realy glad to help you. Thanks again.

---

### Post by tturrisi on 2006-12-17
By "built into the comp" I meant onboard wifi, integrated into the motherboard as opposed to a separate plugin device.  If yours is a separate plugin device (pcmcia card or usb) then it is possible to get working using windows drivers & ndiswrapper, but it's not a sure thing for broadcom chipset devices.  I suggest getting an atheros chipset card such as the recent D-Link DWL-630G or 650G pcmcia cards.  Here's a site that sells many cards known to work w/ linux, I bought my New Orinoco Gold card from them & shipping was quick & the guy even responded to my emails.  The product descriptions inform whether or not works w/ linux.
[http://www.data-alliance.net/servlet/StoreFront](http://www.data-alliance.net/servlet/StoreFront)

---

