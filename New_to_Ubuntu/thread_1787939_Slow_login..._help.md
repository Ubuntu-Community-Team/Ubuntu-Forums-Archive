---
title: "Slow login... help"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by eb3ha4el on 2011-06-21
Every booting process seems to work well untill
the login page. Problem is it takes fairly long to load up desktop after I type in username and password.

It wasn't like this before when I was using Ubuntu. 
(Now I have re-installed lubuntu. Unlike when I used Ubuntu, this time I added swap space)


here is output of dmesg.


```
[   18.019310] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.020429] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.244333] ppdev: user-space parallel port driver
[   47.006786] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   61.359417] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[   61.362820] wlan0: authenticated
```


login is also slow when I login from screen saver. 

Any idea?
thanks

---

### Post by wildmanne39 on 2011-06-22
> **eb3ha4el said:**
> Every booting process seems to work well untill
the login page. Problem is it takes fairly long to load up desktop after I type in username and password.

It wasn't like this before when I was using Ubuntu. 
(Now I have re-installed lubuntu. Also unlike Ubuntu, this time I added swap space)


here is output of dmesg.


```
[   18.019310] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.020429] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.244333] ppdev: user-space parallel port driver
[   47.006786] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   61.359417] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[   61.362820] wlan0: authenticated
```


login is also slow when I login from screen saver. 

Any idea?
thanksHi, what are your system specs? are you using the cube or desktop effects, type the command in a termianal
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by eb3ha4el on 2011-06-22
What do you mean by cube and desktop effect?


I'm using Netbook.
detailed specifications is of following (lshw command)


```

toshiba-nb200-s           
    description: Notebook
    version: PLL23K-003004
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 family=ABCDEFGHIJKLMNOPQRSTUVWXYZ sku=012345678912345678912345678 uuid=848BAB01-A896-11DE-B5B9-0026223C73DA
  *-core
       description: Motherboard
       product: KAVAA
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.70
          date: 09/30/2009
          size: 99KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N280   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: U2E1
          size: 1GHz
          capacity: 2048MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             physical id: 1
             slot: M2
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f007ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:f0200000-f023ffff
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
             resources: memory:f0080000-f00fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:f0440000-f0443fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:f0100000-f01fffff ioport:40400000(size=2097152)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:23:08:cc:5f:bd
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=10.32.133.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0100000-f010ffff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:40600000-409fffff ioport:f0500000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:26:22:3c:73:da
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:44 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:40a00000-40bfffff ioport:40c00000(size=2097152)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0444000-f04443ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:18c8(size=8) ioport:18c0(size=4) ioport:18a8(size=8) ioport:180c(size=4) ioport:18b0(size=16) memory:f0444400-f04447ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK2555GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: FG00
                serial: 89CBFD1JS
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9a851e14
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 54c9-3c90
                   size: 1498MiB
                   capacity: 1500MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-06-12 18:18:45 filesystem=ntfs label=System state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 7e0a5a80-db6c-174b-bb68-5f787ae1e260
                   size: 99GiB
                   capacity: 100GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-06-12 18:20:02 filesystem=ntfs label=Windows state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 7065-aeaf
                   size: 5916MiB
                   capacity: 5924MiB
                   capabilities: primary hidden ntfs initialized
                   configuration: clustersize=4096 created=2009-10-03 00:30:57 filesystem=ntfs label=HDDRECOVERY state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 125GiB
                   capacity: 125GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 976MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 124GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
  *-battery
       description: Lithium Ion Battery
       product: PA3395U
       vendor: TOSHIBA
       physical id: 1
       version: 12/01/2005
       serial: 3658Q
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V

```



thanks for help.

---

### Post by wildmanne39 on 2011-06-22
Hi which version of lubuntu are you using? which version of ubuntu were you using? Well at first look your processor is not very strong but if you were running natty then you should have better results with lubuntu, you need to look through you logs to see if you can find anything at login that is slowing you down, open log viewer to see your logs.

---

