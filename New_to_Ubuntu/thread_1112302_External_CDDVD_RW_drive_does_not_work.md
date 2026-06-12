---
title: "External CD/DVD RW drive does not work"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by h2o4444 on 2009-03-31
Hello, I recently purchased a Samsung SE-S084B portable CD/DVD-RW drive and I can't play DVDs or CDs. None of the preinstalled Ubuntu media players work. I installed VLC and it plays the CD as .wav files.

I like to rip the DVDs to mpg or avi format for safe keeping and rip my CDs to mp3, but right now nothing works.

What packages do I need to install?

---

### Post by logos34 on 2009-03-31
[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by h2o4444 on 2009-03-31
Thank you for the links! The first one is most helpful since it contains the second one. I'm ripping a CD right now to mp3 but the progress bar say it'll take me over 90 mins, at a speed of 0.5-0.6X.

Is there anything I can do to speed this up? I remember in Windows Media Player it only takes a few minutes to rip the CD to mp3 at 320 kbps. I did notice that the ripping is set to VBR but I still can't imagine it's this slow.

---

### Post by halitech on 2009-03-31
I'm going to take a guess that the unit is USB since you say it is portable. Is it USB 1.1 or 2.0 and is it plugged into a USB 2.0 port?

---

### Post by h2o4444 on 2009-03-31
My guess is USB 2.0 because it was first introduced in 2000, according to Wikipedia. And my computer is made in 2005 and the USB CD/DVD+RW drive is brand new.

Do you think there's a large time difference when converting a song to mp3 with VBR to converting a song to mp3 with CBR?

---

### Post by halitech on 2009-03-31
guessing is okay but not always accurate :) My system is from around 2004 and I only have usb1.1 ports. post the output of ```
lshw
``` and we can check from there.

---

### Post by h2o4444 on 2009-03-31
Here's the output code, it's quite long:

> description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MiB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 798MHz
          capacity: 798MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth0
                version: 11
                serial: 00:0f:b0:c4:1d:90
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751m-v3.40a latency=0 module=tg3 multicast=yes
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: 00:15:00:23:a1:0b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=206.159.124.30 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7 module=sdhci_pci
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
                vendor: Texas Instruments
                physical id: 6.5
                bus info: pci@0000:02:06.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:6c:c7:a5:07:30
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by halitech on 2009-03-31
I'm not toally sure but I have usbhosts listed in mine

```
*-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.26-1-486 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Comfort Optical Mouse 1000
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.21
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Printer
                   product: Samsung ML-2510 Series
                   vendor: Samsung
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.00
                   serial: 3V61BKCQ901383D.
                   capabilities: usb-1.10 bidirectional
                   configuration: driver=usblp speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.26-1-486 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: Mass Storage Device
                   vendor: Prolific Technology Inc.
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.00
                   serial: 00
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
```

I'm guessing but I think you have USB 1.1 ports based on the width and clock being the same as mine which I know are 1.1

---

### Post by h2o4444 on 2009-03-31
Yeah, probably USB 1. But still, it takes over an hour to rip one CD using Sound Juicer.

---

