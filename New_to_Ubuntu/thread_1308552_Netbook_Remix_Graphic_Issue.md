---
title: "Netbook Remix Graphic Issue"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Jepic Phail on 2009-10-31
Hello,

I am having a strange graphical issue with Ubuntu Netbook Remix on my ThinkPad X31. I tried updating and checking for hardware drivers, but it did not resolve the issue. I also tried disabling visual effects and tried installing compiz config manager. None of them worked.

Please help!

---

### Post by Jepic Phail on 2009-11-01
Shameless bump! 

Well, I might as well install xubuntu... :o

---

### Post by davidryderuk on 2009-11-01
Hi,
There are some settings for xorg.conf recommended on the thinkwiki.org page. I don't have your laptop, but it's probably worth a try.

This is the page describing your laptop.

[http://www.thinkwiki.org/wiki/Category:X31](http://www.thinkwiki.org/wiki/Category:X31)

This is the page that suggests some optimum xorg.conf settings.

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000)

If you want to try the settings out then you can do the following.

1. Create the xorg.conf file and open it in gedit by entering the following in terminal.

```
gksudo gedit /etc/X11/xorg.conf
```

2. Add the following text to the file.

```
Section "Device"
       Identifier      "ATI"
       Driver          "radeon"
       Option          "AccelMethod" "XAA"
       Option          "AGPMode" "4"
       Option          "AGPFastWrite" "yes"
       Option          "EnablePageFlip" "on"
       Option          "RenderAccel" "on"
       Option          "DynamicClocks" "on"
       Option          "BIOSHotkeys" "on"
EndSection
```

3. Save the file and reboot.

---

### Post by Jepic Phail on 2009-11-01
David,

Thanks for you suggestion. Unfortunately, it did not work.

Oh, here is the output of lshw just for fun:
```
zombie-laptop
    description: Notebook
    product: 2672NEK
    vendor: IBM
    version: ThinkPad X31
    serial: 99MGACW
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=325A0401-4710-11CB-9D52-A22D83BF32DA
  *-core
       description: Motherboard
       product: 2672NEK
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1T8041Y127
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1QET72WW (2.10a) (12/24/2003)
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1600MHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.9.5
          slot: None
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: DIMM 2
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:c0100000-c01fffff memory:e0000000-e7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:e0000000-e7ffffff(prefetchable) ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:c0000000-c00003ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:4000(size=20480) memory:c0200000-cfffffff memory:e8000000-efffffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:02:00.0
                version: aa
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603020-b0060301f irq:11 memory:b0000000-b0000fff ioport:4000(size=256) ioport:4400(size=256) memory:e8000000-ebffffff(prefetchable) memory:c4000000-c7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: aa
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00707020-b0070701f irq:11 memory:b1000000-b1000fff ioport:4800(size=256) ioport:4c00(size=256) memory:ec000000-efffffff(prefetchable) memory:c8000000-cbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:11 memory:c0202000-c02027ff
           *-network:0
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1
                version: 04
                serial: 00:0c:f1:1c:fc:63
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
                resources: irq:11 memory:c0200000-c0200fff
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 81
                serial: 00:0d:60:77:a2:2e
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.3 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:11 memory:c0201000-c0201fff ioport:8000(size=64)
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1860(size=16) memory:50000000-500003ff
           *-disk
                description: ATA Disk
                product: ST9100822A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.00
                serial: 3LG01TQQ
                size: 93GiB (100GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1b5c1b5b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 066ff251-6339-4938-8fd2-da48e480ce7e
                   size: 89GiB
                   capacity: 89GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-29 21:56:20 filesystem=ext4 lastmountpoint=/>ï¿œMï¿œï¿œï¿œï¿œ0ï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œiWï¿œï¿œï¿œï¿œïï¿œï¿œï¿œï¿œï¿œïï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œï¿œYï¿œï¿œï¿œï¿œï¿œï¿œ%ï¿œï¿œ modified=2009-10-29 22:05:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-01 11:37:57 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3671MiB
                   capacity: 3671MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3671MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:18c0(size=64) memory:c0000c00-c0000dff memory:c0000800-c00008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
```

---

### Post by sparko on 2009-11-03
I have same problem ... :/ there are a lot of manuals but noone works.

---

### Post by sdpiowa on 2009-11-03
If you run the Live CD, does it still have the problems?  If not, the problem is due to your configuration on your computer.

---

### Post by sparko on 2009-11-03
yes from live its same. i want try 9.04 but i cant get it on usb ... :/

---

### Post by sparko on 2009-11-03
with 'vesa' driver its ok but slow, with 'ati' or 'radeon' its fast but ugly and 'fglrx' ist working at all :( its my situation

---

### Post by sparko on 2009-11-03
ok i have a solution. I use 'vesa' driver which is slow in netbook mode but in gnome its ok so I uninstall netbook stuff and go on classic gnome and its ok.

---

### Post by Jepic Phail on 2009-11-03
> **sdpiowa said:**
> If you run the Live CD, does it still have the problems?  If not, the problem is due to your configuration on your computer.

I know my logic here is flimsy, but since I was "downgrading" from Ubuntu 9.04 to NBR 9.10 I did not test the hardware with the Live CD. I know, I know, what a ultra-noob-ish mistake. Well, I guess I am paying the price with interest...

> **sparko said:**
> ok i have a solution. I use 'vesa' driver which is slow in netbook mode but in gnome its ok so I uninstall netbook stuff and go on classic gnome and its ok.

xubuntu here I come (and vive la gnome)! ;)

---

### Post by sparko on 2009-11-04
'ati' driver is ok too. its faster than 'alsa' (ati 1000frames/5s; alsa 400frames/5s). only notify messages are bad ... so i uninstalled them and all is ok :)

---

