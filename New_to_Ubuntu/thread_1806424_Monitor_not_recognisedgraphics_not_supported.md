---
title: "Monitor not recognised/graphics not supported?"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by metalmickey on 2011-07-17
Hi,
I have just received a monitor back from repair, whilst it was away (which took a few weeks) I installed 11.04. No problems at the time, however my new monitor supports a higher resolution (full 1080 HD)

The highest resolution I have available is 1024x768 in 4:3 mode.

I dual boot with Windows 7, which I have set at 1600x1200 @60hz in 16:9 mode.

Everything under Ubuntu looks too big & sometimes menus etc.are missing off the bottom of the screen.

My monitor shows as unknown, it is a DGM 23" so not exactly a well known make.

My graphics card is Intel G41 Express 4 series, which is on board a Asustek P5qpl-am motherboard.

It looks like the standard Intel drivers are installed, but now I'm wondering if unity will work using this graphics? I can't get any higher than 1024x768.

---

### Post by ikt on 2011-07-17
Is there an option to install any intel drivers in the additional drivers program?

---

### Post by wep940 on 2011-07-17
If you can connect to the internet, do so and then do the following:
 
- open a terminal window (applications/accessories/terminal)
 
- type:  sudo apt-get update <press enter>  and wait for this to finish
 
- click on system/administration/additional drivers.  Hopefully this will run for a while and then find a driver, but I'm more suspicious that your monitor being undefined means you will probably have to enter mode lines to set the various resolutions and timings to make it work.

---

### Post by wildmanne39 on 2011-07-17
> **metalmickey said:**
> Hi,
I have just received a monitor back from repair, whilst it was away (which took a few weeks) I installed 11.04. No problems at the time, however my new monitor supports a higher resolution (full 1080 HD)

The highest resolution I have available is 1024x768 in 4:3 mode.

I dual boot with Windows 7, which I have set at 1600x1200 @60hz in 16:9 mode.

Everything under Ubuntu looks too big & sometimes menus etc.are missing off the bottom of the screen.

My monitor shows as unknown, it is a DGM 23" so not exactly a well known make.

My graphics card is Intel G41 Express 4 series, which is on board a Asustek P5qpl-am motherboard.

It looks like the standard Intel drivers are installed, but now I'm wondering if unity will work using this graphics? I can't get any higher than 1024x768.
Hi, intel cards are supported in the kernel so it should be working but we can check that and a few other things. Run these commands in a terminal
```
sudo lspci -k
```
```
lsmod
```
```
/usr/lib/nux/unity_support_test -p
```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

If your driver is loading like it should then you will have to set the resolution manually by one of these to means, here is a link for both methods.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

### Post by Reahreic on 2011-07-17
> **wildmanne39 said:**
> Hi, intel cards......

Im having a similar issue with regards to an unknown monitor, ive tried the 915revision stuff to no avail. not to threadjack but i have attached the results of running your suggested code below.
im on an older Inspiron 500m (which im glad to say is running 10000% faster than when i had winxp on it)
[B]
sudo lspci -k[/B]
```
stephanie@Penguinbreath:~$ sudo lspci -k
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Dell Device 0153
    Kernel driver in use: agpgart-intel
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Dell Device 0153
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Dell Device 0153
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Dell Device 0153
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Dell Device 0153
    Kernel modules: i915
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
    Subsystem: Dell Device 0153
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500
    Kernel driver in use: ata_piix
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
    Subsystem: Dell Device 0153
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
    Subsystem: PCTel Inc Latitude D500
    Kernel modules: snd-intel8x0m
01:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
    Subsystem: Dell Device 0153
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
    Subsystem: Dell Latitude D500
    Kernel driver in use: e100
    Kernel modules: e100

```

