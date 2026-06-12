---
title: "Ethernet not working"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by alex240 on 2014-08-17
(I'm a newbie to Ubuntu, please help and explain)  
A few weeks ago, I built my first ever computer and put Ubuntu on it. It was fine for a few days but when I went on vacation I shut it off and when I came back Ubuntu was not installed and I had to install it again, and again it was OK. But the Ethernet constantly says "connecting" but does not connect and gives me an error message like "network disconnected" and repeats he cycle, please try and help.

---

### Post by coldraven on 2014-08-18
To start solving your problem some information is needed. Copy and paste the following in a terminal and post back the result.
```
sudo lshw -class network
```

What I usually do on a new machine is to get a listing of all the hardware into a text file so that I can easily search it. If you run the following command it will create a text file called hardware.txt. in your home folder. Then if you double click the file Gedit will open it and you can search through it for your system information.
```
sudo lshw > hardware.txt
```

---

### Post by alex240 on 2014-08-18
> **coldraven said:**
> To start solving your problem some information is needed. Copy and paste the following in a terminal and post back the result.
```
sudo lshw -class network
```

What I usually do on a new machine is to get a listing of all the hardware into a text file so that I can easily search it. If you run the following command it will create a text file called hardware.txt. in your home folder. Then if you double click the file Gedit will open it and you can search through it for your system information.
```
sudo lshw > hardware.txt
```

For the first line of code, it says:
```

*-network
Description: Ethernet interface
Product: RTL8111/8168/8411 PCI Express Gigabit Ethernet controller
Vendor: Realtek semiconductor Co., Ltd.
Physical I'd: 0
Bus info: pci@0000:03:00.0
Logical name: eth0
Version: 06
Serial: 74:d4:35:9b:84:a1
Size: 100Mbit/s
Capacity: 1Gbit/s 
Width: 64 bits
Clock: 33Mhz
Capabilities: pm MSI pciexpress msix vpd bus_master cap_list Ethernet physical to mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                Configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 IP=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                Resources: irq: 73 ioport:d000(size=256) memory:fe800000-fe800fff memory: d0000000-d0003fff

```

---

### Post by alex240 on 2014-08-18
> **coldraven said:**
> To start solving your problem some information is needed. Copy and paste the following in a terminal and post back the result.
```
sudo lshw -class network
```

What I usually do on a new machine is to get a listing of all the hardware into a text file so that I can easily search it. If you run the following command it will create a text file called hardware.txt. in your home folder. Then if you double click the file Gedit will open it and you can search through it for your system information.
```
sudo lshw > hardware.txt
```

Anyway, here is the hardware.txt file code just in case.
```

zipeto-computer    description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 ldt16 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=7402D403-3504-9B05-8406-A10700080009
  *-core
       description: Motherboard
       product: 970A-D3P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F5
          date: 08/06/2013
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD FX(tm)-6300 Six-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-6300 Six-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1400MHz
          capacity: 3500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
          configuration: cores=6 enabledcores=6 threads=6
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 288KiB
             capacity: 288KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 6MiB
             capacity: 6MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Dimm0_PartNum
             vendor: Dimm0_Manufacturer
             physical id: 0
             serial: Dimm0_SerNum
             slot: Node0_Dimm0
        *-bank:1
             description: DIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: F3-2133C9-4GX
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: Node0_Dimm1
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Dimm2_PartNum
             vendor: Dimm2_Manufacturer
             physical id: 2
             serial: Dimm2_SerNum
             slot: Node0_Dimm2
        *-bank:3
             description: DIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: F3-2133C9-4GX
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: Node0_Dimm3
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 ioport:e000(size=4096) memory:fea00000-feafffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:74 memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:fea40000-fea5ffff
           *-multimedia
                description: Audio device
                product: Tahiti XT HDMI Audio [Radeon HD 7970 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:75 memory:fea60000-fea63fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 memory:fe900000-fe9fffff
           *-usb
                description: USB controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:72 memory:fe900000-fe900fff
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port H)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:53 ioport:d000(size=4096) memory:fe800000-fe8fffff ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 74:d4:35:9b:84:a1
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:73 ioport:d000(size=256) memory:fe800000-fe800fff memory:d0000000-d0003fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0b000-feb0b3ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb0a000-feb0afff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb09000-feb090ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb08000-feb08fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb07000-feb070ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb06000-feb06fff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000DM003-1ER1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: CC43
             serial: Z4Y0QF1P
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0008d102
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: fbd8642b-b790-42a9-b930-5be1628bdab5
                size: 923GiB
                capacity: 923GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-08-17 10:54:01 filesystem=ext4 lastmountpoint=/ modified=2014-08-17 21:05:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-08-17 21:05:25 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 8155MiB
                capacity: 8155MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8155MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-H653L
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 0414
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```

---

### Post by coldraven on 2014-08-18
I'm not a Networking expert so I hope that someone with more knowledge will join in. Also we are probably in different time zones so your PM arrived when I was asleep.
Anyway, a bit of searching found this from here:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting)


> **Doing Basic Cable and Link Tests**

 Your server won't be able to communicate with any other device on  your network unless the NIC's "link" light is on. This indicates that  the connection between your server and the switch/router is functioning  correctly. 
