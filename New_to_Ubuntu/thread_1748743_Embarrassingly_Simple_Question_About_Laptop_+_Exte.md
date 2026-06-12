---
title: "Embarrassingly Simple Question About Laptop + External Monitor"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by WilliamAnderso on 2011-05-03
Hi. It's humiliating to admit I need help with a simple problem, but here it is. I installed Ubuntu 10.04 on a HP Pavilion dv6 laptop; I've got everything working except the monitor. When I try to plug a Samsung SyncMaster SA350 into either the analog or HDMI port on my laptop, and I run "Detect Monitor" on the preference menu that appears under System>Preferences>Monitors, the laptop stubbornly refuses to acknowledge the presence of a new monitor. Attempting to create an xorg.conf file via the X command in a root shell simply resulted in my computer refusing to acknowledge the presence of even the laptop's internal monitor. I believe the onboard video card is an integrated chip set, if that helps. Oh, and the processor is 64-bit.

What should I do? I've been unable to get this working for two straight days now.

---

### Post by Blasphemist on 2011-05-03
Let's start with having you post your laptop make and model, and the external display make and model. Also run this and post the results. Oh, and what connection are you trying to use on the laptop to the monitor?

```
sudo lshw
```

---

### Post by alphacrucis2 on 2011-05-04
> **WilliamAnderso said:**
> Hi. It's humiliating to admit I need help with a simple problem, but here it is. I installed Ubuntu 10.04 on a HP Pavilion dv6 laptop; I've got everything working except the monitor. When I try to plug a Samsung SyncMaster SA350 into either the analog or HDMI port on my laptop, and I run "Detect Monitor" on the preference menu that appears under System>Preferences>Monitors, the laptop stubbornly refuses to acknowledge the presence of a new monitor. Attempting to create an xorg.conf file via the X command in a root shell simply resulted in my computer refusing to acknowledge the presence of even the laptop's internal monitor. I believe the onboard video card is an integrated chip set, if that helps. Oh, and the processor is 64-bit.

What should I do? I've been unable to get this working for two straight days now.

If the graphics card in the laptop has a proprietary driver available, then using that may fix the problem. I find that the open source drivers don't always support these extra features well. To get external monitors to work properly with my own laptop (which has an ATI HD3400), I have to use the AMD/ATI Catalyst driver. Even though the open source driver for my card has come ahead leaps and bounds over the last couple of years, it's still not quite there. Your problem may be similar depending on which specific graphics card your laptop has.

---

### Post by WilliamAnderso on 2011-05-04
**EDIT: To be specific, the laptop is a store-bought HP Pavilion dv6-6013cl. The monitor is a SyncMaster SA350 from Samsung.**

Here is the output of sudo lshw:

