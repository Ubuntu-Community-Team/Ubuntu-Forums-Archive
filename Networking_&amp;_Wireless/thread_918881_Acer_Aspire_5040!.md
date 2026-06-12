---
title: "Acer Aspire 5040!"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by darkchron on 2008-09-13
Hello ubuntu people of this universe.

I have now installed the latest version of ubuntu on my acer aspire 5040 laptop. The installation went smooth but the wireless network does not work. I think this issue has to do with the on and off network button that acer has on this laptop. I remember having the same problem on a fresh XP installation, then i had to find drivers for the "On/Off" network button.

How can i fix this please?

:popcorn:

---

### Post by darkchron on 2008-09-13
It appears that i don't have any wireless connection, so i don't think ubuntu has even found the card. In network configuration i only have wired connection.:confused: The card is using AR5005G drivers.

Any help would be appreciated.:KS

---

### Post by darkchron on 2008-09-13
```
skyggen@skyggen-laptop:~$ sudo lshw
skyggen-laptop            
    description: Notebook
    product: Aspire 5040
    vendor: Acer
    version: -1
    serial: LXADX052186350CD9E2000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=ECD4EAC0-3C65-11DB-85E5-F2DCDEB27A66
  *-core
       description: Motherboard
       product: Aspire 5040
       vendor: Acer
       physical id: 0
       version: Rev.A
       serial: LXADX052186350CD9E2000
       slot: &#65533;
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: V1.05 (04/21/2006)
          size: 98KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-37
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.2
          slot: Socket 754
          size: 2GHz
          capacity: 2500MHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: S2
             size: 512MiB
             width: 32 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS485 [Radeon Xpress 1100 IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: ST9120822A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.ALC
                   serial: 5LZ0LRZE
                   size: 111GiB (120GB)
                   capacity: 111GiB (120GB)
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 signature=34fe34fd smart=on
                 *-volume:0
                      description: Windows FAT volume
                      vendor: MSWIN4.1
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      version: FAT32
                      serial: 0e4e-05ce
                      size: 4000MiB
                      capacity: 4000MiB
                      capabilities: primary boot fat initialized
                      configuration: FATs=2 filesystem=fat
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 53GiB
                      capacity: 53GiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: HPFS/NTFS partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 26GiB
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/hda6
                         logical name: /
                         logical name: /dev/.static/dev
                         capacity: 25GiB
                         configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                    *-logicalvolume:2
                         description: Linux swap / Solaris partition
                         physical id: 7
                         logical name: /dev/hda7
                         capacity: 1176MiB
                         capabilities: nofs
                 *-volume:2
                      description: Windows FAT volume
                      vendor: MSWIN4.1
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      version: FAT32
                      serial: 9612-ae03
                      size: 54GiB
                      capacity: 54GiB
                      capabilities: primary bootable fat initialized
                      configuration: FATs=2 filesystem=fat
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: Slimtype DVDRW SSW-8015S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: HRS2
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 5
                bus info: pci@0000:06:05.0
                logical name: wlan0
                version: 01
                serial: 00:16:cf:50:99:82
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,01/10/2004,4.0.0.14001 latency=128 link=no maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 6
                bus info: pci@0000:06:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:1
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:16:d3:45:3b:79
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.103 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
```

skyggen@skyggen-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Operation not supported

if it helps......

---

### Post by Crafty Kisses on 2008-09-13
First, let's see if you get an output when you do this in Terminal:
```
lspci | grep Atheros
```
You should get something similar to this:
```
06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```
You may also need to install this package:
```
sudo apt-get install linux-restricted-modules madwifi-tools 
```

---

### Post by darkchron on 2008-09-13
**skyggen@skyggen-laptop:~$ lspci | grep Atheros**
```
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```
**skyggen@skyggen-laptop:~$ sudo apt-get install linux-restricted-modules madwifi-tools**
```
[sudo] password for skyggen: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following NEW packages will be installed:
  linux-restricted-modules madwifi-tools
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.0kB of archives.
After this operation, 262kB of additional disk space will be used.
Get:1 http://no.archive.ubuntu.com hardy-proposed/restricted linux-restricted-modules 2.6.24.21.23 [26.5kB]
Get:2 http://no.archive.ubuntu.com hardy/universe madwifi-tools 1:0.9.3+dfsg-3 [40.5kB]
Fetched 67.0kB in 0s (149kB/s)                
Selecting previously deselected package linux-restricted-modules.
(Reading database ... 100751 files and directories currently installed.)
Unpacking linux-restricted-modules (from .../linux-restricted-modules_2.6.24.21.23_i386.deb) ...
Selecting previously deselected package madwifi-tools.
Unpacking madwifi-tools (from .../madwifi-tools_1%3a0.9.3+dfsg-3_i386.deb) ...
Setting up linux-restricted-modules (2.6.24.21.23) ...
Setting up madwifi-tools (1:0.9.3+dfsg-3) ...

```

All done. i don't know why it shows up AR2413 driver. I downloaded the AR5005G drivers that i use for XP, also i got them from Acer aspire 5040 driver support site. i then installed with ndiswrapper.

---

### Post by darkchron on 2008-09-13
Error message on iwlist scan has changed: 

skyggen@skyggen-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

---

