---
title: "No TV. The card is not being detected but Ok in Vista"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by cpcpcp on 2010-09-19
The card, a Peak DVB-T digital TV PCI card, works OK in Vista. Nothing works it in Ubuntu and no TV card is detected. How do I "switch on" the card for Ubuntu?  If I, or rather you, can do that for me which prog would you go for -MeTV TV Time or what?

If this helps here is the result of lshw -short

```
cjp@cjp-desktop:~$ sudo lshw -short
H/W path      Device       Class       Description
==================================================
                           system      System Product Name
/0                         bus         M2N4-SLI
/0/0                       memory      128KiB BIOS
/0/3                       processor   AMD Athlon(tm) 64 X2 Dual Core Processor 
/0/3/b                     memory      128KiB L1 cache
/0/3/d                     memory      512KiB L2 cache
/0/5                       processor   CPU
/0/5/c                     memory      128KiB L1 cache
/0/5/e                     memory      512KiB L2 cache
/0/37                      memory      2GiB System Memory
/0/37/0                    memory      1GiB DIMM 667 MHz (1.5 ns)
/0/37/1                    memory      1GiB DIMM 667 MHz (1.5 ns)
/0/37/2                    memory      DIMM [empty]
/0/37/3                    memory      DIMM [empty]
/0/4                       memory      Memory controller
/0/1                       bridge      CK804 ISA Bridge
/0/1.1                     bus         CK804 SMBus
/0/2                       bus         CK804 USB Controller
/0/2.1                     bus         CK804 USB Controller
/0/f                       multimedia  CK804 AC'97 Audio Controller
/0/6          scsi0        storage     CK804 IDE
/0/6/0        /dev/cdrom1  disk        DVD RW AD-5170A
/0/6/0.1.0    /dev/cdrom   disk        CD/DVDW SH-S182M
/0/6/0.1.0/0  /dev/cdrom   disk        
/0/6/1        /dev/sda     disk        80GB ST380011A
/0/6/1/1      /dev/sda1    volume      74GiB Windows NTFS volume
/0/7          scsi5        storage     CK804 Serial ATA Controller
/0/7/0.0.0    /dev/sdb     disk        250GB MAXTOR STM325031
/0/7/0.0.0/1  /dev/sdb1    volume      120GiB Windows NTFS volume
/0/7/0.0.0/2  /dev/sdb2    volume      4768MiB Linux swap volume
/0/7/0.0.0/3  /dev/sdb3    volume      107GiB EXT4 volume
/0/8          scsi7        storage     CK804 Serial ATA Controller
/0/8/0.0.0    /dev/sdc     disk        250GB MAXTOR STM325082
/0/8/0.0.0/1  /dev/sdc1    volume      232GiB Windows NTFS volume
/0/9                       bridge      CK804 PCI Bridge
/0/9/6                     storage     INI-950 SCSI Adapter
/0/9/7                     bus         VT82xxxxx UHCI USB 1.1 Controller
/0/9/7.2                   bus         USB 2.0
/0/a          eth0         bridge      CK804 Ethernet Controller
/0/b                       bridge      CK804 PCIE Bridge
/0/c                       bridge      CK804 PCIE Bridge
/0/d                       bridge      CK804 PCIE Bridge
/0/e                       bridge      CK804 PCIE Bridge
/0/e/0                     display     G96 [GeForce 9500 GT]
/0/100                     bridge      K8 [Athlon64/Opteron] HyperTransport Tech
/0/101                     bridge      K8 [Athlon64/Opteron] Address Map
/0/102                     bridge      K8 [Athlon64/Opteron] DRAM Controller
/0/103                     bridge      K8 [Athlon64/Opteron] Miscellaneous Contr
/0/10         scsi3        storage     
/0/10/0.0.0   /dev/sdd     disk        SCSI Disk
/0/10/0.0.1   /dev/sde     disk        SCSI Disk
/0/10/0.0.2   /dev/sdf     disk        SCSI Disk
/0/10/0.0.3   /dev/sdg     disk        SCSI Disk

```Something simple I hope.:)

---

### Post by halj32 on 2010-09-19
first have you installed "linux-firmware-nonfree" as this is needed
next you need to use a media player like Kaffeine which can detect your tv card and scan for channels
also make sure you have the codecs installed like ffmpeg & w-scan etc. 
look in Synaptic Package Manager 

good luck

---

### Post by cpcpcp on 2010-09-19
How does one get to know all this stuff??

