---
title: "Network device changes on reboot"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by svenbertil on 2007-09-06
Long time lurker, first time poster :)

Here goes.

I'm setting up a computer that will act as a router (among other things). It has two network cards, one Realtek 8139 and one 3com 3c905B. The Realtek card is always eth0 so thats fine. The 3com however changes between eth1 to eth2 on reboot.

So I edit /etc/network/interfaces and change it to eth2. On the next reboot the network card has changed to eth1, so I edit the interfaces-file again, it works, I reboot, and now it has changed back to eth2 yet again.

The box is running a somewhat clean installation of ubuntu server 7.04 and I'd prefer not to clutter it up with gnome or KDE so if someone knows how to fix this using only command line, I'd be grateful.

lspci: (the one in bold is the troublesome one)
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**02:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)**
```

lsmod:
```

Module                  Size  Used by
ipt_LOG                 7680  6 
xt_tcpudp               4224  8 
ipt_MASQUERADE          4608  1 
xt_state                3456  8 
iptable_nat             8580  1 
nf_nat                 19372  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19468  10 iptable_nat
nf_conntrack           62728  5 ipt_MASQUERADE,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               7576  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_filter          3968  1 
ip_tables              13796  2 iptable_nat,iptable_filter
x_tables               16388  6 ipt_LOG,xt_tcpudp,ipt_MASQUERADE,xt_state,iptable_nat,ip_tables
lp                     12324  0 
snd_intel8x0           34332  0 
snd_ac97_codec         97952  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44416  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52464  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
analog                 12832  0 
gameport               16520  1 analog
snd_timer              23684  2 snd_pcm,snd_seq
snd_mpu401              9384  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
parport_pc             36644  1 
parport                36808  2 lp,parport_pc
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    53892  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               8672  1 snd
psmouse                38920  0 
snd_page_alloc         11016  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
serio_raw               7940  0 
intel_agp              25244  1 
agpgart                35528  1 intel_agp
shpchp                 34452  0 
pci_hotplug            32448  1 shpchp
ipv6                  273344  22 
tsdev                   8768  0 
evdev                  11008  1 
ext3                  132872  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23300  7 
sg                     35996  0 
sr_mod                 17060  0 
cdrom                  37536  1 sr_mod
8139too                27648  0 
floppy                 59396  0 
3c59x                  46760  0 
uhci_hcd               25488  0 
8139cp                 25216  0 
mii                     6656  3 8139too,3c59x,8139cp
usbcore               134408  2 uhci_hcd
ata_piix               15620  5 
ata_generic             9092  0 
libata                125848  2 ata_piix,ata_generic
scsi_mod              142220  4 sd_mod,sg,sr_mod,libata
generic                 5124  0 [permanent]
raid1                  25472  1 
md_mod                 79764  3 raid1
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


```

lshw:
```
testrouter
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: PLATINIX-4
       vendor: Legend QDI
       physical id: 0
       version: V1.XX
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (06/29/2001)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1600MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.0.10
          slot: Socket 423
          size: 1600MHz
          capacity: 2GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KB
             capacity: 16KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 256KB
     *-cache
          description: L2 cache
          physical id: b
          slot: External Cache
          size: 256KB
          capacity: 256KB
          capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 1d
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM Fast-paged CMOS 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 256MB
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM Fast-paged CMOS 400 MHz (2.5 ns)
             physical id: 1
             slot: A1
             size: 256MB
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM Fast-paged CMOS 400 MHz (2.5 ns) [empty]
             physical id: 2
             slot: A2
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM Fast-paged CMOS 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: A3
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82850 850 (Tehama) Chipset Host Bridge (MCH)
          vendor: Intel Corporation
          physical id: d8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: 82850 850 (Tehama) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
                resources: iomemory:dc000000-dcffffff iomemory:d0000000-d7ffffff irq:9
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: a
                bus info: pci@02:0a.0
                logical name: eth0
                version: 10
                serial: 00:00:e8:53:3b:84
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.64.20.248 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:c000-c07f iomemory:df001000-df00107f irq:5
           *-network:1
                description: Ethernet interface
                product: 3c905B 100BaseTX [Cyclone]
                vendor: 3Com Corporation
                physical id: b
                bus info: pci@02:0b.0
                logical name: eth2
                version: 30
                serial: 00:10:5a:84:79:7f
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
                resources: ioport:c400-c47f iomemory:df000000-df00007f irq:11
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f000-f00f
           *-disk:0
                description: SCSI Disk
                product: Maxtor 2B020H1
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: WAH2
                serial: B1A0KHHE
                size: 19GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 16GB
                   capabilities: primary bootable multi
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 478MB
                   capabilities: primary nofs
           *-disk:1
                description: SCSI Disk
                product: HDS728080PLAT20
                vendor: ATA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: PF2O
                serial: PFD215S6RYD9LM
                size: 76GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 16GB
                   capabilities: primary bootable multi
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   capacity: 478MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   capacity: 59GB
                   capabilities: primary
           *-cdrom
                description: DVD reader
                product: DVD-ROM DVD-116
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.22
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d000-d01f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-server uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d400-d41f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-server uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc00-dc3f irq:11

```

ifconfig -a at one moment:
```
eth0      Link encap:Ethernet  HWaddr 00:00:E8:53:3B:84  
          inet addr:10.64.20.248  Bcast:10.64.20.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe53:3b84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1861257 (1.7 MiB)  TX bytes:396893 (387.5 KiB)
          Interrupt:5 Base address:0x2000 

eth2      Link encap:Ethernet  HWaddr 00:10:5A:84:79:7F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

ifconfig -a after next reboot:```

eth0      Link encap:Ethernet  HWaddr 00:00:E8:53:3B:84  
          inet addr:10.64.20.248  Bcast:10.64.20.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe53:3b84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7452 (7.2 KiB)  TX bytes:7209 (7.0 KiB)
          Interrupt:5 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:10:5A:84:79:7F  
          inet addr:192.168.51.1  Bcast:192.168.51.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

If I leave /etc/network/interfaces unchanged it will work upon next reboot but not the reboot after that. Is there some way of forcing that specific NIC to always be eth1?

---

### Post by noob12 on 2007-09-06
You need to edit **/etc/iftab**.  Add/replace the entry for eth1 and replace the mac address with the one for the card that is flipping.  Read **man iftab** for details, or post if you have questions.
The line you add or replace should look like this after you are done.
```

eth1 mac 00:10:5a:84:79:7f arp 1

```

---

### Post by svenbertil on 2007-09-06
That worked like a charm! thank you!

---