**lsmod**
```
stephanie@Penguinbreath:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  0 
udf                    83795  0 
crc_itu_t              12627  1 udf
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
i915                  450934  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
snd_seq_midi           13132  0 
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 i915
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
usb_storage            43946  1 
pcmcia_rsrc            18292  1 yenta_socket
ppdev                  12849  0 
drm                   180037  2 i915,drm_kms_helper
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
joydev                 17322  0 
uas                    17676  0 
soundcore              12600  1 snd
parport_pc             32111  1 
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 

```

**unity support test**
```
stephanie@Penguinbreath:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```
[B]
sudo lshw
[/B]```
stephanie@Penguinbreath:~$ sudo lshw
penguinbreath             
    description: Portable Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4C00-1058-8056-B4C04F563231
  *-core
       description: Motherboard
       product: 04Y212
       vendor: Winbond Electronics
       physical id: 0
       serial: .4LXVV21.CN486433410509.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A08
          date: 07/14/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1300MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.9.5
          slot: Microprocessor
          size: 1300MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1280MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:f0000000-f7ffffff memory:faf80000-faffffff ioport:c000(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-efffffff memory:faf00000-faf7ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf40(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:faeffc00-faefffff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fc000000-fdffffff memory:50000000-53ffffff
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:01:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:11 memory:fc000000-fc000fff ioport:e000(size=256) ioport:e400(size=256) memory:50000000-53ffffff memory:58000000-5bffffff
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 81
                serial: 00:0b:db:05:f7:b2
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:11 memory:fcfff000-fcffffff ioport:ecc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
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
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:54000000-540003ff
           *-disk
                description: ATA Disk
                product: IC25N020ATCS04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: CA2O
                serial: CSL204DMDM25NE
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009701c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ead6e95d-1089-4bda-82c5-9c63a0ba271c
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-17 12:28:12 filesystem=ext4 lastmountpoint=/ modified=2011-07-17 13:16:27 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-17 18:26:52 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1278MiB
                   capacity: 1278MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1278MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SBW-242
                vendor: QSI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UD22
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:d800(size=256) ioport:dc40(size=64) memory:faeff800-faeff9ff memory:faeff400-faeff4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:d400(size=256) ioport:d080(size=128)
     *-scsi
          physical id: 1
          bus info: usb@1:3.3
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             size: 3843MiB (4029MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/5A5A9F285A9EFFC5
                version: 3.1
                serial: 5a9e-ffc5
                size: 3835MiB
                capacity: 3839MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-07-17 12:11:46 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-battery
       product: DELL 0008P78
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:1c:df:30:0c:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-10-generic firmware=0.12 ip=192.168.1.67 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by wildmanne39 on 2011-07-18
Hi Reahreic, are you using 11.04 in classic mode?

You will need to use one of those links in my previous post to manually set your resolution, your driver is loaded so that is not the problem.

In 11.04 I have seen several people that the monitor did not get detected properly and one of those two methods in my previous post should do the trick, I know the instructions can be confusing so take your time.

---

### Post by metalmickey on 2011-07-18
No frivers found using wep940 advice.

wildmanne39 here is the results I get:

```
dad@dad-puta:~$ sudo lspci -k
[sudo] password for dad: 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 836d
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 836d
	Kernel driver in use: i915
	Kernel modules: i915
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 840b
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Kernel driver in use: ata_piix
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Kernel driver in use: ata_piix
01:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
	Subsystem: ASUSTeK Computer Inc. P5KPL-CM Motherboard
	Kernel driver in use: ATL1E
	Kernel modules: atl1e
03:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs SB0090 Audigy Player/OEM
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1
03:00.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs SB Audigy Game Port
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp
03:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
	Subsystem: Creative Labs SB Audigy FireWire Port
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
03:01.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 11)
	Subsystem: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller
	Kernel driver in use: pata_it821x
	Kernel modules: pata_it821x
