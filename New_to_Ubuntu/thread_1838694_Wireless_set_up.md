---
title: "Wireless set up"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Brianret on 2011-09-04
[SIZE=3]I have just installed Ubuntu 10.10 alongside my Windows7. With W7 I have a Netgear router which talks to four wall plugs the first plug is connected to my router via a cable and the other three are attached to other equipment such as my Humax HDR etc.
The router was easy to set up via a cd and the wall plugs were a little more difficult but they all work together happily now.
For the past few days I have been trying to set the above system up on Ubuntu but I am finding it difficult to the point of giving up - I am not very technical but I can follow instructions to the letter. Most of the guides on Ubuntu are eye wateringly complicated and my question is, is it possible for someone of my limited ability to set this up or should I leave it to Windows?
[/SIZE]

---

### Post by fdrake on 2011-09-04
try to run those commands in hteterminal: from Appplications> accessories> terminal
```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update
sudo aptitude upgrade
<reboot>
```

if the problem persists run these commands and post here the resuslts

```
sudo lshw -c network
ifconfig
iwconfig
lsmod
nm-tool
rfkill list all

```

---

### Post by Brianret on 2011-09-04
[SIZE=3]Thanks, here is the result

"eth0      Link encap:Ethernet  HWaddr 00:1f:c6:bc:69:d5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:febc:69d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3201069 (3.2 MB)  TX bytes:563384 (563.3 KB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4512 (4.5 KB)  TX bytes:4512 (4.5 KB)

brian@Benbow-PC-Wireless:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

brian@Benbow-PC-Wireless:~$ lsmod
Module                  Size  Used by
snd_hda_codec_analog    80317  1 
binfmt_misc             7984  1 
nvidia              10221014  38 
snd_hda_intel          26147  2 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6804  0 
amd64_edac_mod         24491  0 
parport_pc             30086  1 
snd                    64277  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110           12987  0 
serio_raw               4910  0 
edac_core              46822  3 amd64_edac_mod
edac_mce_amd            9387  1 amd64_edac_mod
k8temp                  4128  0 
i2c_nforce2             6155  0 
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
usbhid                 42030  0 
hid                    84710  1 usbhid
floppy                 65299  0 
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
sata_nv                23770  2 
pata_amd               12050  0 
forcedeth              55649  0 
brian@Benbow-PC-Wireless:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1F:C6:BC:69:D5

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
[/SIZE]

"

---

### Post by fdrake on 2011-09-04
can you post please the results for
```

lshw -c network
rfkill list all

```

---

### Post by Brianret on 2011-09-04
[SIZE=3]" brian@Benbow-PC-Wireless:~$ lshw -c network
WARNING: you should run this program as super-user.
brian@Benbow-PC-Wireless:~$ rfkill list all   "[/SIZE]

---

### Post by fdrake on 2011-09-04
> **Brianret said:**
> [SIZE=3]" brian@Benbow-PC-Wireless:~$ lshw -c network
WARNING: you should run this program as super-user.
brian@Benbow-PC-Wireless:~$ rfkill list all   "[/SIZE]

what about:
```
lspci
lsusb
```

---

### Post by Brianret on 2011-09-04
[SIZE=3]That had a better result -

"brian@Benbow-PC-Wireless:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
brian@Benbow-PC-Wireless:~$ lsusb
Bus 002 Device 003: ID 04ca:0022 Lite-On Technology Corp. 
Bus 002 Device 002: ID 046d:c508 Logitech, Inc. Cordless Trackball
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
brian@Benbow-PC-Wireless:~$ [/SIZE]
   "

---

### Post by fdrake on 2011-09-04
what about 
```

sudo lspci -vvvs 03:00.00
sudo lshw

```

can you tell us model and name of laptop.

---

### Post by Brianret on 2011-09-04
[SIZE=3]OK, Fdrake, I hope that this means more to you than it does to me!
Thanks for your efforts so far.

" brian@Benbow-PC-Wireless:~$ sudo lspci -vvvs 03:00.00
brian@Benbow-PC-Wireless:~$ sudo lshw
benbow-pc-wireless        
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=7CE3D4E9-74FE-D511-BF79-303F782C1B69
  *-core
       description: Motherboard
       product: M2N
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0807 (02/29/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 2800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 33
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:cc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:dbeff000-dbefffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dbefec00-dbefecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:d000(size=4096) memory:dbf00000-dbffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 46
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=32
             resources: irq:19 memory:dbfff800-dbffffff ioport:dc00(size=128)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:dbef8000-dbefbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-disk
             description: ATA Disk
             product: ST3160021A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.06
             serial: 3JS389BT
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ba143
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 307549ff-92a5-4e0c-84b6-c900123a814e
                size: 149GiB
                capacity: 149GiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2011-03-29 23:25:53 filesystem=ext3 modified=2011-09-02 20:27:12 mounted=2011-09-02 19:51:29 state=clean
        *-cdrom
             description: DVD writer
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw dvd dvd-r
             configuration: status=nodisc
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1f:c6:bc:69:d5
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.2 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
          resources: irq:43 memory:dbefd000-dbefdfff ioport:c480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16) memory:dbefc000-dbefcfff
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: CC38
             serial: 5VP4VNB2
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0007b6dc
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: 0e00fe67-3001-244d-a959-99dd93b18c9c
                size: 242GiB
                capacity: 242GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-08-18 05:47:19 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                size: 689GiB
                capacity: 689GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /
                   capacity: 13GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sdb6
                   capacity: 17GiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sdb7
                   capacity: 641GiB
              *-logicalvolume:3
                   description: Linux swap / Solaris partition
                   physical id: 8
                   logical name: /dev/sdb8
                   capacity: 17GiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B1LT
             vendor: ASUS
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:e000(size=4096) memory:dc000000-dfffffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G98 [GeForce 8400 GS]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ec00(size=128) memory:defe0000-deffffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
brian@Benbow-PC-Wireless:~$ [/SIZE]
 "

---

### Post by Brianret on 2011-09-04
[SIZE=3]I also cannot get my VPN network to function[/SIZE]
[SIZE=3]
Brian[/SIZE]

---

