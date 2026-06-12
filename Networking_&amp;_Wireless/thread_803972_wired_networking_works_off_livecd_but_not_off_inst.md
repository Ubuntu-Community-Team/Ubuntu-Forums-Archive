---
title: "wired networking works off livecd but not off installed system"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by gtaskeraus on 2008-05-22
Installed 8.04 a few weeks ago with a new Gigabyte motherboard.  Everything worked fine but in a recent update of the operating system the network stopped working.

I figure that the problem must be software related because I grabbed the live CD and threw it in to boot off and the network runs fine.  As a result I don't believe that it is a hardware problem.

I've tried a few things.  Some obvious and others not so obvious.

Anyhow here are some symptoms and results.

Sometimes dhcp will not work and other times it picks up a lease from the router.  The trouble is that even when it does trying to ping the router gives the error message "Network unreachable".  Pinging the local ip does return a ping echo.

As I mentioned before networking seems to work perfectly off the live CD.

So does anyone have some suggestions about what can be done to diagnose the problem apart from having to reinstall the whole box?

Here is some output from lshw under livecd

```
ubuntu
    description: Desktop Computer
    product: 945GCM-S2L
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-001D7D41F76F
  *-core
       description: Motherboard
       product: 945GCM-S2L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F4 (10/26/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
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
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
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
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G72 [GeForce 7300 SE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:7d:41:f7:6f
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.4 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD300LD
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: WK10
                serial: S0A5J1GL500736
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=06c406c4
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 11ac16d2-4183-4679-a161-9251a509da93
                   size: 40GiB
                   capacity: 40GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-04-27 14:29:05 filesystem=ext3 modified=2008-05-22 16:03:37 mounted=2008-05-22 15:51:35 state=clean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: dcf48b92-5791-4bd8-98d8-b3b6d69dbacc
                   size: 6542MiB
                   capacity: 6542MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: b060b0e2-38ff-43a1-8eaf-4177d9fee19e
                   size: 233GiB
                   capacity: 233GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-10-22 00:45:42 filesystem=ext3 modified=2008-05-22 09:10:01 mounted=2008-05-16 08:25:54 state=clean
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-H10N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: JL10
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3500630AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 5QG1HJRS
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0006b780
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 13bcbb52-aa71-4182-826c-7cf8d963bf44
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-05-13 12:07:46 filesystem=ext3 modified=2008-05-22 16:03:37 mounted=2008-05-22 15:51:36 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 2
          bus info: usb@5:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: USB DISK
             vendor: FLORAL
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 1100
             serial: &#65533;&#65533;&#65533;&#65533;&#65533; 1100&#65533;&#65533;
             size: 967MiB (1014MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 967MiB (1014MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=c3072e18
              *-volume
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/FLORAL
                   version: FAT16
                   serial: c2f8-e4f2
                   size: 967MiB
                   capacity: 967MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted
```

---

### Post by superprash2003 on 2008-05-22
could you post your ifconfig output from the terminal

---

### Post by gtaskeraus on 2008-05-23
OK here is the ifconfig first from the installed system

```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:41:f7:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:605618324 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:02:44:56:b9:fa  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe56:b9fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218650 (213.5 KB)  TX bytes:6863 (6.7 KB)
          Interrupt:20 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:7d:41:f7:6f  
          inet addr:169.254.7.226  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144396 (141.0 KB)  TX bytes:144396 (141.0 KB)

```

And now from the live cd

```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:41:f7:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3755182220 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:02:44:56:b9:fa  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe56:b9fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3088826 (2.9 MB)  TX bytes:414068 (404.3 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1030100 (1005.9 KB)  TX bytes:1030100 (1005.9 KB)

```

You will notice that a second network card has been added since I first posted.  The reason is that the onboard NIC stopped working for the live cd as well which means there could be some kind of hardware problem.  So now I'm back to where I started.

I've observed that the installed ifconfig output shows an extremely low transmit rate compared to its receive rate.  Maybe someone can tell me a story about this.

The router is reachable because dhcp is picking up a lease in both the installed and live cd situations.

---

### Post by superprash2003 on 2008-05-23
> The router is reachable because dhcp is picking up a lease in both the installed and live cd situations.
so whats the problem you are facing?so you mean you can access your router but not the internet? if so type ping google.com in the terminal and post output here

---

### Post by gtaskeraus on 2008-05-24
Well it turns out that the problem was the firewall setup I was getting the error message "Network port unreachable"

Another section of the forums clued me up to this.  So while I have the network working again I'll consider the cased closed for now.

I had moblock setup and it hadn't installed properly.  I tried to uninstall it but it wouldn't so I stopped the process using ```
/etc/init.d/moblock stop
``` and the internet came good.  I had to manually remove moblock seeing it wasn't playing nice with synaptic.

I found information I needed on iptables to help sort out the problem at
[http://ubuntuforums.org/showthread.php?t=445174&page=3]("http://ubuntuforums.org/showthread.php?t=445174&page=3")

So thank you very much for your assistance.

The final question will have to deal with why the onboard NIC stopped working in both the livecd and the installed version of ubuntu.  But that is a question that will have to wait until the exams are finished.  I'll just keep the system going tied together with bailing string until I can get it all sorted out properly until that time.

---

### Post by jre on 2008-05-24
If you want me to help you solve your moblock problems (either uninstall it or do a correct setup) feel free to post again after your exams.
For a start I need your version (dpkg --list moblock), your apt/synaptic/aptitude output and your /var/log/moblock-control.log.

---

