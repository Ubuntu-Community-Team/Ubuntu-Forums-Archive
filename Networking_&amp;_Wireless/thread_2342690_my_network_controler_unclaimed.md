---
title: "my network controler unclaimed"
date: 2016-11-09
forum: Networking &amp; Wireless
---

### Post by ghulam_mustafa3 on 2016-11-09
as i am using windows 10 and my wifi network working fine and as i switch from window to ubuntu 16.04 LTS my wifi not working at all and im search it a lot on google and try all solution but nothing to work for me and im frustrationg. I try **sudo lshw -C network** the following are 

```
*-network UNCLAIMED
       description: Network controller
       product: MEDIATEK Corp.
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0600000-d06fffff
```
and i also use **sudo lshw** and the following are the 

```
umachine                  
    description: Notebook
    product: HP ProBook 450 G1 (F3K30PA#ABG)
    vendor: Hewlett-Packard
    version: A3009DD10303
    serial: 2CE3461YXB
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N L=BUS B=HP S=PRO sku=F3K30PA#ABG uuid=FFC86301-BB50-E311-9673-CE39E75C1B10
  *-core
       description: Motherboard
       product: 1942
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 89.10
       serial: PDWTF1B2D5PERH
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: c
          version: L74 Ver. 01.05
          date: 11/04/2013
          size: 64KiB
          capacity: 6528KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4200M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4200M CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2501MHz
          capacity: 2501MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 4
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: asynchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 6
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 99U5469-045.A00LF
             vendor: Kingston
             physical id: 0
             serial: 14064181
             slot: Top - Slot 1 (top)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 9905474-011.A00LF
             vendor: Kingston
             physical id: 1
             serial: 13082019
             slot: Top - Slot 2 (under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Haswell DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Haswell Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:49 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:d0910000-d0913fff
        *-usb:0
             description: USB controller
             product: Lynx Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:d0900000-d090ffff
        *-communication
             description: Communication controller
             product: Lynx Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:48 memory:d0919000-d091900f
        *-usb:1
             description: USB controller
             product: Lynx Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d091e000-d091e3ff
        *-multimedia:1 UNCLAIMED
             description: Audio device
             product: Lynx Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:d0914000-d0917fff
        *-pci:0
             description: PCI bridge
             product: Lynx Point PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:d0800000-d08fffff ioport:bf300000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Lynx Point PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:d0700000-d07fffff ioport:d0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 0c
                serial: 8c:dc:d4:cc:c7:63
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-1_0.0.3 10/23/12 ip=192.200.200.50 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:47 ioport:3000(size=256) memory:d0700000-d0700fff memory:d0400000-d0403fff
        *-pci:2
             description: PCI bridge
             product: Lynx Point PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:d0600000-d06fffff
           *-network UNCLAIMED
                description: Network controller
                product: MEDIATEK Corp.
                vendor: MEDIATEK Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:d0600000-d06fffff
        *-pci:3
             description: PCI bridge
             product: Lynx Point PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:d0500000-d05fffff ioport:bf500000(size=2097152)
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:45 memory:d0500000-d0500fff
        *-usb:2
             description: USB controller
             product: Lynx Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:d091d000-d091d3ff
        *-isa
             description: ISA bridge
             product: Lynx Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Lynx Point 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:d091c000-d091c7ff
     *-scsi:0
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABF0
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: AM0P
             serial: 843JC1GGT
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000acebb
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: b078458c-9783-41f9-9b4a-2b5bab2bb898
                size: 457GiB
                capacity: 457GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-11-08 22:45:17 filesystem=ext4 lastmountpoint=/ modified=2016-11-09 10:15:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-11-09 10:15:14 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 8072MiB
                capacity: 8072MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8072MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8C2
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: FP09093
       vendor: 13-24
       physical id: 1
       slot: Primary
       capacity: 93240mWh
       configuration: voltage=11.1V
```
so please healp me how i can install wifi driver so that it working on my ubunru os 16.04 LTS. Thanks

---

### Post by mörgæs on 2016-11-09
I think you will get more support in the networking forum: [https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)
Please see the sticky notes there.

---

### Post by ajgreeny on 2016-11-09
*Thread moved to **Networking & Wireless**.* which is more appropriate for the problem and should be a better fit.

As suggested by mörgæs you will get better help by using the Wireless-info link in my signature at the bottom of my post.  Run the script shown in that thread and post the output back here.

Please use code-tags for terminal output; see my signature below again for a How-To.

---

### Post by Geoffrey_Arndt on 2016-11-09
Maybe another forum member will post if a driver exists, and how it can be installed . . . . BUT,  until then, here is a link to a source for Linux usb wireless adapters . . just plug & play, and cost is $10.00 usd:

These are excellent devices, well supported and require no driver install in most cases.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

