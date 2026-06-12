---
title: "Toshiba L655-S5075 / Realtek RTL8191SEvB: Hard Freeze When Disconnected From Wireless"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by Connor_Strandt on 2013-10-04
I have been searching for this for a couple weeks now, when I am at work using my Toshiba l655-s5105 (specs [http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=489121](http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=489121) ) [ the only difference is I have a 500GB HDD ] and disconnected from internet or tethered through my cell ubuntu (12.04) will randomly freeze (hard reset required), can't find any issue in logs or anything. The only thing that changes from my house to work is the fact that it is not connected via wireless or I'm tethered but it happens only when disconnected from wireless. Has anyone else had this issue, or does anyone have any suggestions? If any other information is needed I can provide, though it would be later tonight.

---

### Post by mörgæs on 2013-10-05
Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by Connor_Strandt on 2013-10-05
```

computer    description: Notebook
    product: Satellite L655 (PSK2GU-00Q009)
    vendor: TOSHIBA
    version: PSK2GU-00Q009
    serial: [REMOVED]
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=notebook family=Intel_Mobile sku=PSK2GU-00Q009 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Base Board Product Name
       vendor: Intel Corp.
       physical id: 0
       version: Base Board Version
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: 2.80
          date: 07/03/2012
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: CM3X4GSD1066
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             width: 8 bits
             clock: 1067MHz (0.9ns)
        *-bank:2
             description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
             product: CM3X4GSD1066
             physical id: 2
             serial: [REMOVED]
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1067 MHz (0.9 ns) [empty]
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
             width: 8 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 2b
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
          slot: CPU
          size: 933MHz
          capacity: 933MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: 2c
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 2e
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 2f
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 2d
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
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:d6000000-d60fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:c0000000-cfffffff ioport:5000(size=256) memory:d6000000-d600ffff memory:d6020000-d603ffff
           *-multimedia
                description: Audio device
                product: RV710/730 HDMI Audio [Radeon HD 4000 series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:44 memory:d6010000-d6013fff
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
             configuration: driver=mei latency=0
             resources: irq:42 memory:d6106100-d610610f
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
             resources: irq:16 memory:d6105c00-d6105fff
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
             resources: irq:43 memory:d6100000-d6103fff
        *-pci:1
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
             resources: irq:17 ioport:4000(size=4096) memory:d5000000-d5ffffff ioport:d0000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:d4000000-d4ffffff ioport:d1000000(size=16777216)
           *-network
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=3.8.0-31-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 ioport:3000(size=256) memory:d4000000-d4003fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:d3000000-d3ffffff ioport:d2000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: c1
                serial: [REMOVED]
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:d3000000-d303ffff ioport:2000(size=128)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d6105800-d6105bff
        *-pci:4
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
             resources: irq:41 ioport:6048(size=8) ioport:6054(size=4) ioport:6040(size=8) ioport:6050(size=4) ioport:6020(size=32) memory:d6105000-d61057ff
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
             resources: memory:d6106000-d61060ff ioport:6000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000BEKT-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000c47ed
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 457GiB
                capacity: 457GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-09-10 23:41:07 filesystem=ext4 lastmountpoint=/ modified=2013-09-12 06:48:56 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-10-04 00:13:04 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 8053MiB
                capacity: 8053MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8053MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DV-W28S-VTF
             vendor: TEAC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: M.7B
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:1.4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 7580MiB (7948MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/NIKON D90
                version: FAT32
                serial: [REMOVED]
                size: 7569MiB
                capacity: 7576MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=NIKON D90 mount.fstype=vfat mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: [REMOVED]
       capacity: 75mWh
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: [REMOVED]
       slot: Fake

```

---

### Post by mörgæs on 2013-10-05
So now the network people have something to begin with.
I don't have a solution myself, but let's move it to Networking and see what happens.

---

### Post by Connor_Strandt on 2013-10-05
I guess I should add that if I run
```

sudo service network-manager stop

```
it seems to make it last a little longer before the freeze (though it freezes randomly, but at least once per hour) but like I said in my post above the only difference between home and work is the fact that I am disconnected from wireless at work. At home I can leave it on 24/7 with no freezes or other issues. I also haven't had the time at home to try to shut off my router to see if it happens there as well (but I would assume it would).

---

### Post by Connor_Strandt on 2013-10-05
Ok, after installing wicd and removing network-manager everything seems to be working. Been going at it strong for about an hour now with no freezes. Will update and mark solved after I make it home and verify my wireless will still work there as well.

---

### Post by Connor_Strandt on 2013-10-06
I take my last post back, same problem still exists.

---

### Post by Connor_Strandt on 2013-10-06
I was able to reproduce the issue by turning off wireless through wicd at home (though it took just under 45 mins). If anyone has suggestions they would be greatly appreciated as this is getting very annoying.

---

### Post by mörgæs on 2013-10-06
As I mentioned before I don't have any particular knowledge regarding wireless, but as part of general troubleshooting I would suggest trying 13.10.

---

### Post by Connor_Strandt on 2013-10-06
Just another note my laptop is a L655-S5075 I don't know why I thought it was a S5105 ([http://laptop-infomation-247.blogspot.com/2010/12/toshiba-satellite-l655-s5075.html](http://laptop-infomation-247.blogspot.com/2010/12/toshiba-satellite-l655-s5075.html)) I'm also working on getting 13.10 installed (within the next couple hours, since I'm at work).

---

### Post by Connor_Strandt on 2013-10-07
Ok, after upgrading to 13.04 I left it disconnected all night and it didn't freeze (where it was freezing by disconnecting it and leaving it before). I will take it to work and verify tonight and then update this thread as necessary either tonight or tomorrow.

---

### Post by Connor_Strandt on 2013-10-13
Ok, so now I have 13.04 the issue still happens only when network manager is enabled... If I am quick enough at login to disable network manager I can use the computer all night with no issues. Now I use easytether to connect to the internet but when it connects the computer freezes only to be fixed with a hard reset (just like before). I do most of my web development at work during my down time and would like to be able to manage my local dev sites along with the remote sites so any help on this issue would be greatly appreciated. I still don't feel that network manager should freeze when disconnected like it is but I could be wrong as I haven't had much of a run in with these types of issues before.

---

### Post by Connor_Strandt on 2013-10-14
Well after tinkering with it a little longer tonight I was able to get it working, I got my first "fix" (being able to just use the computer) by disabling network-manager by un-checking "Enable Networking" in the dropdown.

But I was able to successfully stop the freezing while using easytether by doing the following:
```

sudo service network-manager stop
easytether connect

``` and also in another terminal running ```
sudo dhclient easytether0
```
I was successfully able to use the computer and easytether for at least 5 hours with no freezes.

---

### Post by mörgæs on 2013-10-14
Good, if the same approach works for 13.10 do you have time for posting a bug report in Launchpad (including the workaround)?

---

### Post by Connor_Strandt on 2013-10-18
Testing now, haven't had time to test but I put 13.10 on here and am at work so I will test it tonight with the workaround, I already tested without the workaround and had the same result as before.

---

### Post by Connor_Strandt on 2013-10-19
Submitted bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1241920](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1241920)

---

