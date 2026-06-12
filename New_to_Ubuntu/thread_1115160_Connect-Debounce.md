---
title: "Connect-Debounce"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by LeWench on 2009-04-03
Hello,
 I recently purchased the Asus EEE PC 1000. I have installed Ubuntu 8.10 with the custom array kenel ([http://array.org/ubuntu/setup-intrepid.html](http://array.org/ubuntu/setup-intrepid.html))  I have also installed EEE-Control which shouldn't matter but just in case ([http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)). Everything is working as intended. USB's work (can connect external HD, as well as flash drives). Camera, bluetooth (for my mouse).

My issue:
When I insert an SD card onto the built in card reader (Non HC, its a 1G lexar SD card, also tried PNY 1G SD Card) I get this message output: 
  
"hub 1-0:1.0: connect-debounce failed, port 5 disabled"

I have read on this, but have failed to find a solution, or even a temp solution. I have seen post dates going back to 2006, still with no solution. I have come onto the forums as last resort, as I have already talked with individuals in IRC (#ubuntu,#eeepc)

I have ordered a 32GB SD card, with the luck of this working, I tried out a memory card I had laying around just to make sure this worked before my new card arrives. I did not know this could be so tedious. 

Does anyone have the solution to this problem, or can point me in the right direction? Thanks in advanced for your help.

---

### Post by Hospadar on 2009-04-03
with an sdcard that's been properly formatted in the drive, what do your
df -h
sudo fdisk -l
look like?
how about 
sudo lshw
Could you post the results in "code" blocks?

---

### Post by LeWench on 2009-04-03
**_df -h_**

```
lewench@EEE-PC:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.1G  3.6G  3.2G  54% /
tmpfs                1009M     0 1009M   0% /lib/init/rw
varrun               1009M   96K 1008M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M  2.8M 1006M   1% /dev
tmpfs                1009M  200K 1008M   1% /dev/shm
/dev/sdb1              30G  938M   28G   4% /home
```

**_sudo fdisk -l_**

```
lewench@EEE-PC:~$ sudo fdisk -l

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90599059

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux
```

**_sudo lshw_**

```
lewench@EEE-PC:~$ sudo lshw
eee-pc                    
    description: Notebook
    product: 1000
    vendor: ASUSTeK Computer INC.
    version: x.x
    serial: EeePC-1234567890
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=1 uuid=00879721-845C-DD81-2A6A-00221575B6A2
  *-core
       description: Motherboard
       product: 1000
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.xx
       serial: EeePC-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0702 (07/14/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: PBGA 437
          size: 800MHz
          capacity: 1666MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: b0
                serial: 00:22:15:75:b6:a2
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: RaLink
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: ra0
                version: 00
                serial: 00:15:af:e6:34:39
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2860 ip=192.168.1.113 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
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
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: ASUS-PHISON SSD
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: TST2
                serial: SOQ1782263
                size: 7695MiB (8069MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=294a294a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 137d6825-a3f0-451e-8aac-e18d65300889
                   size: 7318MiB
                   capacity: 7318MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-03-27 11:37:42 filesystem=ext3 modified=2009-04-03 15:01:19 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-04-03 13:58:24 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 376MiB
                   capacity: 376MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 376MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ASUS-PHISON SSD
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: TST2
                serial: SOQ1782273
                size: 30GiB (32GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=90599059
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /home
                   version: 1.0
                   serial: 425afa86-fa68-458a-830e-f5cffd2c2620
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-03-27 11:38:02 filesystem=ext3 modified=2009-04-03 15:10:06 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2009-04-03 15:10:06 state=mounted
        *-serial
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0 module=i2c_i801
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:39:60:f3:3c:38
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Note: The card is Fat32. When I get the 32G SDHC card, I will convert that to ext3.

---

### Post by LeWench on 2009-04-04
Any help on this?

---

