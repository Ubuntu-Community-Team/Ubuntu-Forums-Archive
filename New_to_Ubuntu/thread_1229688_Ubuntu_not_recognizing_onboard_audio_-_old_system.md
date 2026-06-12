---
title: "Ubuntu not recognizing onboard audio - old system"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Nikhil.S on 2009-08-02
Hi, before going into the details I would like to state that I have only posted this thread after reading several other related threads and researching for two days. I read whatever I could using the "Search" function of the forums for Audio problems, Audio Drivers, Troubleshooting, general help, codecs [Multimedia guide sticky, audio guide sticky, general help] etc. If however, I have missed something that would solve this problem I apologize.

I have a Compaq Deskpro - Intel Pentium three 650 Mhz, 384 Mb memory, ATI 3D rage pro agp 1x/2x

This system had windows XP before and the audio was working, but the system was really slow and I decided to switch to Ubuntu.

The volume control shows Playback: Null Output (Pulse Audio Mixer) for Device.

After reading several threads I followed the steps outlined in Comprehensive sound problem guide. I got stuck where the ALSA drivers are supposed to be installed. On the site I cannot find anything related to my chipset. Some of the links did not work for Intel so Im not even sure if it is supported. I tried downloading the closest module/driver I could find with the "sudo modprobe snd-" command, which was "snd-Intel8x0" with no results.

I checked the sound troubleshooting section and followed the steps. The modules are properly installed as i see a list pop up when i put in the ocmmand "find /lib/modules/`uname -r` | grep snd". I downloaded them again just in case rebooted and checked for the audio card and it still didnt work.

checked the BIOS the onboard sound is on. Reset the BIOS to factory defaults just in case. Checked and made sure volume is not muted. Downloaded softwares sysinfo and several others to see if they have any info - didnt help. 


Now I am not sure that this is happening because theres no driver for the chipset or if this is a bug in the OS or the hardware has a problem? The motherboard doesnt seem to recognize onboard audio, but it worked in XP somehow.

Any help would be appreciated :shock: . Once again if this has been dealt with before, I apologize. I am posting output form commands that i tried. 


aplay -l Displays the following :
```
aplay: device_list:217: no soundcards found...
```the command lspci gives the following info:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:10.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:12.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
```the command "lspci -v | less" gives the following result:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at 44000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-410fffff
        Prefetchable memory behind bridge: 20000000-200fffff
        Kernel modules: shpchp

00:10.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
        Subsystem: D-Link System Inc Device 3a16
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 41200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath_pci, ath5k

00:12.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
        Subsystem: Compaq Computer Corporation Device b0d7
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at 41300000 (32-bit, prefetchable) [size=4K]
        I/O ports at 2000 [size=32]
        Memory at 41100000 (32-bit, non-prefetchable) [size=1M]
        [virtual] Expansion ROM at 20100000 [disabled] [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100, eepro100

00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 2040 [size=16]
        Kernel driver in use: ata_piix

00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2020 [size=32]
        Kernel driver in use: uhci_hcd

00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9
        Kernel driver in use: piix4_smbus
        Kernel modules: i2c-piix4

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
        Subsystem: ATI Technologies Inc Device 0084
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 1000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
```the command lshw gives the following info:
```
description: Mini Tower Computer
    product: Deskpro
    vendor: Compaq
    serial: 6023DKZCA066
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
    configuration: boot=normal chassis=mini-tower uuid=1CE75639-17E2-D411-80D0-B4896CAB46EB
  *-core
       description: Motherboard
       product: 0400h
       vendor: Compaq
       physical id: 0
       serial: 6023DKZCA066
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 686T3 (08/18/99)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: J22
          size: 650MHz
          capacity: 950MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: burst internal write-through
        *-cache:1
             description: L2 cache
             physical id: a
             slot: Cache L2
             size: 256KiB
             capacity: 4MiB
             capabilities: burst internal write-through
     *-memory:0
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          capacity: 384MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM #1: J10
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM #2: J11
             size: 128MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM #3: J12
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 22
          slot: System board or motherboard
          capacity: 256KiB
        *-bank UNCLAIMED
             description: Chip FLASH
             physical id: 0
             slot: AM29F002: U35
             size: 256KiB
             width: 16 bits
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 5c
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 bus_master cap_list
                configuration: latency=66 mingnt=8
        *-network:0
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: wmaster0
             version: 01
             serial: 00:11:95:d4:c4:de
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath5k_pci ip=192.168.0.193 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-network:1
             description: Ethernet interface
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 05
             serial: 00:50:8b:ae:98:31
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64
           *-disk
                description: ATA Disk
                product: Maxtor 6E040L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: NAR6
                serial: E1NLZFKE
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c3fcc3fc
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2dce73d7-31c7-42cb-a6a8-cacae031e107
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-08-01 09:45:30 filesystem=ext3 modified=2009-08-02 10:03:54 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-02 10:03:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1090MiB
                   capacity: 1090MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1090MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:e5:32:5e:c4:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```the "find /lib/modules/`uname -r` | grep snd" command gavethe following result:

```
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-14-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-14-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-14-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-14-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-14-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.28-14-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.28-14-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-14-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-14-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-14-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-14-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-14-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-14-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-14-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
```

---

### Post by cariboo on 2009-08-02
It looks like you have an isa sound device. I would suggest you use [isapnptools]("http:////www.roestock.demon.co.uk/isapnptools/") to get your sound card to work, unfortunately debian has dropped the package, so you will have to use the tar package form the page.

Ideally, if you have an extra pci slot, you can install a pci sound card and get your sound working.

---

### Post by Nikhil.S on 2009-08-03
Thanks a lot for the solution, I didnt even know that I had an ISA device (or the technology existed). The isapnptools utility looks really complex to implement. I am just beginning to use Ubuntu and am completely unaware of how it would work. Is there any other program or anything that I can do to make this work? 
didnt want to spend any money on this system as its really old anyways 

appreciate the help thanks

---

