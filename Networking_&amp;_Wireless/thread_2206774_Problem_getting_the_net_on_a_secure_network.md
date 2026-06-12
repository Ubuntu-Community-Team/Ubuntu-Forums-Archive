---
title: "Problem getting the net on a secure network"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by crua9 on 2014-02-20
Hello everyone. I'm using Ubuntu 13.10, and I'm running it on an HP Laptop. The following shows up after I put in
```
sudo lshw | less
```
 ```
description: Notebook
    product: HP G72 Notebook PC (XZ218UARABA)
    vendor: Hewlett-Packard
    version: 058C110002252710001620100
    serial: 5CS10146JQ
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=XZ218UARABA uuid=75FC1305-1DCF-7DFF-2352-1C4E7615E14E
  *-core
       description: Motherboard
       product: 1439
       vendor: Hewlett-Packard
       physical id: 0
       version: 60.4F
       serial: PBLVDC2FPZSAOH
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.46
          date: 11/15/2010
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: D106F7D4
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
 description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 1
             serial: D106F97D
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
          slot: CPU
          size: 1999MHz
          capacity: 2GHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid popcnt lahf_lm arat dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L3 cache
             physical id: 1c
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 1e
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 1f
             slot: L1 Cache
  capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 1d
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:3050(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:42 memory:b4404000-b440400f




 *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:b440a000-b440a3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:b4400000-b4403fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:b3400000-b43fffff ioport:b0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
 serial: 3c:4a:92:c9:03:82
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:41 ioport:2000(size=256) memory:b0410000-b0410fff memory:b0400000-b040ffff memory:b0420000-b043ffff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:1000(size=4096) memory:b2400000-b33fffff ioport:b1400000(size=16777216)
           *-network

                description: Wireless interface
                product: BCM4313 802.11bgn Wireless Network Adapter
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 88:9f:fa:78:3f:16
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:18 memory:b2400000-b2403fff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
: physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b4409000-b44093ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:3048(size=8) ioport:305c(size=4) ioport:3040(size=8) ioport:3058(size=4) ioport:3020(size=32) memory:b4408000-b44087ff
        *-serial UNCLAIMED
             description: SMBus


 product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b4406000-b44060ff ioport:3000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:7f:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:7f:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:7f:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:7f:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
*-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:7f:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:7f:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000BEVT-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 02.0
             serial: WD-WXU1EA0LSYR4
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0006faab
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f01275f3-b0ef-44c6-afaa-9fa9cc0d506f
                size: 461GiB
                capacity: 461GiB
 capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-02-01 12:24:37 filesystem=ext4 lastmountpoint=/ modified=2014-02-20 14:11:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-02-20 14:11:24 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3893MiB
                capacity: 3893MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3893MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633R
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 0200
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:1.5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
 size: 1886MiB (1977MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/craig/3538-6463
                version: FAT16
                serial: 3538-6463
                size: 1883MiB
                capacity: 1884MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-battery
       product: MU06047
       vendor: 13-42
       physical id: 1
       slot: In the back
       capacity: 47000mWh
       configuration: voltage=10.8V
(END)
```








So basically the wireless is
```
*-network
                description: Wireless interface
                product: BCM4313 802.11bgn Wireless Network Adapter
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 88:9f:fa:78:3f:16
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:18 memory:b2400000-b2403fff
```



Anyways, the problem I'm having is getting any internet on a secure network. I have no problem connecting and using a N router, but for some reason I can't get any internet from it when it's secure. However, my Windows computers don't have this problem.
I've tried all of these methods in the following link, and none of them worked.
[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

I've also tried the following method.
[http://askubuntu.com/questions/81156/wireless-with-wep-extremely-slow-on-an-acer-timeline-4810t-with-a-centrino-wirel](http://askubuntu.com/questions/81156/wireless-with-wep-extremely-slow-on-an-acer-timeline-4810t-with-a-centrino-wirel)


The 2 wireless routers I'm trying to hook into is a Amped Wireless [COLOR=#444444][FONT=arial]Extender and a [/FONT][/COLOR]Belkin wireless router.

Thanks

---

### Post by chili555 on 2014-02-20
There are two methods to get this device working; one is good and one is better. You have tried the driver *wl* and found it not so good. Let's try the other method. Please open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe brcmsmac
```Please post back and tell us if it is working as expected. 

The newer Broadcoms are a particular interest of mine; either they are going to work properly or I am going to give up Ubuntu altogether and buy a particle accelerator and work on an easier intellectual pursuit!

---

### Post by crua9 on 2014-02-20
That might have worked, but I just found out the router was out of date. 

I wish the good people at Ubuntu will fix their OS to run with no problem on a N router.

Anyways, thanks

---

### Post by chili555 on 2014-02-20
> **crua9 said:**
> I wish the good people at Ubuntu will fix their OS to run with no problem on a N router.

Mine runs perfectly well. I think the good people at Ubuntu wish that the hardware manufacturers like Intel, Linksys, Netgear, et al would agree upon and implement 802.11N correctly instead of finger pointing.

> wlan0     IEEE 802.11abgn  ESSID:"router"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: xx:D7:19:41:54:xx 
          Bit Rate=120 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm 

---