Anyway installed linux-firmware-nonfree" 
Had ffmeg, installed w-scan
ran MeTV and was told 
"***There are no digital tuner devices available***"

TV Time Television Viewer just opens a window and closes


Same question then - how do I get Ubuntu to "see" the card?

:)Still smiling as I do not need to watch television (just feel that if I have it it ought to work):)

---

### Post by realzippy on 2010-09-19
Is "Peak DVB-T digital TV PCI" all you got?Any Numbers?Is it the PEAK hybrid or dual tuner card?

---

### Post by cpcpcp on 2010-09-19
> **realzippy said:**
> Is "Peak DVB-T digital TV PCI" all you got?Any Numbers?Is it the PEAK hybrid or dual tuner card?

Neither hybrid not Dual it is their bog standard device 103906AGPK

---

### Post by cpcpcp on 2010-10-02
Anybody got a solution for me?

Pretty Please.     ):P


Chris

---

### Post by Mark Phelps on 2010-10-02
Don't have a solution but do have a suggestion.  Go to the MythTV site.  I believe they have a list of supported TV tuners.  If yours is NOT on the list, you're most probably out of luck.  There are only a limited set of TV tuner cards for which Linux drivers exist.

---

### Post by am4tor on 2010-10-02
Can You please copy-paste here the responses to these commands (no quotemarks )?

[B]" lspci -v  "
[/B]
"[B] lsmod "

[/B]and

[B]" dmesg | grep tuner  "  .

[/B]B.r.

---

### Post by cpcpcp on 2010-10-02
> **am4tor said:**
> Can You please copy-paste here the responses to these commands (no quotemarks )?

[B]" lspci -v  "
[/B]
"[B] lsmod "

[/B]and

[B]" dmesg | grep tuner  "  .

[/B]B.r.
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: 66MHz, fast devsel, IRQ 5
    I/O ports at fc00 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at feb00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 822c
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at f000 [size=256]
    I/O ports at ec00 [size=256]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at e800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d400 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c000 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fdf00000-fdffffff
    Prefetchable memory behind bridge: 80000000-800fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
    Subsystem: ASUSTeK Computer Inc. Device 812a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at bc00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:06.0 SCSI storage controller: Initio Corporation INI-950 SCSI Adapter (rev 02)
    Subsystem: Device 9292:0202
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at ac00 [size=256]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at 80000000 [disabled] [size=32K]
    Kernel driver in use: initio
    Kernel modules: initio

01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at a800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

05:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 1573
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 9c00 [size=128]
    [virtual] Expansion ROM at fbf80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau

``````
 cjp@cjp-desktop:~$ lsmod
