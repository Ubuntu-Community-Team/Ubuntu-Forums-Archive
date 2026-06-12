---
title: "ASUS M70 Atheros madwifi problem"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by sudo_chop on 2008-08-17
I have a new ASUS M70 laptop with an Atheros card (not sure which one, dont know how to tell) and it doesn't work. I've been searching and it doesn't seem like anything I have found is relevant, because on mine nothing shows up in the restriced drivers, it says no proprietary drivers are in use on this system. Is there something I need to configure in madwifi to get it to work? Maybe the newest madwifi package? Do I need to find out exactly what card I have first? I really don't even know where to start here. Maybe this from my lspci -v will be helpful.

```
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
        Subsystem: Unknown device 1a3b:1067
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
```

Please help! :confused:

---

### Post by sudo_chop on 2008-08-18
bump :confused:

---

### Post by jualin on 2008-08-18
If you can locate the Windows drivers for your card you can use Ndiswrapper to make them work with Linux. Check my signature for more information. If you are not able to connect your laptop using an Ethernet cable then you need to use the Ubuntu Live CD to get the Ndiswrapper utility from it. To do this open Synaptic Package Manager under System, Administration and then select Settings, Repositories and check the Live CD as a download source.

---

### Post by Mgiacchetti on 2008-09-26
If you have the asus m70vM-x1 its probably the Atheros AR928x (i'm having the same problems with it and NO INTREPID does NOT fix the issue)

---

### Post by Mgiacchetti on 2008-09-26
Atheros AR928x  chipset

uname -a
```

Linux ubuntu 2.6.27-3-generic #1 SMP Wed Sep 10 16:02:00 UTC 2008 i686 GNU/Linux

```lspci -nn
```

Network controller [0280]: Atheros Communications Inc. Device [168c:002a] (rev 01)

```ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:15:af:dd:7c:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-DD-7C-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```dmesg |grep wlan0
```

[   55.857897] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``` dmesg |grep Atheros
```


[   41.906100] phy0: Atheros 9280: mem=0xf8be0000, irq=17

```

---

### Post by TDragon on 2008-09-26
> **Mgiacchetti said:**
> If you have the asus m70vM-x1 its probably the Atheros AR928x (i'm having the same problems with it and NO INTREPID does NOT fix the issue)
 
 
Me Too!

---

### Post by jualin on 2008-09-26
Can you please go to the terminal and post the output of > lshw

---

### Post by jualin on 2008-09-26
Also you may want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?p=5637017") which will direct you eventually to [this other thread.]("http://ubuntuforums.org/showthread.php?t=874097") Maybe you can give the new ath9k driver a try. Hope this helps!

---

### Post by Mgiacchetti on 2008-09-26
> **jualin said:**
> Can you please go to the terminal and post the output of


```

ubuntu
    description: Notebook
    product: M70Vm
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: NF1S8716550205
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: chassis=notebook cpus=2 uuid=005E0483-1954-DD81-3A5A-002215565EC2
  *-core
       description: Motherboard
       product: M70Vm
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 206.000 (07/07/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: Socket 478
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 267MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts nopl pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
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
     *-cache
          description: L1 cache
          physical id: 6
          slot: L1-Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: N/A
             vendor: N/A
             physical id: 0
             serial: N/A
             slot: SODIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: N/A
             vendor: N/A
             physical id: 1
             serial: N/A
             slot: SODIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 2534MHz
          capacity: 2534MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Cantiga Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Cantiga PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 01
                serial: 00:15:af:dd:7c:c9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 02
                serial: 00:22:15:56:5e:c2
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:07:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:07:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:07:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:07:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXE408DL3273
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=97646c29
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 88771ed4-9ab5-b247-83e6-ab84e996a6ac
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-09-21 03:33:38 filesystem=ntfs label=VistaOS state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 139GiB
                   capacity: 139GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 139GiB
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/DRIVER_CD_VISTA_10
                version: AS00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=999,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/DRIVER_CD_VISTA_10
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=999,utf8 state=mounted
     *-scsi
          physical id: 2
          bus info: usb@8:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 983MiB (1030MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=3a8b6561
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT16
                serial: d40b-9ee2
                size: 982MiB
                capacity: 982MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 state=mounted
  *-battery
       description: Other Battery
       product: M70--26
       vendor: AS011OM33F
       physical id: 1
       version: 08/05/30
       serial: 0927
       slot: In the back
       capacity: 5060mWh
       configuration: voltage=14.8V

```

---

### Post by Mgiacchetti on 2008-09-26
> **jualin said:**
> Also you may want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?p=5637017") which will direct you eventually to [this other thread.]("http://ubuntuforums.org/showthread.php?t=874097") Maybe you can give the new ath9k driver a try. Hope this helps!

lol, interesting...  intrepid comes with the ath9k driver. AND  i have seen both of those already...

I changed from network manager to wicd

---

### Post by jualin on 2008-09-26
According to your output you are using the ath9k driver. You can get a more concise result by using > lshw -C network I should have mentioned that before.

Basically this is the important part of the output> *-network
                description: Wireless interface
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 01
                serial: 00:15:af:dd:7c:c9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
 
As you can see the driver being used is the ath9k and the module is the ath9k, so probably the suggestion above will not help you. What I can suggest is using Ndiswrapper. The only tricky part about it is that you need to get the Windows drivers. After you get the Windows drivers, you can follow the tutorial on my signature. I was using Ndiswrapper on Hardy and it worked really well, I also have a similar atheros card. Now on Intrepid the ath5k module takes care of the wireless for me.

---

### Post by Mgiacchetti on 2008-09-26
> **jualin said:**
> According to your output you are using the ath9k driver. You can get a more concise result by using  I should have mentioned that before.

Basically this is the important part of the output 
As you can see the driver being used is the ath9k and the module is the ath9k, so probably the suggestion above will not help you. What I can suggest is using Ndiswrapper. The only tricky part about it is that you need to get the Windows drivers. After you get the Windows drivers, you can follow the tutorial on my signature. I was using Ndiswrapper on Hardy and it worked really well, I also have a similar atheros card. Now on Intrepid the ath5k module takes care of the wireless for me.

I think it has to do with the bluetooth being in there as well...

I have vista set up a certian way..  

bluetooth off
wifi on

when i restart into vista after trying to get ubuntu on wifi, bluetooth is on and wifi is off...

any ideas??
again i have the asus m70vm-x1

---

### Post by Mgiacchetti on 2008-09-26
can i echo my wifi on?

in fixing another problem, my light sensor continually turns the screen really dark in ubuntu. since the fn's dont work, i have to 
```

echo 0 > /sys/devices/platform/asus-laptop/ls_switch

```Is there a way to do this to the bluetooth and wifi to turn them off and on, respectively?

---

### Post by Mgiacchetti on 2008-09-26
YES YOU CAN!!!

Please note this is only known to work for the ASUS M70 SERIES if you think you have this problem NAVIGATE TO /SYS/DEVICES/PLATFORM/ASUS-LAPTOP AND CHECK FOR THE BELOW FILES, TO SEE IF THEY ARE 0 OR 1


```

sudo su
echo 1 > /sys/devices/platform/asus-laptop/wlan
echo 0 > /sys/devices/platform/asus-laptop/bluetooth

```

---

### Post by jualin on 2008-09-27
> **Mgiacchetti said:**
> YES YOU CAN!!!

Please note this is only known to work for the ASUS M70 SERIES if you think you have this problem NAVIGATE TO /SYS/DEVICES/PLATFORM/ASUS-LAPTOP AND CHECK FOR THE BELOW FILES, TO SEE IF THEY ARE 0 OR 1


```

sudo su
echo 1 > /sys/devices/platform/asus-laptop/wlan
echo 0 > /sys/devices/platform/asus-laptop/bluetooth

```
:confused::confused:So did you solve your problem?:confused::confused:

---

### Post by Mgiacchetti on 2008-09-27
> **jualin said:**
> :confused::confused:So did you solve your problem?:confused::confused:

ok, long story short, the above that i posted turns the bluetooth off, and the wifi on, however my transmit and receive speeds vary per second...

example. 

I boot.  good everything allright.

run the commands (i have ubuntu on a usb non-persistent for testing until i can get it working good) and connect to the router and get an ip, great.

my signal will go anywhere from 20% to 115% every minute...

yes i will type in an address it will load halfway, then get stuck for like 5 min...
i hit reload nothing....

this happens right next to the router, and as far away as i can get.

so far, nothing i have done has corrected this problem.

---

### Post by Mgiacchetti on 2008-09-28
**STATUS UPDATE**
Please review this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270748/") for up to date information regarding this issue.

---

### Post by GnuBoi on 2008-11-01
ath9k driver in interpid are not enabled in default...

---

### Post by Post Monkeh on 2009-01-20
> **Mgiacchetti said:**
> lol, interesting...  intrepid comes with the ath9k driver. AND  i have seen both of those already...

I changed from network manager to wicd

was having a similar problem (sometimes my connection would work fro ages then just stop connecting until a reboot)

out of curiosity i tried the girlfriend's belkin wireless adapter and i got exactly the same problem.

a shift to wicd seems to be doing the trick so far, i suspect the problem was with network manager, though i'm pretty new to ubuntu and linux in general so i could be wrong.

---

### Post by Post Monkeh on 2009-01-21
lol.

wicd won't let me connect to the net through my mobile usb connection.  nothing's easy.

---

