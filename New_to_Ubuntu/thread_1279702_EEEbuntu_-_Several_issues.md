---
title: "EEEbuntu - Several issues"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by Kakakaun on 2009-10-01
Hi there. I just started using eeebuntu Standard 3.0 Latest edition on my ASUS N10J.
Since I cannot create an user account on eeebuntu forums I came here with my problems:

1. Whenever I boot, appearance looks like clearlooks, although I want EB3.
I have no idea how to solve this.
[[IMG]http://lookpic.com/t/472/GMBFPAwU.png[/IMG]]("http://lookpic.com/i/472/GMBFPAwU.png")

2. The resolution starts in 800x600 and I have to put it in 1024x600 every time. When I try to save the x-config file it says it cannot be saved.
[[IMG]http://lookpic.com/t/794/XfgiFdsi.png[/IMG]]("http://lookpic.com/i/794/XfgiFdsi.png")


3. After 20 minutes or so NetworkManager Applet 0.7.0.100 disappears and FF goes into offline mode.
[[IMG]http://lookpic.com/t/514/zqABOI0g.png[/IMG]]("http://lookpic.com/i/514/zqABOI0g.png")

(The green Wifi Icond thingey)

If you need any other information just let me know and I will provide.
> netbook                   
    description: Notebook
    product: N10Jc
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: NF1S8A65060053
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: chassis=notebook cpus=1 uuid=0059824A-58A7-DD81-29C9-002354729B03
  *-core
       description: Motherboard
       product: N10Jc
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 207 (09/09/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm lahf_lm cpufreq
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
             physical id: 7
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
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
     *-cache
          description: L1 cache
          physical id: 6
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
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
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 02
                serial: 00:23:54:72:9b:03
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
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
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:43:32:cd:45
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.68 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
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
           *-display
                description: VGA compatible controller
                product: GeForce 9300M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
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
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST9160310AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0303
                serial: 5SV1QL4G
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6a6b537a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4ac26a4c-c5d4-43f3-b042-2f70f4d9a3ee
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-09-27 09:30:31 filesystem=ext3 modified=2009-10-01 17:57:52 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-10-01 17:15:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5891MiB
                   capacity: 5891MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5890MiB
                      capabilities: nofs
     *-scsi
          physical id: 1
          bus info: usb@5:7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:8c:51:cb:5e:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



 And thanks for any trouble in advance!

I wish I could register on eeebuntuforums, not only to whine about my problems but also to thank you guys for all your hard work. My boot time of just seconds. And 'freeing' me off windows. I will spread the word!

---

### Post by anaconda on 2009-10-01
2. Start nvidia-settings with:
```
sudo nvidia-settings
```
and it should be able to save the config-file.

3. I solved my (many) problems with networkmanager by uninstalling it!  
And replacing it with WiCd  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I also use Gnome-ppp, when I want to make a 3G-connection.
If networkmanager isn't isntalled then programs like firefox wont even try to ask from it if there is a network connection, and so firefox will newer start in offline mode.
Also I think wicd is better than nm when connecting to wireless networks.

---

### Post by Cato2 on 2009-10-01
You might need to do gksudo nvidia-settings, not just sudo.

---

### Post by Kakakaun on 2009-10-01
> **anaconda said:**
> 2. Start nvidia-settings with:
```
sudo nvidia-settings
```and it should be able to save the config-file.

3. I solved my (many) problems with networkmanager by uninstalling it!  
And replacing it with WiCd  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I also use Gnome-ppp, when I want to make a 3G-connection.
If networkmanager isn't isntalled then programs like firefox wont even try to ask from it if there is a network connection, and so firefox will newer start in offline mode.
Also I think wicd is better than nm when connecting to wireless networks.

Thank you very much!
2. Worked out for me, durr just sudo :-) Itl probably work out when I reboot, but ill try it later.
3. Well the network manager just disapears on me..
It has not happend for a while now...
Because WiFi was working out off the box, and if I uninstall it im afraid I might have to fumble with the settings. And im in a pretty remote area right now, so I only have one computer..
So maybe you have any other suggestions? :3

---

### Post by Kakakaun on 2009-10-03
Thanks Cato2, cheers for the input.

---

### Post by Paqman on 2009-10-03
If you create a new user account on your machine and try logging in/out a few times, do you still get the same problems with themes and settings? Do you know if you've got your /home folder mounted in a different location to your root? Have you messed about with permissions on your /home, or with user accounts?

---

### Post by Kakakaun on 2009-10-03
Well what now happens, I boot up, it starts in the right resolution. Wrong interface. I change the appearance to EB3 and then the resolutions faults..
And as far as I know everything is fine, I haven't even try'd ******* with anything because I would probably break it..

---