### Post by eb3ha4el on 2011-06-22
> **wildmanne39 said:**
> Hi which version of lubuntu are you using? which version of ubuntu were you using? Well at first look your processor is not very strong but if you were running natty then you should have better results with lubuntu, you need to look through you logs to see if you can find anything at login that is slowing you down, open log viewer to see your logs.



Both Lubuntu and ubuntu I used the latest: 11.04 Natty.

How do I see my logs? and what log do you mean?
I'm newbie and am confused. Is dmesg not a kind of log as well?

---

### Post by wildmanne39 on 2011-06-23
Hi, like I said on log file viewer, I do not know if it is installed by default on lubuntu, you will have to look in your menu
for it. open it and start at the top of the page and see what xorg says,Authority log, boot log,bootstrap logs this one is interesting,dmesg,kernel and system logs.

---

### Post by eb3ha4el on 2011-06-23
ca> **wildmanne39 said:**
> Hi, like I said on log file viewer, I do not know if it is installed by default on lubuntu, you will have to look in your menu
for it. open it and start at the top of the page and see what xorg says,Authority log, boot log,bootstrap logs this one is interesting,dmesg,kernel and system logs.


Hi there.
I assume "log file viewer" is not the name of package, and i think it is not installed on my system. Can you tell me name of particular software for viewing log file? so that I can install it from SPM?

---

### Post by wildmanne39 on 2011-06-23
> **eb3ha4el said:**
> ca


Hi there.
I assume "log file viewer" is not the name of package, and i think it is not installed on my system. Can you tell me name of particular software for viewing log file? so that I can install it from SPM?Hi, in ubuntu it is called gnome system log viewer, just type in log and start looking for the package. I have never used lubuntu. You can also do it from the command line. Ok, open your file manager go to var, then log and click on it and you can see all your logs, at least it works on ubuntu.

---

### Post by dFlyer on 2011-06-23
You can also check your logs for the command line by going cd /var/log from a terminal.

---

### Post by crispy_420 on 2011-06-23
Try putting mem=1000M in boot options with grub. I have an odd laptop that performed horribly until this boot option is set. Try adding at boot temporary before adding as a permanent option.

Here's link to a similar type topic:

[http://ubuntuforums.org/showthread.php?t=1666847](http://ubuntuforums.org/showthread.php?t=1666847)

---

### Post by eb3ha4el on 2011-06-25
It booted more slowly today.
dmesg says: (selection)

```
[    4.077501] Btrfs loaded
[    4.093508] xor: automatically using best checksumming function: pIII_sse
[    4.112024]    pIII_sse  :  5053.000 MB/sec
[    4.112035] xor: using function: pIII_sse (5053.000 MB/sec)
[    4.120255] device-mapper: dm-raid45: initialized v0.2594b
[    4.744529] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   61.345573] Adding 999420k swap on /dev/sda5.  Priority:-1 extents:1 across:999420k 
[   61.426016] <30>udev[322]: starting version 167
[   61.498766] lp: driver loaded but no devices found
[   61.555862] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro


[   66.022058] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   66.022122] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   66.121020] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   66.122034] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   66.346943] ppdev: user-space parallel port driver
[   97.636274] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[  107.227863] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[  107.229976] wlan0: authenticated
```


I still think the problem is from adding swap.
When I used Ubuntu, I had sda 1~4. 
sda 1~3 was used for Windows itself, system, and window recovery disk.
and whole sda4 was used for Ubuntu. 
but I divided this sda4 section and created a logical partition for swap and rest (sda6) for Lubuntu. no relevance to the problem?

I tried to have a look at other logs.. but I'm just really newbie.. can't understand anything..:(
Shall I put all up here?



Second reboot dmesg:

```
[   15.365129] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   15.368778] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.503429] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.592301] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.592982] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.796334] ppdev: user-space parallel port driver
[   40.244543] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   45.804691] wlan0: authenticate with 00:26:5a:92:c1:8e (try 1)
[   45.806801] wlan0: authenticated
```

---