In most cases a lack of link is due to the wrong cable type being used. As described in Chapter 2, "[Introduction to Networking]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking")", there are two types of Ethernet cables crossover and straight-through. Always make sure you are using the correct type. 
Other sources of link failure include: 
 
[LIST]
[*] The cables are bad. 
[*] The switch or router to which the server is connected is powered down. 
[*] The cables aren't plugged in properly. 
[/LIST]


So is the little green light on the network socket on or not?

The next thing would be to run the command ifconfig and post back the result
```
ifconfig
```

---

### Post by alex240 on 2014-08-18
> **coldraven said:**
> I'm not a Networking expert so I hope that someone with more knowledge will join in. Also we are probably in different time zones so your PM arrived when I was asleep.
Anyway, a bit of searching found this from here:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting)




So is the little green light on the network socket on or not?

The next thing would be to run the command ifconfig and post back the result
```
ifconfig
```

Yes, the green light on my router is on, as well as on my pc, along with a blinking yellow light.
I tried a Wi-fi card and the wi-fi is recognized but does not connect.
And also, at times, it says that ethernet is connected and i get the 2 little arrows on top, but the internet (firefox browser) still does not work.:mad:
The "ifconfig" line of code brings up the following:

```

eth0      Link encap:Ethernet  HWaddr 74:d4:35:9b:84:a1            inet6 addr: fe80::76d4:35ff:fe9b:84a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:2867 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1014563 (1.0 MB)  TX bytes:7553 (7.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:254191 (254.1 KB)  TX bytes:254191 (254.1 KB)


wlan0     Link encap:Ethernet  HWaddr 00:18:f8:2b:19:eb  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fe2b:19eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1994 (1.9 KB)  TX bytes:85751 (85.7 KB)



```

---

### Post by coldraven on 2014-08-19
```
eth0      Link encap:Ethernet  HWaddr 74:d4:35:9b:84:a1            inet6 addr: fe80::76d4:35ff:fe9b:84a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:2867 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1014563 (1.0 MB)  TX bytes:7553 (7.5 KB)
```

It looks like you are not getting an IP address from your router. Was your router working before? 
Have you tried looking at the router settings? Do you have another device that successfully connects with it? 
(Presumably you can, because you can post here)
I access my router at this address in a browser [http://192.168.2.1/](http://192.168.2.1/)
Then in the "Interface Setup" section I can see that the DHCP server is enabled (this creates IP addresses for connected devices)
Then if I click on "Current pool summary" it shows me that I have a laptop and and an android phone connected and their MAC and IP address.
Your router will be slightly different but the same info should be viewable somewhere.

You say that it works occasionally, try changing the network cable, it could be faulty.

---

### Post by alex240 on 2014-08-19
> **coldraven said:**
> ```
eth0      Link encap:Ethernet  HWaddr 74:d4:35:9b:84:a1            inet6 addr: fe80::76d4:35ff:fe9b:84a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:2867 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1014563 (1.0 MB)  TX bytes:7553 (7.5 KB)
```

It looks like you are not getting an IP address from your router. Was your router working before? 
Have you tried looking at the router settings? Do you have another device that successfully connects with it? 
(Presumably you can, because you can post here)
I access my router at this address in a browser [http://192.168.2.1/](http://192.168.2.1/)
Then in the "Interface Setup" section I can see that the DHCP server is enabled (this creates IP addresses for connected devices)
Then if I click on "Current pool summary" it shows me that I have a laptop and and an android phone connected and their MAC and IP address.
Your router will be slightly different but the same info should be viewable somewhere.

You say that it works occasionally, try changing the network cable, it could be faulty.

I have all of that information now, I just don't know what to do with it now.

---

### Post by varunendra on 2014-08-19
> **alex240 said:**
> ```
                Configuration: autonegotiation=on .... **[COLOR="#0000FF"]IP=192.168.1.15[/COLOR] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s**
```
Everything in that lshw output looks pretty solid to me. But in the later post, you didn't have an IP on eth0 like coldraven pointed out. Assuming you didn't disconnect the cable, I strongly suspect it to be a case of bad/loose cable/connector. Try replacing it with a working/tested one.

---

### Post by alex240 on 2014-08-19
> **varunendra said:**
> Everything in that lshw output looks pretty solid to me. But in the later post, you didn't have an IP on eth0 like coldraven pointed out. Assuming you didn't disconnect the cable, I strongly suspect it to be a case of bad/loose cable/connector. Try replacing it with a working/tested one.

My internet works fine when I booted up with windows.

---

### Post by varunendra on 2014-08-19
When the output of "lshw -C network" shows those parts I quoted above (has an IP, and speed=100 Mbps), then the output of "ifconfig" should also show the same IP address. Does it (the IP) appear and disappear automatically?

How does the Ethernet get its IP address in Ubuntu? You have manually configured it or is it automatically received via DHCP? If manual, is it the same as in Windows?

In Windows, you can see the IP address (and other related details) with "ipconfig" command.

The behaviour you describe (getting connected, then disconnected automatically) is indicative of either a bad cable/contact, or an IP conflict with some other device on the network. But IP conflict shouldn't occur if all the devices are receiving their IP via DHCP, or manually assigned ones have IP's outside DHCP range (and not mutually conflicting with others).

---