Module                  Size  Used by
ndiswrapper           184677  0 
nls_utf8                1069  0 
isofs                  29250  0 
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2870sta             461811  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nvidia               9961216  38 
parport_pc             25962  1 
asus_atk0110            9017  0 
psmouse                63245  0 
serio_raw               3978  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39425  0 
pata_amd                8766  0 
forcedeth              49556  0 
initio                 17807  0 
sata_nv                19440  4 
```The third request produced no output.

[SIZE=2]**And the MYTH TV site was silent about Peak hardware (and most other hardware by name)**[/SIZE]

---

### Post by am4tor on 2010-10-02
From Nvidia site  [http://www.nvidia.com/Download/index.aspx?lang=en-us ]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
download the apropriate driver for [GeForce 9500 GT] (NOT THE NEWEST but the recomended), 
next uninstal the nouveau driver and 
next install the Nvidia proprietary driver just downloaded (see install notes on download page and this link: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html]("http://http//www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") )

Next install MeTV like described here: [http://www.ubuntugeek.com/me-tv-digital-television-viewer-for-gnome.html](http://www.ubuntugeek.com/me-tv-digital-television-viewer-for-gnome.html)

Hope will work.

---

### Post by SeijiSensei on 2010-10-02
You might get some help here: [http://www.avsforum.com/avs-vb/forumdisplay.php?f=76](http://www.avsforum.com/avs-vb/forumdisplay.php?f=76)

---

### Post by cpcpcp on 2010-10-02
> **am4tor said:**
> From Nvidia site  [http://www.nvidia.com/Download/index.aspx?lang=en-us ]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
download the apropriate driver for [GeForce 9500 GT] (NOT THE NEWEST but the recomended), 
next uninstal the nouveau driver and 
next install the Nvidia proprietary driver just downloaded (see install notes on download page and this link: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html]("http://http//www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") )

Next install MeTV like described here: [http://www.ubuntugeek.com/me-tv-digital-television-viewer-for-gnome.html](http://www.ubuntugeek.com/me-tv-digital-television-viewer-for-gnome.html)

Hope will work.

Interesting.:confused:
The file I downloaded was NVIDIA-Linux-x86-256.53.run
The Nvidia site said go to the directory install the driver by  running, as root, sh  ./NVIDIA-Linux-x86-256.53-pkg1.run
and doing so the error message was could not open file
As a newbie I suppose it ought to have said ...  running, as root, sh  ./NVIDIA-Linux-x86-256.53.run
but being nervous would you please confirm.
Or should I have done something about Nvidia Nouvae (whatever) first?

It all looks a bit tricky to me:confused:

---

### Post by cpcpcp on 2010-10-02
Just asking but why can all this not be done using the Administration -> Hardware Drivers or Administration -> Nvidia X Server Settings  (huh!!) ?

Chris

---

### Post by am4tor on 2010-10-03
You're right, You may install it throu graphical way and please do install the proprietary nvidia video driver in order to benefit the full pover of it.

The main isue is that your tvcard isn't recognized at all (...). I've dig it a while and it seems that you need to install the "kernel-source" and the "kernel-headers" .
example: "apt-get install kernel-source-**2.5.25**"  or "apt-get install kernel-headers-**2.5.25**"

In CLI (Terminal window You do:
[B]
uname -r[/B]     (obtain the kernel "release" neded to put instead 2.5.25 above)
then if you are not root, use sudo to install .
restart PC
re run  **lspci -v** and other commands and paste here the result.

Or maybe you know what kinda chip is on your tvcard ()

B.r.

---

### Post by cpcpcp on 2010-10-04
> **am4tor said:**
> You're right, You may install it throu graphical way and please do install the proprietary nvidia video driver in order to benefit the full pover of it.

The main isue is that your tvcard isn't recognized at all (...). I've dig it a while and it seems that you need to install the "kernel-source" and the "kernel-headers" .
example: "apt-get install kernel-source-**2.5.25**"  or "apt-get install kernel-headers-**2.5.25**"

In CLI (Terminal window You do:
[B]
uname -r[/B]     (obtain the kernel "release" neded to put instead 2.5.25 above)
then if you are not root, use sudo to install .
restart PC
re run  **lspci -v** and other commands and paste here the result.

Or maybe you know what kinda chip is on your tvcard ()

B.r.

Not a lot of joy

```
 cjp@cjp-desktop:~$ uname -r
2.6.32-24-generic
cjp@cjp-desktop:~$ apt-get install kernel-source-2.6.32
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cjp@cjp-desktop:~$ sudo apt-get install kernel-source-2.6.32
[sudo] password for cjp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-source-2.6.32
cjp@cjp-desktop:~$ sudo apt-get install kernel-headers-2.6.32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.32
cjp@cjp-desktop:~$ lspci-v
lspci-v: command not found
cjp@cjp-desktop:~$ lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: 66MHz, fast devsel, IRQ 5
    I/O ports at fc00 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at feb00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 822c
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at f000 [size=256]
    I/O ports at ec00 [size=256]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at e800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d400 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c000 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fdf00000-fdffffff
    Prefetchable memory behind bridge: 80000000-800fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
    Subsystem: ASUSTeK Computer Inc. Device 812a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at bc00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:06.0 SCSI storage controller: Initio Corporation INI-950 SCSI Adapter (rev 02)
    Subsystem: Device 9292:0202
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at ac00 [size=256]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at 80000000 [disabled] [size=32K]
    Kernel driver in use: initio
    Kernel modules: initio

01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at a800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

05:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 1573
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 9c00 [size=128]
    [virtual] Expansion ROM at fbf80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nvidia-current, nvidiafb, nouveau

