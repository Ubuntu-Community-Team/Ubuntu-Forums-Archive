---
title: "screen resolution"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Aitashan on 2011-07-28
it seems as if on 1280x1024 i am on 800x600 everything is too big

---

### Post by helenacoder on 2011-07-28
what kind of video card do you have?

---

### Post by wildmanne39 on 2011-07-28
Hi, you can open settings and set your font size.

Also have you looked in additional drivers to see if there is a driver for your video card there?

If there is not and you are not sure what video card or the specs of your system you can run this command in a terminal 
```
sudo lshw
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Aitashan on 2011-07-28
this is the result that i got i sorry i m new to the forum so i didn't caught the # thing u told anyways heres what i got
```

( description: Desktop Computer
    version: 4000888
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=C004F0FA-D81D-B211-8000-DE86D02848C5
  *-core
       description: Motherboard
       product: D865GLC
       vendor: Intel Corporation
       physical id: 0
       version: AAC28705-409
       serial: BTLC44216861
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: BF86510A.15A.0066.P13.0404221042
          date: 04/22/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: J2E1
          size: 2800MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
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
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: NT256D64S88AAG-7K
             vendor: Nanya Technology
             physical id: 0
             serial: 00000015
             slot: J6G1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: V826632K24SCTG-D3
             vendor: ProMOS/Mosel Vitelic
             physical id: 1
             serial: BD1A3802
             slot: J6G2
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: M3 68L3223ETM-CCC
             vendor: Samsung
             physical id: 2
             serial: 060C9550
             slot: J6H1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:3
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: KT326667-041-INCE5
             vendor: Kingston
             physical id: 3
             serial: 6C18CEAA
             slot: J6H2
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:ffa80000-ffafffff ioport:ec00(size=8)
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to CSA Bridge
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:b000(size=4096) memory:ff800000-ff8fffff
           *-network
                description: Ethernet interface
                product: 82547EI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 00
                serial: 00:11:11:84:04:dc
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:18 memory:ff8e0000-ff8fffff ioport:bc00(size=32)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c400(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:cc00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d000(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa7f400-ffa7f7ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:40000000-400003ff
           *-disk
                description: ATA Disk
                product: Maxtor 6Y120L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y3J6JTQE
                size: 114GiB (122GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000cefa0
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: aa3e1526-3a3a-46f2-880b-3a8a3453432e
                   size: 113GiB
                   capacity: 113GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-25 16:05:21 filesystem=ext4 lastmountpoint=/ modified=2011-07-25 17:06:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-28 13:14:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1004MiB
                   capacity: 1004MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1004MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:d400(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 memory:ffa7fc00-ffa7fdff memory:ffa7f800-ffa7f8ff)
```

---

### Post by realzippy on 2011-07-28
Which Ubuntu version do you use?
Note,there seems to be a problem with Intel 865 graphics
and Natty...
[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-05/03730/%28Bug-774999%29-Re-Intel-82865G-X11-unusable-after-Natty-upgrade.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-05/03730/%28Bug-774999%29-Re-Intel-82865G-X11-unusable-after-Natty-upgrade.html)

---

### Post by Aitashan on 2011-07-28
> **realzippy said:**
> which ubuntu version do you use?
Note,there seems to be a problem with intel 865 graphics
and natty...
[http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-05/03730/%28bug-774999%29-re-intel-82865g-x11-unusable-after-natty-upgrade.html](http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-05/03730/%28bug-774999%29-re-intel-82865g-x11-unusable-after-natty-upgrade.html)

11.04

---

### Post by realzippy on 2011-07-28
...so the bug might be "yours"...

---

### Post by Aitashan on 2011-07-28
now what should i do

---

### Post by realzippy on 2011-07-28
Well,8 years old hardware reaches EOL....

You could wait,maybe it gets fixed...
You could install 10.04....


**Edit:**
Maybe it is a DPI issue....
If you have some patience (and are willing to run some commands),we could check this out...

---

### Post by realzippy on 2011-07-28
Just posting to make you notice "edit" in post about...

---

### Post by Aitashan on 2011-07-28
> **realzippy said:**
> Just posting to make you notice "edit" in post about...

what are u trying to say

---

### Post by realzippy on 2011-07-28
..wanted you to notice that I have edited post #9...

---

### Post by Aitashan on 2011-07-28
> **realzippy said:**
> ..wanted you to notice that I have edited post #9...
  ok i am patince and willing to do what you say

---

### Post by realzippy on 2011-07-28
Ok.
Open terminal,run

```
xrandr -q
```

and post the output.

---

### Post by Aitashan on 2011-07-28
> **realzippy said:**
> Ok.
Open terminal,run

```
xrandr -q
```and post the output.

 this is the result i got

(Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0* 
   1152x864       75.0  
   1024x768       85.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     66.7     60.0  
   720x400        70.1

---

### Post by realzippy on 2011-07-28
Which monitor model do you use?

---

### Post by wildmanne39 on 2011-07-28
Hi, I am going to let realzippy take over it looks like he has it under control.

---

### Post by realzippy on 2011-07-28
@wildmanne39

Not really under control.Just wanted to help out "overnight"...
Idea is to set the DPI with xrandr ....
Comments welcome

@Aitashan
Run
```
xdpyinfo | grep dimensions
```
```
xdpyinfo | grep "dots per inch"
```

and post...

BTW,which monitor model?

---

### Post by Aitashan on 2011-07-29
> **realzippy said:**
> @wildmanne39

Not really under control.Just wanted to help out "overnight"...
Idea is to set the DPI with xrandr ....
Comments welcome

@Aitashan
Run
```
xdpyinfo | grep dimensions
``````
xdpyinfo | grep "dots per inch"
```and post...

BTW,which monitor model?

 dimensions:    1280x1024 pixels (339x271 millimeters)

 resolution:    96x96 dots per inch

and i use viewsonic lcd

---

### Post by Aitashan on 2011-07-29
thank you for your time realzippy please help me find a solution for this

---

### Post by °-° on 2011-07-29
Have you updated your graphics card drivers?

---

### Post by Aitashan on 2011-07-29
no there are no additional drivers for my graphic card

---

### Post by realzippy on 2011-07-29
Just realising that setting dpi with xrandr does not work anymore as it used to in older ubuntu versions.
Anyway,you should try what *wildmanne* suggested:
Right click on the desktop --> change desktop backround --> fonts --> details

then reduce the dpi.
Does it help ?

---

### Post by wildmanne39 on 2011-07-29
Hi, if my first suggestion does not work you can edit the xorg file, I will give you a link for it you will have to actually create the file it does not exist in natty anymore.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

### Post by Aitashan on 2011-07-31
> **wildmanne39 said:**
> Hi, if my first suggestion does not work you can edit the xorg file, I will give you a link for it you will have to actually create the file it does not exist in natty anymore.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

one thing i found in boot grub menu that my grub gfxmode wast set to 640x480

---

### Post by wildmanne39 on 2011-07-31
Hi, that is the default setting at boot up to allow you to boot it has nothing to do with the resolution after you are booted, unless your intel graphics driver is not loading properly but I doubt that is the case you can run these two commands and we will check.
```
lspci -k
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by realzippy on 2011-08-01
So have you checked out *wildmanne's* dpi suggestion yet or not?:

Right click on the desktop --> change desktop backround --> fonts --> details

then reduce the dpi.

---

### Post by Aitashan on 2011-08-04
sorry for not replying but since past 2 days i have been through a lot of pain had to reinstall ubuntu with xp using wubi and now i have to start all over again and whay i installed xp is a long story so anyways changing the dpi did not worked and here is the result of the commands you posted

---

### Post by Aitashan on 2011-08-04
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:03.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to CSA Bridge (rev 02)
    Kernel modules: shpchp
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: ata_piix
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
    Subsystem: Gateway 2000 Device 2026
    Kernel driver in use: e1000
    Kernel modules: e1000

```

```
Module                  Size  Used by
binfmt_misc            13213  1 
snd_usb_audio          91410  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  3 snd_intel8x0,snd_usb_audio,snd_ac97_codec
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
ppdev                  12849  0 
i915                  450944  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
uvcvideo               66851  0 
drm                   180037  3 i915,drm_kms_helper
snd                    55295  16 snd_intel8x0,snd_usb_audio,snd_ac97_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 i915
shpchp                 32345  0 
video                  18951  1 i915
parport_pc             32111  1 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e1000                 101089  0 

```

---

### Post by wildmanne39 on 2011-08-04
Hi, if you have any hope of getting the resolution you want you will need to use the link I gave you in post #24.

Your driver for your video card is loaded and being used but it is not really supported very well in 11.04 because of the age of the hardware.

I do not remember but you are probably using classic with no effects just to make 11.04 usable right? 

Here is a link for your card.
[http://ubuntuforums.org/showthread.php?t=1745151&highlight=82865G+Integrated+Graphics](http://ubuntuforums.org/showthread.php?t=1745151&highlight=82865G+Integrated+Graphics)

It may be best to go back to 10.04 for now.

In 10.04 you can even use effects like the cube.

That being said you should be able to use the link in post #24 to manually set resolution.

---

### Post by Aitashan on 2011-08-04
i am using unity 2d and i am still having trouble editing the xorg file

---

### Post by realzippy on 2011-08-04
As somebody formerly mentioned,your graphics card reaches EOL with
newer Ubuntu versions.
Get off the dead horse  !!
...and install 10.04 to get the maximum out of your graphics card. :o

---

### Post by Aitashan on 2011-08-04
ok thanks

---

### Post by Aitashan on 2011-08-04
> **realzippy said:**
> As somebody formerly mentioned,your graphics card reaches EOL with
newer Ubuntu versions.
Get off the dead horse  !!
...and install 10.04 to get the maximum out of your graphics card. :o
 is there a difference between 10.10 and 10.04 which is best for me

---

### Post by realzippy on 2011-08-04
Generally:
Ubuntu 10.04 LTS is supported until april 2013.
10.10 only until april 2012.

Concerning your Intel Corporation 82865G graphics:
I don 't know,you had to google for it.
But it may be faster to install it and see what happens.

---

### Post by wildmanne39 on 2011-08-04
Hi, you should be good with 10.04.

---

