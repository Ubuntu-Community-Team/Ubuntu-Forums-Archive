---
title: "Video Problems - NV6 [Vanta/Vanta LT]"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by ubergunner86 on 2009-01-27
Hello everyone!

I have installed an older NV6 [Vanta/Vanta LT] video card into a Dell Optiplex GX260 because the integrated card doesn't work well either(which is a  82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge).  This card has been running and I can even run higher resolutions, its just that the picture quality is really fuzzy and I cannot enable desktop effects or use compiz/beryl.  I have tried using different resolutions as well as different refresh rates (60,75hz).  The monitor I am currently using is a Dell 1702FP and it works fine on other machines.  Here is my lshw and a copy of my xorg.conf file:

LSHW:

commstudent-41pr-desktop  
    description: Mini Tower Computer
    product: OptiPlex GX260
    vendor: Dell Computer Corporation
    serial: F9HSS11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-3900-1048-8053-C6C04F533131
  *-core
       description: Motherboard
       product: OptiPlex GX260
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A02 (07/25/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns) [empty]
             physical id: 1
             slot: DIMM_B
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV6 [Vanta/Vanta LT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 02
                serial: 00:08:74:26:a3:f5
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A ip=172.19.61.8 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: WDC WD400BB-75DE
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAD11864246
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d561d561
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: ccb2f6c5-e667-489a-ae4d-11ff772f42de
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-26 13:05:29 filesystem=ext3 modified=2009-01-27 11:05:32 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-01-27 11:05:32 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 729MiB
                   capacity: 729MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 729MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: APL.
                serial: 652102180331
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cc37cc37
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: e460179e-1b5c-3545-be9a-3d3dd60217dd
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2004-09-27 10:18:49 filesystem=ntfs state=clean
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW NR-9100A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 108A
                serial: [_NEC    CD-RW NR-9100A  108A02040500
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:07:d5:15:6e:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I have not been able to find/compile any drivers for this video card and it does not show up on restricted drivers.  

In addition, I tried using EnvyNG and there WAS a compatible/recommended driver, but when I installed it it bricked my box and I had to reformat.
Any help would be greatly appreciated.  Thank you.

---

### Post by sandyd on 2009-01-27
did you install KDE before, or after installing and running envyng?

for me, if i install kde before running envyng, it kills my box too. 

i have to install envyng (and run it) before installing kde for it not to kill my box

---

### Post by ubergunner86 on 2009-01-27
> **carlee said:**
> did you install KDE before, or after installing and running envyng?

for me, if i install kde before running envyng, it kills my box too. 

i have to install envyng (and run it) before installing kde for it not to kill my box


I actually wasn't even aware that Envy was only for KDE.

So the answer to that would be no.. I did not install KDE beforehand.

That is the 'lshw' and 'xorg.conf' from a freshly reformatted box.

The xorg.conf file seems to be kind of blank... I don't even think that I have a driver at all for the card at the moment.  Nothing came up on Restricted Drivers and I did not try to install any drivers because I couldn't find the right one yet.

---

### Post by SOULRiDER on 2009-01-27
What driver did you install? If you didnt install one manually you will have to use the 'nv' driver. If you want the nVidia driver you will have to install the legacy driver, but im not sure that driver supports cards as old as that one.

---

### Post by sandyd on 2009-01-28
try installing the drivers from nvidia themselves (they have their own drivers too)

make sure youve remove envyng before you do that or your ubuntu will have two drivers with the same name (which won't be good)

then add this line(s) to xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

```

---

### Post by gigaferz on 2009-01-29
let me know if this works 4 u, this card used to work with previous ubuntu versions, i installed intrepid and its not working either, You can run the screens and resolutions program but its kinda hidden in the latest ubuntus, I did it and there was a performance impact.

hope to hear from you.

---

### Post by ubergunner86 on 2009-01-29
> **SOULRiDER said:**
> What driver did you install? If you didnt install one manually you will have to use the 'nv' driver. If you want the nVidia driver you will have to install the legacy driver, but im not sure that driver supports cards as old as that one.

Well.. I tried installing the driver and I got this message:
(and I know I did the install correctly because I read the instructions off of the nvidia website and this thread: [http://ubuntuforums.org/showthread.php?t=34479](http://ubuntuforums.org/showthread.php?t=34479))

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jan 29 12:09:14 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 71.86.06.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-11-gener
   ic/build SYSOUT=/lib/modules/2.6.27-11-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-11-generic/build SUBDIRS
   =/tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -i
   nclude include/linux/autoconf.h
    -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-str
   ict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march
   =i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronou
   s-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mac
   h-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling
   -calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz6197
   /NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -W
   switch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multich
   ar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAME
   S -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNE
   L__ -DMODULE -DNV_VERSION_STRING=\"71.86.06\" -DNV_UNIX -DNV_LINUX -DNV_INT6
   4_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nv)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6197/NVIDIA-Linux-x86-71
   .86.06-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-p
   kg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1975: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:83,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:104:27:
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv-linux.h:106,
                    from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h: In fun
   ction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv-linux.h:595: er
   ror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   ‘__nv_setup_pat_entries’:
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:887: warning:
   comparison between signed and unsigned
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   ‘__nv_restore_pat_entries’:
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:913: warning:
   comparison between signed and unsigned
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c: In function 
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1239: warning
   : comparison between signed and unsigned
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1242: error: 
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1246: warning
   : comparison between signed and unsigned
   /tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.c:1249: error: 
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz6197/NVIDIA-Linux-x86-71.86.06-pkg1/usr/src
   /nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


If anyone could help with this problem, that would be amazing.  Thanks.

---

### Post by ubergunner86 on 2009-01-29
> **gigaferz said:**
> let me know if this works 4 u, this card used to work with previous ubuntu versions, i installed intrepid and its not working either, You can run the screens and resolutions program but its kinda hidden in the latest ubuntus, I did it and there was a performance impact.

hope to hear from you.

Hey thanks for your advice, but that was one of the first things I tried.  I know that without proper drivers that the video card will not function properly, that is why I am currently using low resolutions (800x600 at the moment).  In addition, I tried using other resolutions, and surprisingly the computer even functioned better at higher resolutions, but the screen was still fuzzing just as much as the 800x600.  I'd rather not try and burn out the card/monitor and keep it low res until i can get my driver working properly.

---

### Post by ubergunner86 on 2009-01-29
> **carlee said:**
> try installing the drivers from nvidia themselves (they have their own drivers too)

make sure youve remove envyng before you do that or your ubuntu will have two drivers with the same name (which won't be good)

then add this line(s) to xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

```

Hey thanks for the tip, but I tried installing the driver and it did not load properly.  I have the log file listed above, I just don't know how to go about fixing the problem, as the log means nothing to me at the moment...

---

