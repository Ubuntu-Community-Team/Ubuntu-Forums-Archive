---
title: "How can I increase my screen resolution?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by jimmibennett on 2009-11-15
Right now it is a hideous 800X600, and this cannot be increased any further using the standard settings.

I have viewed some other threads, and somebody suggested using 

sudo gedit /etc/X11/xorg.conf

in the terminal.

When I do this, however, a blank screen just appears, and there is nothing for me to edit.

Please help!

---

### Post by coldReactive on 2009-11-15
What's your graphics card?

---

### Post by travmanx on 2009-11-15
Run sudo lshw and post back the results under 'display'

Have you tried 

xrandr -s 1024x768

Replace with your resolution tho...

---

### Post by jimmibennett on 2009-11-16
> **travmanx said:**
> Run sudo lshw and post back the results under 'display'

Have you tried 

xrandr -s 1024x768

Replace with your resolution tho...

I couldn't find a 'display' heading, but heres what I get when I run sudo Ishw:

james-laptop              
    description: Computer
    product: EasyNote MH35
    vendor: PACKARD BELL BV
    version: PB49201906
    serial: 12345678901234567
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: EasyNote MH35
       vendor: PACKARD BELL BV
       physical id: 0
       version: SI94B-20+SI96A-33
       serial: 1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: PE14A05 (08/13/2008)
          size: 105KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T1400  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: uPGA 479M
          size: 1730MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: burst internal write-back
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
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: DIMM2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1750MHz
          capabilities: ht
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
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:d0000000-d3ffffff
        *-pci:0
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:d4000000-d40fffff memory:c0000000-cfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:d4000000-d401ffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1080(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7530B
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: NX09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:d4104000-d4104fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:d4105000-d4105fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:d4106000-d4106fff
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:23:8b:33:bf:7e
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
             resources: irq:19 memory:d4307000-d430707f ioport:1000(size=128)
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:10c8(size=8) ioport:10bc(size=4) ioport:10c0(size=8) ioport:10b8(size=4) ioport:10a0(size=16)
           *-disk
                description: ATA Disk
                product: Hitachi HTS54321
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FB2O
                serial: 080919FB2200LCDJ01AA
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0782f72d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 93156d82-9c69-4cec-bb14-2002bd6c2ce5
                   size: 85GiB
                   capacity: 85GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-16 00:45:54 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 63GiB
                   capacity: 63GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 60GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2557MiB
                      capabilities: nofs
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:3000(size=8192) memory:dc000000-dfffffff
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52
             resources: irq:18 memory:d4100000-d4103fff
     *-scsi
          physical id: 2
          bus info: usb@1:4
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
  *-remoteaccess UNCLAIMED
       vendor: SiS
       physical id: 1
       capabilities: inbound
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:17:c4:43:b2:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.2 multicast=yes wireless=IEEE 802.11bg

when I run xrandr -s 1024X768 it says 'Size 1024x768 not found in available modes'

But Im pretty sure this that 1024X768 was the resolution that I had enabled in windows, and it was perfect.

---

### Post by jimmibennett on 2009-11-16
> **coldReactive said:**
> What's your graphics card?

I'm not sure, how can I find out?

---

### Post by jimmibennett on 2009-11-16
Oh Ive found it:

*-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:d4000000-d401ffff ioport:9000(size=12:)

---

### Post by ukripper on 2009-11-16
> **jimmibennett said:**
> Oh Ive found it:

*-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:d4000000-d401ffff ioport:9000(size=12:)

If you using 32bit ubuntu 9.10 you need this driver to make you graphics card work. Download this and install [http://launchpadlibrarian.net/24529643/xorg-driver-sis671_0.9_i386.deb](http://launchpadlibrarian.net/24529643/xorg-driver-sis671_0.9_i386.deb)

Do not make any changes in xorg.conf. this driver will do everything.

Edit reason:updated link for 9.10 driver

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> If you using 32bit ubuntu 9.10 you need this driver to make you graphics card work. Download this and install [http://launchpadlibrarian.net/24529643/xorg-driver-sis671_0.9_i386.deb](http://launchpadlibrarian.net/24529643/xorg-driver-sis671_0.9_i386.deb)

Do not make any changes in xorg.conf. this driver will do everything.

Edit reason:updated link for 9.10 driver



Thanks, I've tried that and restarted the system, but still I can't increase the resolution any higher. Is there anything I need to run once this program is installed?

---

### Post by ukripper on 2009-11-16
> **jimmibennett said:**
> Thanks, I've tried that and restarted the system, but still I can't increase the resolution any higher. Is there anything I need to run once this program is installed?

Can you post output of the following command:
```
tail -n 80 /var/log/Xorg.0.log
```

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> Can you post output of the following command:
```
tail -n 80 /var/log/Xorg.0.log
```


Here's what I get:

james@james-laptop:~$ tail -n 80 /var/log/Xorg.0.log
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(EE) config/hal: couldn't initialise context: unknown error (null)
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)

---

### Post by ukripper on 2009-11-16
can you post output of below command:
```
lsmod
```

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> can you post output of below command:
```
lsmod
```

Yeah...

james@james-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
joydev                 10272  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_realtek   203328  1 
rtl8187                50624  0 
sis190                 17824  0 
mac80211              181236  1 rtl8187
led_class               4096  1 rtl8187
psmouse                56180  0 
mii                     5212  1 sis190
serio_raw               5280  0 
eeprom_93cx6            1916  1 rtl8187
shpchp                 32272  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  2 rtl8187,mac80211
usb_storage            52544  0 
video                  19380  0 
output                  2780  1 video
sis_agp                 6972  1 
agpgart                34988  1 sis_agp
james@james-laptop:~$

---

### Post by ukripper on 2009-11-16
> **jimmibennett said:**
> Yeah...


sis_agp                 6972  1 
agpgart                34988  1 sis_agp


The deb drivers package you installed seems to be loaded fine within your kernel.

Now can you post output of your xorg.conf by running this command:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> The deb drivers package you installed seems to be loaded fine within your kernel.

Now can you post output of your xorg.conf by running this command:
```
sudo gedit /etc/X11/xorg.conf
```


A blank Gedit window pops up

Thanks for all your help by the way

---

### Post by ukripper on 2009-11-16
> **jimmibennett said:**
> A blank Gedit window pops up

Thanks for all your help by the way

can you post output of this command:
```
xrandr
```

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> can you post output of this command:
```
xrandr
```


Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0

---

### Post by ukripper on 2009-11-16
> **jimmibennett said:**
> Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0

ok can you run this in terminal and post output here:
```
cvt 1024 768 60
```

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> ok can you run this in terminal and post output here:
```
cvt 1024 768 60
```


# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

---

### Post by ukripper on 2009-11-16
can you run this in command line and see if it fixes your resolution to 1024 X 768. Note this will be temperory fix only, we'll need to put this fix in xorg.conf later on if it works for you.

So try below:
```
xrandr --newmode Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
```

and then

```
xrandr --addmode default 1024x768_60.00

```

This will switch you to 1024 X 768 mode temperorly and tell me if this works for you:
```
xrandr --output default --mode 1024x768_60.00
```

if this works then we can make it permanent and try different modes too.

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> can you run this in command line and see if it fixes your resolution to 1024 X 768. Note this will be temperory fix only, we'll need to put this fix in xorg.conf later on if it works for you.

So try below:
```
xrandr --newmode Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
```and then

```
xrandr --addmode default 1024x768_60.00

```This will switch you to 1024 X 768 mode temperorly and tell me if this works for you:
```
xrandr --output default --mode 1024x768_60.00
```if this works then we can make it permanent and try different modes too.


Hasn't worked unfortunately :(

This is what I get:

james@james-laptop:~$ xrandr --newmode Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
james@james-laptop:~$ xrandr --addmode default 1024x768_60.00
xrandr: cannot find mode "1024x768_60.00"
james@james-laptop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: cannot find mode 1024x768_60.00

---

### Post by ukripper on 2009-11-16
sorry my mistake. Forgot to take modeline out

So try below:
Code:
```

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
```

and then

Code:
```

xrandr --addmode default 1024x768_60.00
```

This will switch you to 1024 X 768 mode temperorly and tell me if this works for you:
Code:

```
xrandr --output default --mode 1024x768_60.00
```

---

### Post by jimmibennett on 2009-11-16
> **ukripper said:**
> sorry my mistake. Forgot to take modeline out

So try below:
Code:
```

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
```and then

Code:
```

xrandr --addmode default 1024x768_60.00
```This will switch you to 1024 X 768 mode temperorly and tell me if this works for you:
Code:

```
xrandr --output default --mode 1024x768_60.00
```


[COLOR=Green]This didn't change the resolution, yet it did create another option in the drop down list of displays in my display manager.
When I attempted to click on the preferred screen size, a small window appears saying:

'the selected screen configuration for displays could not be applied. Could not set the configuration for CRTC 256'

Here's my terminal:[/COLOR]

james@james-laptop:~$ xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
james@james-laptop:~$ xrandr --addmode default 1024x768_60.00
james@james-laptop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)

---

### Post by ukripper on 2009-11-16
can you tell me what resolution is supported by your monitor?

---

### Post by jimmibennett on 2009-11-17
> **ukripper said:**
> can you tell me what resolution is supported by your monitor?


Been looking online for a while, and I think it goes up to 1440x900

---

### Post by ukripper on 2009-11-17
> **jimmibennett said:**
> Been looking online for a while, and I think it goes up to 1440x900

follow my steps in this thread for 1440x900 
and then



```
xrandr --addmode default 1440x900_60.00
```



```
xrandr --output default --mode 1440x900_60.00
```

__________________

---

### Post by tedden on 2009-11-17
> **jimmibennett said:**
> Right now it is a hideous 800X600, and this cannot be increased any further using the standard settings.

I have viewed some other threads, and somebody suggested using 

sudo gedit /etc/X11/xorg.conf

in the terminal.

When I do this, however, a blank screen just appears, and there is nothing for me to edit.

Please help!xorg.conf, command removed in 9.10 version

---

### Post by realzippy on 2009-11-17
> **tedden said:**
> xorg.conf, command removed in 9.10 version

Run

[B]sudo rm /etc/X11/xorg.conf
[/B]
**gksudo gedit /etc/X11/xorg.conf **  *save empty file*

[B]sudo dpkg-reconfigure xserver-xorg
[/B]

Still no xorg.conf ?

---

