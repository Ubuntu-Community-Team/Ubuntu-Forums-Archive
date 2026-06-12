---
title: "Very slow internet connection"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by kenixkil on 2008-07-23
Hi, I switched to ubuntu this week, but the internet connection is driving me insane. I have an optical lan connection, which gives me 5~10 MB/s on windows but when I switch to ubuntu, it slows down a LOT.

When I first installed it, updates were going at like 0.9 KB/s ~ 3 KB/s. I tried disabling ipv6 (both globally and inside firefox), can't use openDNS because I'm on a server, and the only relief came when I updated some code (I think they were on these forums) and I got my speed up to 500KB, but this is very finicky (it oscillates from 0.5 KB ~ 450KB) and still a lot slower than my connection from windows. Also, I tried pinging google, but nothing happened even after several minutes so I quit it. Is there any way to solve this?

Also, in the worst-case scenario, in which it is unsolvable, if I switched to a different distribution (say, Debian or openSuSe) would it make a difference?

---

### Post by hariprs on 2008-07-23
What type of internet connection do you have?

---

### Post by kenixkil on 2008-07-23
Like I said, optic LAN. Like broadband, but a LOT faster :)
(I think an alternative designation is gigabit ethernet)

Except now with ubuntu not letting me take advantage of it...

---

### Post by bab1 on 2008-07-24
Can we assume this is FIOS?  Optical is the physical medium the you are connected with.  Copper gig Ethernet is just as fast as fiber optical gig Ethernet.  The capability of the provider is probably not the limiting factor.  What NIC is in your computer?  Try the following commands from the terminal.

```
lshw
```  and ```
ifconfig -a
```

Send us the results.

Also,  is this a dual boot situation?

---

### Post by kenixkil on 2008-07-24
It is a dual boot situation; I have Windows XP and Kubuntu-turned-ubuntu running.

For the lshw command,

    description: Notebook
    product: EVANS
    vendor: LG Electronics Inc.
    version: Not Applicable
    serial: Not Applicable
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=note
book cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_passw
ord=disabled uuid=0041D847-5964-0010-A312-0A58BD9602FB
  *-core
       description: Motherboard
       product: EVANS
       vendor: LG Electronics
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
       slot: @
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: EVANSF08 (02/05/2007)
          size: 106KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootsel
ect edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: U1
          size: 1GHz
          capacity: 2160MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8
 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht t
m pbe x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 s
sse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
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
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
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
          physical id: b
          slot: System board or motherboard
          size: 2GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
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
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Cont
roller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Expr
ess Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_li
st
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_li
st
                configuration: driver=fglrx_pci latency=0 module=fglrx
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
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_li
st
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: ET-131x PCI-E Ethernet Controller
                vendor: Agere Systems
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:e0:91:20:98:75
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list ethernet phy
sical
                configuration: broadcast=yes driver=et131x ip=192.168.108.33 lat
ency=0 module=et131x multicast=yes
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_li
st
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
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_li
st
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:73:5a:f6
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethe
rnet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl
3945 multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
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
             version: 02
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
             version: 02
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
             version: 02
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
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
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
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 min
gnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 0.2
                bus info: pci@0000:06:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 0.3
                bus info: pci@0000:06:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digit
al Controller
                vendor: Texas Instruments
                physical id: 0.4
                bus info: pci@0000:06:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=57 maxlatency=4 mingnt=7 mod
ule=sdhci
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
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4244N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: SBDO
                serial: SB2D04E4C575BE
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b12ea6c2
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 2af32cff-35ed-8547-9890-67a4748c93a3
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-07-20 03:53:58 f
ilesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true
state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 6698e74d-79a4-40cc-baba-6de7852dfad7
                   size: 3906MiB
                   capacity: 3906MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 36b9cc74-1f77-4c0a-a0f1-83671ad5ba5c
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary journaled extended_attributes large_fil
es huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-22 03:35:24 filesystem=ext3 mo
dified=2008-07-24 13:59:28 mount.fstype=ext3 mount.options=rw,relatime,errors=re
mount-ro,data=ordered mounted=2008-07-24 13:59:28 state=mounted
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: 128b0979-9cf8-4442-a969-88e0adfb10d5
                   size: 50GiB
                   capacity: 50GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-07-20 05:10:46 f                                                           ilesystem=ntfs state=clean
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

and for ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:e0:91:20:98:75
          inet addr:191.167.105.31  Bcast:191.167.105.251  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1078275 (1.0 MB)  TX bytes:156942 (153.2 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:84 (84.0 B)  TX bytes:84 (84.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:73:5a:f6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-73-5A-F6-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by bab1 on 2008-07-24
> *-network
description: Ethernet interface
product: ET-131x PCI-E Ethernet Controller
vendor: Agere Systems
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:e0:91:20:98:75
width: 64 bits
clock: 33MHz

I see the ethernet card.  What about it's config?

---

### Post by kenixkil on 2008-07-24
If that's the ifconfig information, it's listed at the bottom...

If not, how do I get it?

---

### Post by bab1 on 2008-07-24
I missed it, sorry.  :-(
> eth0 Link encap:Ethernet HWaddr 00:e0:91:20:98:75
inet addr:191.167.105.31 Bcast:191.167.105.251 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST [COLOR="Green"]MTU:1500[/COLOR] Metric:1
[COLOR="Magenta"]RX packets:1703 errors:0 dropped:0 overruns:0 frame:0
TX packets:985 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000[/COLOR]
RX bytes:1078275 (1.0 MB) TX bytes:156942 (153.2 KB)
Interrupt:16

The config looks fine.  I'll bet it is in the implementation of the gig Ethernet in Linux.  There are no errors or malformed packets. (see colored text)  

Pinging someone does not always work.  That feature (ICMP) can be turned off.  Ping your own ISP.

I would see if this is a known bug.

---

### Post by bab1 on 2008-07-24
There is a bug listing for this nic.  See:[[COLOR="Red"]Here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/102291")
I think it's for a new driver

---

### Post by kenixkil on 2008-07-24
I installed the driver, but I'm not sure whether or not the system is using the new driver or not.

I don't, unfortunately, notice any significant speed changes (Konqueror still runs at 20KB).

---

### Post by bab1 on 2008-07-24
I am not familier with your gig ethernet chipset.  I still believe your proplem is driiver reated.

---