wanderso@araran:~$ sudo lshw
[sudo] password for wanderso: 
araran                    
    description: Notebook
    product: HP Pavilion dv6 Notebook PC
    vendor: Hewlett-Packard
    version: 0595100000244710000020100
    serial: 5CH11208H1
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=E1567F20-23AC-4822-465A-68B599E19491
  *-core
       description: Motherboard
       product: 1658
       vendor: Hewlett-Packard
       physical id: 0
       version: 10.1C
       serial: PBWQK03HT061V9
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.05 (02/10/2011)
          size: 1MiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: 845BF66A
             slot: Bottom - Slot 1 (top)
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 1
             serial: 845BF669
             slot: Bottom - Slot 2 (under)
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          slot: CPU1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 1d
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 1e
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 1f
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
     *-cache
          description: L1 cache
          physical id: 1c
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Sandy Bridge PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:5000(size=4096) memory:c7500000-c84fffff ioport:c0400000(size=16777216)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:6000(size=64)
        *-communication UNCLAIMED
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:c8504000-c850400f
        *-usb:0
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c850a000-c850a3ff
        *-multimedia
             description: Audio device
             product: Cougar Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:c8500000-c8503fff
        *-pci:1
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:c6500000-c74fffff ioport:c1400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 06
                serial: 68:b5:99:e1:94:91
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:4000(size=256) memory:c1404000-c1404fff(prefetchable) memory:c1400000-c1403fff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096) memory:c5500000-c64fffff ioport:c2400000(size=16777216)
           *-network
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0d:00.0
                logical name: eth1
                version: 01
                serial: ac:81:12:35:bb:c2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.1.25 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:c5500000-c5503fff
        *-pci:3
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:2000(size=4096) memory:c4500000-c54fffff ioport:c3400000(size=16777216)
           *-generic UNCLAIMED
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:13:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c4500000-c4500fff memory:c3400000-c340ffff(prefetchable)
        *-pci:4
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 memory:c4400000-c44fffff
           *-usb
                description: USB Controller
                product: NEC Corporation
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:19:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:c4400000-c4401fff
        *-usb:1
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:c8509000-c85093ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Cougar Point 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:6088(size=8) ioport:609c(size=4) ioport:6080(size=8) ioport:6098(size=4) ioport:6060(size=32) memory:c8508000-c85087ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PB4O
                serial: 110205PBG408M7J31TUV
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00005426
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: c46619e5-bbef-4328-ad4b-f6901aeb3d84
                   size: 454GiB
                   capacity: 454GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-05-02 07:14:52 filesystem=ext4 lastmountpoint=/8&#65533;?I&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;?I&#65533;&#65533;&#65533;Q&#65533;J&#65533;&#65533;&#65533;S&#65533;G&#65533;&#65533;&#65533;&#65533;&#65533;OG&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;hTG&#65533; modified=2011-05-02 14:23:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-03 19:07:58 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633R
                vendor: hp
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/Fedora 14 x86_64 DVD
                version: 0300
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/Fedora 14 x86_64 DVD
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: Cougar Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c8506000-c85060ff ioport:6040(size=32)
  *-battery
       description: Lithium Ion Battery
       product: MU06055
       vendor: 11-85
       physical id: 1
       slot: Primary
       capacity: 55080mWh
       configuration: voltage=10.8V

---

### Post by Bluenoser81 on 2011-05-04
```
sudo lshw
```[/QUOTE]

Just wondering, is there a GUI version of this output, or something similar? Seems like there should be something equivalent to Device Manager in Windows installed by default that is easy to find. I'm not on my Ubuntu right now, but I don't remember seeing one. I remember having to run things like "sudo lspci" and stuff to see card details.

---

### Post by joe carolan on 2011-05-04
For what its worth I have been having problems for days getting my samsung ext monitor to work and see some items in your post that may be similar to my problem.
I have got my monitor working after natty upgrade by loading older kernel 2.6.35.29
selecting at boot and also selecting classic menu from login
although monitor works in unity with this kernel,i have seen other problems ,such as crashes in Firefox. I have used this older kernel with no problems in classic and my ext monitor works fine
Let me know if this helps
joe

---

### Post by Blasphemist on 2011-05-04
William- I have found another thread with people on natty and your integrated graphics controller that are also having trouble with the use of a second monitor. This thread is going on in parallel with this one. [http://ubuntuforums.org/showthread.php?t=1728526&page=2](http://ubuntuforums.org/showthread.php?t=1728526&page=2)

It seems you may have the opposite issue of common, your gpu may be so new that the best driver for it isn't known or there may not be a good one yet. You are on 10.04 right? Natty still seems to have an issue with a driver for the Intel HD Graphics 3000. I'd add yourself to the other thread and include the VGA section of the lshw you attached. Or this allows you to just output the graphics info.

```
sudo lshw -C video
```

You can see that you are not using the same driver the natty guys are using, i915. I don't see any reason to have you load it since they are still having issues. I do recommend that all having issues do get bugs reported on launchpad as I'm sure there is work being done on drivers for this gpa.

---