dad@dad-puta:~$ 
```

```
dad@dad-puta:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_emu10k1_synth      12964  0 
snd_emux_synth         33506  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13482  1 snd_emux_synth
snd_emu10k1           137068  5 snd_emu10k1_synth
snd_ac97_codec        105614  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  4 snd_hda_intel,snd_hda_codec,snd_emu10k1,snd_ac97_codec
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13274  3 snd_hda_codec,snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
snd_rawmidi            25269  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
i915                  450979  5 
snd_seq                51291  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_emu10k1,snd_pcm,snd_seq
ppdev                  12849  0 
snd_seq_device         14110  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
snd                    55295  29 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp             12566  0 
asus_atk0110           17664  0 
drm                   184133  6 i915,drm_kms_helper
psmouse                59039  0 
gameport               15027  2 emu10k1_gp
i2c_algo_bit           13184  1 i915
parport_pc             32111  1 
serio_raw              12990  0 
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  3 snd_hda_intel,snd_emu10k1,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
pata_it821x            18001  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
atl1e                  32576  0 
dad@dad-puta:~$ 
```

```
dad@dad-puta:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
dad@dad-puta:~$ 
```

```
dad@dad-puta:~$ sudo lshw
[sudo] password for dad: 
dad-puta                  
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=003B0916-5C27-DF11-94C3-485B3912C872
  *-core
       description: Motherboard
       product: P5QPL-AM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: 104234970000106
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0414
          date: 06/11/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: LGA775
          size: 1203MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM B1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1203MHz
          capacity: 1203MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:fe400000-fe7fffff memory:e0000000-efffffff ioport:cc00(size=8)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:fe9f8000-fe9fbfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:dde00000-ddffffff ioport:de000000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fea00000-feafffff ioport:de200000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: b0
                serial: 48:5b:39:12:c8:72
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:43 memory:feac0000-feafffff ioport:dc00(size=128)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c400(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c480(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c800(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe9f7c00-fe9f7fff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:19 ioport:e880(size=32)
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:ec00(size=8)
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:febff800-febfffff memory:febf8000-febfbfff
           *-storage
                description: RAID bus controller
                product: IT/ITE8212 Dual channel ATA RAID controller
                vendor: Integrated Technology Express, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list rom
                configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8
                resources: irq:16 ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=8) ioport:e080(size=4) ioport:e000(size=16) memory:fe940000-fe95ffff
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk:0
                description: ATA Disk
                product: ST3160215ACE
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AC
                serial: 9RXH7T6Q
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003a154
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: fbe81460-9312-4131-941f-820f3a373153
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-06-19 12:53:53 filesystem=ntfs label=new drive state=clean
           *-disk:1
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: YAR4
                serial: Y2J5GZFE
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=39e639e5
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: ee7e27fe-0c15-6646-9d9a-f92280a30461
                   size: 76GiB
                   capacity: 76GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-05-01 13:10:28 filesystem=ntfs label=Backups state=clean
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: 1AJ1
                serial: S246J9AZ200676
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3f188d72
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 4cc4-8112
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-05-22 01:18:25 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdc2
                   version: 3.1
                   serial: 24b5a578-b43a-6742-9b81-f952b4805398
                   size: 558GiB
                   capacity: 558GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-05-22 01:18:31 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdc3
                   size: 373GiB
                   capacity: 373GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 4060MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdc6
                      logical name: /
                      capacity: 365GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sdc7
                      capacity: 4060MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7240S
                vendor: Optiarc
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
dad@dad-puta:~$ 
```

All of which by the way means absolutely nothing to me:confused:

Many thanks for helping though...

---

### Post by wildmanne39 on 2011-07-18
Hi, your video card driver is loaded properly so you will have to use one of the links in post #4 to set your resolution manually.

---

### Post by Reahreic on 2011-07-18
> **wildmanne39 said:**
> Hi Reahreic, are you using 11.04 in classic mode?

You will need to use one of those links in my previous post to manually set your resolution, your driver is loaded so that is not the problem.

In 11.04 I have seen several people that the monitor did not get detected properly and one of those two methods in my previous post should do the trick, I know the instructions can be confusing so take your time.

I have attempted the Xorg.conf method however my xorg.xconf is missing or located in several other folders with an additional suffix. There Ctrl + Alt + F1 methods of stopping gdm and generating a xorg.config fail for me each time i try the step sudo xorg -configure

This method also fails  [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

it honestly shouldn't be this difficult to have properly setup video/monitor drivers.

---

### Post by wildmanne39 on 2011-07-18
Hi, type this in a terminal
```
gksudo gedit /etc/X11/xorg.conf
```that will create the file make the adjustment needed then save and exit and restart your system.

Please be careful or you can make your system not bootable if that happens run these two commands from recovery mode by hitting the shift key while you boot then choose root recovery with network
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sandyd on 2011-07-18
> **Reahreic said:**
> I have attempted the Xorg.conf method however my xorg.xconf is missing or located in several other folders with an additional suffix. There Ctrl + Alt + F1 methods of stopping gdm and generating a xorg.config fail for me each time i try the step sudo xorg -configure

This method also fails  [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

it honestly shouldn't be this difficult to have properly setup video/monitor drivers.
Xorg -configure generates xorg.conf in the current directory
do
```

sudo rm xorg.conf*
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

---

### Post by Reahreic on 2011-07-18
After about 2 hours of fiddling i was able to get an xorg.conf configured

Following this tut [http://grenage.com/xorg.html](http://grenage.com/xorg.html) i started manipulating the file. I noticed that the system seems to think that i have 4 screens and 4 graphics cards running each set up slightly differently one VESA one intel and two others.

I tweaked the file and proceeded with startx and got an error about there being screens but the system not being able to use them and that the desktop environment wouldn't load.

below is my tweaked xorg.conf file which i backed up and then removed. perhaps you can see something. (im starting to get used the the cmd line again but my wife wants ease of use lol)

```
 
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dri2"
        Load  "dri"
        Load  "dbe"
        Load  "extmod"
        Load  "record"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Inte 855GM"
        ModelName    "Dell Inspiron 500m 14in"
        HorizSync       59.89
        VertRefresh     63.67
EndSection


Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        VendorName "Intel 855GM"
        BusID       "PCI:0:2:0"
EndSection
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 16
        SubSection "Display"
                Depth  24
                Modes "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1024x768"
        EndSubSection
EndSection


```

tomorrow evening ill post the auto generated xorg.conf file for you to mull over as i cant find the paper with teh code on it now lol

---

### Post by wildmanne39 on 2011-07-19
Hi, what makes you think this?
> I noticed that the system seems to think that i have 4 screens and 4 graphics cards running each set up slightly differently one VESA one intel and two others.
The vesa is installed by default it is a fall back driver it is used at boot time so you can see the boot menu and is a fall back driver.

I looked at the lsmod information and the intel driver is the only one that is being used, unless that changed when you made your xorg.conf file but I doubt that happened if in doubt run lsmod again.

---

### Post by Reahreic on 2011-09-05
After much reading and trying to get the screen rez and hardware 3d accell working im still stuck at 1024x768 with no hardware accell.

Does anyne know the reason why these intel drivers cant identify the monitors and detect their settings correctly.

---

### Post by beew on 2011-09-05
Try upgrading your driver from this ppa
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by cwsnyder on 2011-09-05
My Etronix 1701B monitor's EDID is also not read properly by Ubuntu, so I may be able to help.

First, your xorg.conf file doesn't include the modelines needed to properly display on your monitor.  Included is the xorg.conf file which I used on 10.10 Ubuntu.```
# nvidia-xconfig: X configuration file generated by nvidia-xconf
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x1024"
    HorizSync       31.5 - 64.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
 #
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 1024
        Depth       24
        Modes      "1280x1024@60" "1024x768@60" "1280x960@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"
 #
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection
```Note that this is for an nVidia GeForce 6200, not an Intel display card, so this is just for layout and lines needed in the subsections.

For me, 11.04 doesn't work with the above xorg.conf file.  I had to use the method outlined in [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html) to change the display settings with xrandr.

---