cjp@cjp-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  3 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
ppdev                   5259  0 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
nvidia               9961216  42 
parport_pc             25962  1 
agpgart                31724  1 nvidia
asus_atk0110            9017  0 
psmouse                63245  0 
serio_raw               3978  0 
ndiswrapper           184677  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
i2c_nforce2             5199  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39425  0 
forcedeth              49556  0 
initio                 17807  0 
pata_amd                8766  0 
sata_nv                19440  4 
cjp@cjp-desktop:~$ dmesg | grep tuner
cjp@cjp-desktop:~$ 
```

---

### Post by am4tor on 2010-10-04
Hi,
sorry if i didn't was enough clear about the commands and the use of sudo in case of failure. After i was seing Your last post, they should be like this:

cjp@cjp-desktop:~$ uname -r 
**[COLOR=Navy]2.6.32-24-generic[/COLOR] **

cjp@cjp-desktop:~$ [COLOR=Navy]**sudo** apt-get install kernel-source-2.6.32[/COLOR][B][B][COLOR=Navy]-24-generic[/COLOR]

next:
[/B][/B]cjp@cjp-desktop:~$  [COLOR=Navy]**sudo** apt-get install kernel-headers-[/COLOR][B][COLOR=Navy]2.6.32-24-generic   
[/COLOR][/B]
[COLOR=Navy][COLOR=Black]
But the videocard _proprietary driver must be installed_ .

An example of how, is shown here:
[URL="http://ubuntuforums.org/showpost.php?p=9924471&postcount=6"]http://ubuntuforums.org/showpost.php?p=9924471&postcount=6
[/URL]

At least [/COLOR][/COLOR]re run  [B]lspci -v .

[/B][COLOR=Navy][COLOR=Black]The source of inspiration is this post:"[/COLOR][/COLOR][http://www.linuxquestions.org/questions/debian-26/no-saa7134-dvb-c-so-cannot-modify-firmware-for-dvb-t-658374/](http://www.linuxquestions.org/questions/debian-26/no-saa7134-dvb-c-so-cannot-modify-firmware-for-dvb-t-658374/)[COLOR=Navy][COLOR=Black]"
which is for Gentoo, but maybe will be useful for us too.
[/COLOR][/COLOR]

---

### Post by cpcpcp on 2010-10-04
> **am4tor said:**
> Hi,
sorry if i didn't was enough clear about the commands and the use of sudo in case of failure. After i was seing Your last post, they should be like this:

cjp@cjp-desktop:~$ uname -r 
**[COLOR=Navy]2.6.32-24-generic[/COLOR] **

cjp@cjp-desktop:~$ [COLOR=Navy]**sudo** apt-get install kernel-source-2.6.32[/COLOR][B][B][COLOR=Navy]-24-generic[/COLOR]

next:
[/B][/B]cjp@cjp-desktop:~$  [COLOR=Navy]**sudo** apt-get install kernel-headers-[/COLOR][B][COLOR=Navy]2.6.32-24-generic   
[/COLOR][/B]
[COLOR=Navy][COLOR=Black]
But the videocard _proprietary driver must be installed_ .

An example of how, is shown here:
[URL="http://ubuntuforums.org/showpost.php?p=9924471&postcount=6"]http://ubuntuforums.org/showpost.php?p=9924471&postcount=6
[/URL]

At least [/COLOR][/COLOR]re run  [B]lspci -v .

[/B][COLOR=Navy][COLOR=Black]The source of inspiration is this post:"[/COLOR][/COLOR][http://www.linuxquestions.org/questions/debian-26/no-saa7134-dvb-c-so-cannot-modify-firmware-for-dvb-t-658374/](http://www.linuxquestions.org/questions/debian-26/no-saa7134-dvb-c-so-cannot-modify-firmware-for-dvb-t-658374/)[COLOR=Navy][COLOR=Black]"
which is for Gentoo, but maybe will be useful for us too.
[/COLOR][/COLOR]

You are very patient.

The result of your first suggestion in this last post is nothing!

```
[cjp@cjp-desktop:~$ sudo apt-get install kernel-source-2.6.32-24-generic
[sudo] password for cjp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-source-2.6.32-24-generic
```The result of **lspci -v **was in my last post - in the Code Section it started 19 lines down 
- sorry about it being obscure

The Nvidia is in place and, as far as I know, in use.
Mind you I truly cannot tell for certain <g> but it is reported as such and the Nvidia X Server Settings whatever they might be is now available.

Looking at the link things you pointed me at don't I only want thses kernel things if I am going to be suicidal and compile things:(

---

### Post by am4tor on 2010-10-05
Last  is to check in Synaptic what repos are installed , activate if weren't the universe, multiverse and main-restricted (eventualy the backports) 
after that install the medibuntu repo 
as described in Lucid-User-Guide: [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Repositories_using_Synaptic_Package_Manager](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Repositories_using_Synaptic_Package_Manager)
.
After that , update Synaptic and check if the tv works.

---

### Post by halj32 on 2010-10-13
try using Kaffeine to scan for channels & watch tv, worked for me when a lot of other player wouldnt.

---

