---
title: "Ubuntu Issues"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by nebu on 2008-12-14
Whenever i use ubuntu over a prolonged period of time.... say over a period of 5-6 hrs.....

evrything just goes hay wire.... all my files get read only permissions and then i cant even shut down the computer properly..... i cant unmount any hard drives....when i try to retstart from the kernel using "ctrl+alt+printscr+R+S+E+I+U+B" .... nothing happens..... then the firefox, amarok and a whole lot of apps dont work.....



is this some sort of bug on ubuntu....

how can i fix this??:confused::confused:

---

### Post by Michael.Godawski on 2008-12-14
Which version of Ubuntu are you using?
The behavior you described seems to be like an invisible hand was causing damage to your system.
Spooky..but not very likely.

Can you give us some more details, like your specs?
```

sudo lshw
```

---

### Post by cmnorton on 2008-12-14
The first thing I would do would be to boot this system using a recovery disk of your choice (like Knoppix) or the "live" Ubuntu CD. Mount the drive containing "/". Look in /etc/crontab to see if you have any jobs running you do not know about. I would also look under /var/spool and then cron (if my memory serves me correctly) to see if there are active crontab files there.

Also, look in your logs. /var/log/syslog, /var/log/messages.

When you boot into this system, look also at the output of dmesg.

It sounds like you have an errant batch job running. 

