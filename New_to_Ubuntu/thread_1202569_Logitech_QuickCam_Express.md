---
title: "Logitech QuickCam Express"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by ubergunner86 on 2009-07-02
Hello,

I have been trying to get my computer to recognize a Logitech QuickCam Express, its an older model, but it has worked with  Windows (*shudder*) in the past.

It uses USB and my USB ports work fine, as my box recognizes anything else I connect.

Here is an LSHW even when the webcam is plugged in:

patrick-desktop           
    description: Desktop Computer
    product: System Product Name
    vendor: System Manufacter
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-00508DBC0177
  *-core
       description: Motherboard
       product: IP35-E  (Intel P35+ICH9/R)
       vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (01/11/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: Socket 775
          size: 2720MHz
          capacity: 4GHz
          width: 64 bits
          clock: 340MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous external write-back
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
          physical id: 14
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 8192 MHz (0.1 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 3897MHz (0.3ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM Synchronous 8192 MHz (0.1 ns)
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 3897MHz (0.3ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 2040MHz
          capacity: 2040MHz
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
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8800 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
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
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-ide
                description: IDE interface
                product: JMB368 IDE controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm pciexpress msi bus_master cap_list
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 13
                serial: 00:50:8d:bc:01:77
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.108 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IB (ICH9) LPC Interface Controller
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
             product: 82801IB (ICH9) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1L
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BL05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD2500YS-01S
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 20.0
                serial: WD-WCANY3728369
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=33363336
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: d82d3d77-7727-4142-9128-deb0f72d41fd
                   size: 227GiB
                   capacity: 227GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-06-02 18:16:53 filesystem=ext3 modified=2009-07-01 22:27:32 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-06-30 19:23:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   size: 5930MiB
                   capacity: 5930MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5930MiB
                      capabilities: nofs


I am currently running Ubuntu v. 8.04 -- Hardy Heron, have the latest updates, kernal and headers (I believe...).  Any kind of help would be great, thanks.

If this helps I've also tried installing EasyCam2 and it cannot recognize the webcam either.  I'm not sure if I need drivers, need a new webcam or if I'm just missing some kind of repo.  Thanks.

---

### Post by ubergunner86 on 2009-07-02
Oh and this might be of some help too -- apparently, the computer DOES recognize its existence.

patrick@patrick-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0053 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

---

### Post by ubergunner86 on 2009-07-02
SOLVED!!!

[http://linux.softpedia.com/get/Multimedia/Video/LogitechQuickcamexpressdriver-15089.shtml](http://linux.softpedia.com/get/Multimedia/Video/LogitechQuickcamexpressdriver-15089.shtml)

Download and install the driver but you'll also need to install
xawTV   -- which is in synaptic

---

### Post by charonred on 2009-07-06
I have a Quickcam Express too, that worked with Win XP, but doesn't with Hardy.

So I've downloaded the tar.gz file as listed above and extracted it to my own 'tarsrc' folder and have installed xawTV via Synaptic; but now what, I don't have a clue how to compile a driver from the extracted files.

---

### Post by aj_the_first on 2009-07-26
> **ubergunner86 said:**
> SOLVED!!!

[http://linux.softpedia.com/get/Multimedia/Video/LogitechQuickcamexpressdriver-15089.shtml](http://linux.softpedia.com/get/Multimedia/Video/LogitechQuickcamexpressdriver-15089.shtml)

Download and install the driver but you'll also need to install
xawTV   -- which is in synaptic


nope.
I installed xawTV and all its dependencies, and then downloaded the tarball, extracted it, and then with the "make" command, I get this:

aj@Linus:~$ cd /home/aj/qc-usb-0.6.4/
aj@Linus:~/qc-usb-0.6.4$ sudo make install
make -C "/lib/modules/2.6.24-24-generic/build" SUBDIRS="/home/aj/qc-usb-0.6.4" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/aj/qc-usb-0.6.4/.tmp_versions ; rm -f /home/aj/qc-usb-0.6.4/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/aj/qc-usb-0.6.4
  gcc -Wp,-MD,/home/aj/qc-usb-0.6.4/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.2.4/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2  -mtune=generic -m64 -mno-red-zone -mcmodel=kernel -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args   -fstack-protector -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/aj/qc-usb-0.6.4/.tmp_qc-driver.o /home/aj/qc-usb-0.6.4/qc-driver.c
In file included from /home/aj/qc-usb-0.6.4/qc-driver.c:47:
/home/aj/qc-usb-0.6.4/quickcam.h:79:26: error: linux/config.h: No such file or directory
/home/aj/qc-usb-0.6.4/quickcam.h:126:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/aj/qc-usb-0.6.4/quickcam.h:95,
                 from /home/aj/qc-usb-0.6.4/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
In file included from /home/aj/qc-usb-0.6.4/qc-driver.c:47:
/home/aj/qc-usb-0.6.4/quickcam.h:500: error: field ‘vdev’ has incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_i2c_init’:
/home/aj/qc-usb-0.6.4/qc-driver.c:812: error: ‘struct urb’ has no member named ‘lock’
/home/aj/qc-usb-0.6.4/qc-driver.c:813: warning: assignment from incompatible pointer type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_proc_read’:
/home/aj/qc-usb-0.6.4/qc-driver.c:870: error: ‘UTS_RELEASE’ undeclared (first use in this function)
/home/aj/qc-usb-0.6.4/qc-driver.c:870: error: (Each undeclared identifier is reported only once
/home/aj/qc-usb-0.6.4/qc-driver.c:870: error: for each function it appears in.)
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_isoc_start’:
/home/aj/qc-usb-0.6.4/qc-driver.c:1855: warning: assignment from incompatible pointer type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_v4l_poll’:
/home/aj/qc-usb-0.6.4/qc-driver.c:2242: error: implicit declaration of function ‘video_devdata’
/home/aj/qc-usb-0.6.4/qc-driver.c:2242: warning: initialization makes pointer from integer without a cast
/home/aj/qc-usb-0.6.4/qc-driver.c:2244: error: dereferencing pointer to incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_v4l_open’:
/home/aj/qc-usb-0.6.4/qc-driver.c:2294: warning: initialization makes pointer from integer without a cast
/home/aj/qc-usb-0.6.4/qc-driver.c:2296: error: dereferencing pointer to incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_v4l_close’:
/home/aj/qc-usb-0.6.4/qc-driver.c:2362: warning: initialization makes pointer from integer without a cast
/home/aj/qc-usb-0.6.4/qc-driver.c:2364: error: dereferencing pointer to incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_v4l_read’:
/home/aj/qc-usb-0.6.4/qc-driver.c:2409: warning: initialization makes pointer from integer without a cast
/home/aj/qc-usb-0.6.4/qc-driver.c:2412: error: dereferencing pointer to incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_v4l_mmap’:
/home/aj/qc-usb-0.6.4/qc-driver.c:2463: warning: initialization makes pointer from integer without a cast
/home/aj/qc-usb-0.6.4/qc-driver.c:2467: error: dereferencing pointer to incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/aj/qc-usb-0.6.4/qc-driver.c:2496: warning: initialization makes pointer from integer without a cast
/home/aj/qc-usb-0.6.4/qc-driver.c:2499: error: dereferencing pointer to incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c: At top level:
/home/aj/qc-usb-0.6.4/qc-driver.c:2986: warning: initialization from incompatible pointer type
/home/aj/qc-usb-0.6.4/qc-driver.c:2994: error: variable ‘qc_v4l_template’ has initializer but incomplete type
/home/aj/qc-usb-0.6.4/qc-driver.c:2995: error: unknown field ‘name’ specified in initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2995: warning: excess elements in struct initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2995: warning: (near initialization for ‘qc_v4l_template’)
/home/aj/qc-usb-0.6.4/qc-driver.c:2996: error: unknown field ‘type’ specified in initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2996: warning: excess elements in struct initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2996: warning: (near initialization for ‘qc_v4l_template’)
/home/aj/qc-usb-0.6.4/qc-driver.c:2997: error: unknown field ‘hardware’ specified in initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2997: warning: excess elements in struct initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2997: warning: (near initialization for ‘qc_v4l_template’)
/home/aj/qc-usb-0.6.4/qc-driver.c:2998: error: unknown field ‘minor’ specified in initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2998: warning: excess elements in struct initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:2998: warning: (near initialization for ‘qc_v4l_template’)
/home/aj/qc-usb-0.6.4/qc-driver.c:3000: error: unknown field ‘release’ specified in initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:3000: warning: excess elements in struct initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:3000: warning: (near initialization for ‘qc_v4l_template’)
/home/aj/qc-usb-0.6.4/qc-driver.c:3001: error: unknown field ‘fops’ specified in initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:3001: warning: excess elements in struct initializer
/home/aj/qc-usb-0.6.4/qc-driver.c:3001: warning: (near initialization for ‘qc_v4l_template’)
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_usb_init’:
/home/aj/qc-usb-0.6.4/qc-driver.c:3145: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/aj/qc-usb-0.6.4/qc-driver.c:3145: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/aj/qc-usb-0.6.4/qc-driver.c:3147: error: implicit declaration of function ‘video_register_device’
/home/aj/qc-usb-0.6.4/qc-driver.c:3147: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/aj/qc-usb-0.6.4/qc-driver.c:3203: error: implicit declaration of function ‘video_unregister_device’
/home/aj/qc-usb-0.6.4/qc-driver.c: In function ‘qc_usb_probe’:
/home/aj/qc-usb-0.6.4/qc-driver.c:3269: error: ‘UTS_RELEASE’ undeclared (first use in this function)
make[2]: *** [/home/aj/qc-usb-0.6.4/qc-driver.o] Error 1
make[1]: *** [_module_/home/aj/qc-usb-0.6.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make: *** [quickcam.ko] Error 2
aj@Linus:~/qc-usb-0.6.4$ 


any idea what is happening?

---