I suggest minimally asking this as a question in Ubuntu launchpad -- [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by nebu on 2008-12-14
here is what i get....

```


subho@Mindstorm:~$ sudo lshw
[sudo] password for subho: 
mindstorm                 
    description: Notebook
    product: HP Compaq 6710b
    vendor: Hewlett-Packard
    version: F.11
    serial: SGH8260SP1
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=71481D49-8948-DD11-1998-08B3102B8529
  *-core
       description: Motherboard
       product: 30C0
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 71.2E
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68DDU Ver. F.11 (04/10/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          slot: U10
          size: 2001MHz
          capacity: 2001MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: JM667QSU-2G
             vendor: 7F4F000000000000
             physical id: 0
             serial: 0007CF72
             slot: DIMM #1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: JM667QSU-2G
             vendor: 7F4F000000000000
             physical id: 1
             serial: 00001111
             slot: DIMM #2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
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
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
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
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1f:3c:82:e5:33
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=10.0.0.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:18:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:29:93:be:29
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 4
                bus info: pci@0000:02:04.0
                version: b6
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00603020-b0060301f
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 4.1
                bus info: pci@0000:02:04.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-860H
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: ST9320320AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SD03
                serial: 5SX0X65H
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9ef688ec
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 22fd25b6-a5ca-e447-bc28-49c52b211942
                   size: 140GiB
                   capacity: 140GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-12-13 08:05:13 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: c6c8b641-c010-f744-b220-9a843cbf433c
                   size: 6476MiB
                   capacity: 6477MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-12-13 08:05:20 filesystem=ntfs label=HP_RECOVERY state=clean
              *-volume:2
                   description: FAT16 partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 1589MiB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 148GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
  *-battery
       description: Lithium Ion Battery
       product: HP
       vendor: Hewlett-Packard
       physical id: 1
       version: 06/11/2008
       serial: 01787
       slot: Primary
       capacity: 52000mWh
       configuration: voltage=10.8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:ea:41:5a:c3:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



```

---

### Post by unutbu on 2008-12-14
By default, Ubuntu mounts your root filesystem with the option "errors=remount-ro". Because of this option, if an error is found while writing to the filesystem, the filesystem is remounted in read-only mode. This might be what is happening to you.

If this is the case, you might see error messages related to writing to your hard drive in /var/log/messages or /var/log/syslog.
Perhaps open these files in a text editor and see if you can find any error messages, then please post them here.

---

### Post by nebu on 2008-12-14
the error happened at around this time of the log....

here is the entry on my /var/log/messages file
```

Dec 14 18:51:55 Mindstorm -- MARK --
Dec 14 19:11:55 Mindstorm -- MARK --
Dec 14 19:31:55 Mindstorm -- MARK --
Dec 14 19:38:14 Mindstorm kernel: [20799.000157] Clocksource tsc unstable (delta = -110333845 ns)
Dec 14 19:40:35 Mindstorm kernel: [20939.956145] CE: hpet increasing min_delta_ns to 22500 nsec
Dec 14 19:51:55 Mindstorm -- MARK --
Dec 14 20:06:02 Mindstorm kernel: [22466.520146] CE: hpet increasing min_delta_ns to 33750 nsec
Dec 14 20:31:55 Mindstorm -- MARK --
Dec 14 20:39:12 Mindstorm kernel: [24456.836326] synfigstudio[30824]: segfault at 0 ip 00007fbf022882ca sp 00007fff0c1ac4a0 error 4 in libgtkmm-2.4.so.1.0.30[7fbf01f8d000+39e000]
Dec 14 20:47:58 Mindstorm kernel: [24982.676026] swami[10682]: segfault at 0 ip 00007fe47a8c6f53 sp 00007fff84bb04b0 error 4 in libc-2.8.90.so[7fe47a84b000+169000]
Dec 14 20:48:24 Mindstorm kernel: [25008.258258] awn-manager[11111]: segfault at 40 ip 00007f4452143124 sp 00007fff5b7d0ca0 error 4 in libgobject-2.0.so.0.1800.2[7f4452134000+44000]
Dec 14 20:58:37 Mindstorm kernel: [25621.252102] usb 7-3: new high speed USB device using ehci_hcd and address 4
Dec 14 20:58:37 Mindstorm kernel: [25621.389367] usb 7-3: configuration #1 chosen from 2 choices
Dec 14 20:58:37 Mindstorm kernel: [25621.410459] scsi6 : SCSI emulation for USB Mass Storage devices
Dec 14 20:58:42 Mindstorm kernel: [25626.427330] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Dec 14 20:58:42 Mindstorm kernel: [25626.433777] sd 6:0:0:0: [sdb] 991232 2048-byte hardware sectors (2030 MB)
Dec 14 20:58:42 Mindstorm kernel: [25626.434756] sd 6:0:0:0: [sdb] Write Protect is off
Dec 14 20:58:42 Mindstorm kernel: [25626.438516] sd 6:0:0:0: [sdb] 991232 2048-byte hardware sectors (2030 MB)
Dec 14 20:58:42 Mindstorm kernel: [25626.439763] sd 6:0:0:0: [sdb] Write Protect is off
Dec 14 20:58:42 Mindstorm kernel: [25626.440424]  sdb: sdb1 sdb2
Dec 14 20:58:42 Mindstorm kernel: [25626.445914] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Dec 14 20:58:42 Mindstorm kernel: [25626.446430] sd 6:0:0:0: Attached scsi generic sg2 type 0
Dec 14 21:14:13 Mindstorm syslogd 1.5.0#2ubuntu6: restart.
Dec 14 21:14:13 Mindstorm kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec 14 21:14:13 Mindstorm kernel: Cannot find map file.
Dec 14 21:14:13 Mindstorm kernel: Loaded 54153 symbols from 98 modules.
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)

```


and here is my /var/log/syslog file....
```

Dec 14 20:06:02 Mindstorm kernel: [22466.520146] CE: hpet increasing min_delta_ns to 33750 nsec
Dec 14 20:11:03 Mindstorm NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Dec 14 20:11:03 Mindstorm NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Dec 14 20:17:01 Mindstorm /USR/SBIN/CRON[31817]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 14 20:31:55 Mindstorm -- MARK --
Dec 14 20:39:12 Mindstorm kernel: [24456.836326] synfigstudio[30824]: segfault at 0 ip 00007fbf022882ca sp 00007fff0c1ac4a0 error 4 in libgtkmm-2.4.so.1.0.30[7fbf01f8d000+39e000]
Dec 14 20:41:05 Mindstorm NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Dec 14 20:41:05 Mindstorm NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Dec 14 20:47:58 Mindstorm kernel: [24982.676026] swami[10682]: segfault at 0 ip 00007fe47a8c6f53 sp 00007fff84bb04b0 error 4 in libc-2.8.90.so[7fe47a84b000+169000]
Dec 14 20:48:24 Mindstorm kernel: [25008.258258] awn-manager[11111]: segfault at 40 ip 00007f4452143124 sp 00007fff5b7d0ca0 error 4 in libgobject-2.0.so.0.1800.2[7f4452134000+44000]
Dec 14 20:58:37 Mindstorm kernel: [25621.252102] usb 7-3: new high speed USB device using ehci_hcd and address 4
Dec 14 20:58:37 Mindstorm kernel: [25621.389367] usb 7-3: configuration #1 chosen from 2 choices
Dec 14 20:58:37 Mindstorm kernel: [25621.410459] scsi6 : SCSI emulation for USB Mass Storage devices
Dec 14 20:58:37 Mindstorm kernel: [25621.424634] usb-storage: device found at 4
Dec 14 20:58:37 Mindstorm kernel: [25621.424646] usb-storage: waiting for device to settle before scanning
Dec 14 20:58:42 Mindstorm kernel: [25626.424525] usb-storage: device scan complete
Dec 14 20:58:42 Mindstorm kernel: [25626.427330] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Dec 14 20:58:42 Mindstorm kernel: [25626.433777] sd 6:0:0:0: [sdb] 991232 2048-byte hardware sectors (2030 MB)
Dec 14 20:58:42 Mindstorm kernel: [25626.434756] sd 6:0:0:0: [sdb] Write Protect is off
Dec 14 20:58:42 Mindstorm kernel: [25626.434762] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
Dec 14 20:58:42 Mindstorm kernel: [25626.434767] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 14 20:58:42 Mindstorm kernel: [25626.438516] sd 6:0:0:0: [sdb] 991232 2048-byte hardware sectors (2030 MB)
Dec 14 20:58:42 Mindstorm kernel: [25626.439763] sd 6:0:0:0: [sdb] Write Protect is off
Dec 14 20:58:42 Mindstorm kernel: [25626.439774] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
Dec 14 20:58:42 Mindstorm kernel: [25626.439778] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 14 20:58:42 Mindstorm kernel: [25626.440424]  sdb: sdb1 sdb2
Dec 14 20:58:42 Mindstorm kernel: [25626.445914] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Dec 14 20:58:42 Mindstorm kernel: [25626.446430] sd 6:0:0:0: Attached scsi generic sg2 type 0
Dec 14 20:58:43 Mindstorm hald: mounted /dev/sdb2 on behalf of uid 1000
Dec 14 21:14:13 Mindstorm syslogd 1.5.0#2ubuntu6: restart.
Dec 14 21:14:13 Mindstorm kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec 14 21:14:13 Mindstorm kernel: Cannot find map file.
Dec 14 21:14:13 Mindstorm kernel: Loaded 54153 symbols from 98 modules.
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] Command line: root=UUID=28ead792-1136-44cd-947a-58ae53531e80 ro quiet splash
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] KERNEL supported cpus:
Dec 14 21:14:13 Mindstorm kernel: [    0.000000]   Intel GenuineIntel
Dec 14 21:14:13 Mindstorm kernel: [    0.000000]   AMD AuthenticAMD
Dec 14 21:14:13 Mindstorm kernel: [    0.000000]   Centaur CentaurHauls
Dec 14 21:14:13 Mindstorm kernel: [    0.000000] BIOS-provided physical RAM map:

```

---

### Post by nebu on 2008-12-15
bump...

---

### Post by cmnorton on 2008-12-16
Force fsck to run on the next reboot:

sudo touch /forcefsck

[http://ubuntuforums.org/showthread.php?t=708530&highlight=forcing+fsck+reboot](http://ubuntuforums.org/showthread.php?t=708530&highlight=forcing+fsck+reboot)

I believe CTRL+F1 gets you to a full boot up screen. See what happens during boot.

---

