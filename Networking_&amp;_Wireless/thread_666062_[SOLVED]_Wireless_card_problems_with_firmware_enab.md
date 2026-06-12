---
title: "[SOLVED] Wireless card problems with firmware enabled"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by DUDE_2000 on 2008-01-12
After installing ubuntu on my computer, the wireless drivers don't work. I have tried the howto in the stickies of this section, and it didn't work. The firmware is installed, and (I think) ndiswrapper is working.
It detects the card in the restricted drivers manager (it says I need the broad com firmware, it is enabled) and in the hardware monitor. what is wrong, as this is the only way to acess the internet from my room.

The card and my network works, as I can access it from vista.

---

### Post by tgalati4 on 2008-01-13
Post the output of:

>lspci -vv

and

>lsmod

and

>ifconfig

and

>iwconfig

---

### Post by DUDE_2000 on 2008-01-13
lsmod
Module                  Size  Used by
ipv6                  317192  10 
nls_iso8859_1           6528  1 
nls_cp437               8192  1 
vfat                   16128  1 
fat                    60208  1 vfat
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_userspace       6048  0 
cpufreq_conservative     9608  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
ac                      7304  0 
dock                   12264  0 
sbs                    21520  0 
container               6400  0 
video                  21140  0 
button                 10400  0 
battery                12424  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4608  0 
i2c_nforce2             7808  0 
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
k8temp                  7680  0 
psmouse                45596  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
serio_raw               9092  0 
i2c_core               30208  1 i2c_nforce2
evdev                  13056  3 
ext3                  146576  2 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod
sd_mod                 32512  9 
usb_storage            81728  1 
ata_generic             9988  0 
libusual               22824  1 usb_storage
sata_nv                24068  5 
libata                138928  2 ata_generic,sata_nv
scsi_mod              172856  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
ohci_hcd               25092  0 
forcedeth              55048  0 
amd74xx                17328  0 [permanent]
ide_core              141200  2 usb_storage,amd74xx
ehci_hcd               40076  0 
usbcore               161584  5 usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  5 
apparmor               47008  0 
commoncap               9472  1 apparmor

---

### Post by DUDE_2000 on 2008-01-13
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:B9:8D:2E:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by DUDE_2000 on 2008-01-13
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by DUDE_2000 on 2008-01-13
lspci -vv
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 255
        Region 0: I/O ports at fc00 [size=64]
        Region 4: I/O ports at 1c00 [size=64]
        Region 5: I/O ports at f400 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: fde00000-fdefffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at ec00 [size=8]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 23
        Region 0: I/O ports at 09f0 [size=8]
        Region 1: I/O ports at 0bf0 [size=4]
        Region 2: I/O ports at 0970 [size=8]
        Region 3: I/O ports at 0b70 [size=4]
        Region 4: I/O ports at d800 [size=16]
        Region 5: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 23
        Region 0: I/O ports at 09e0 [size=8]
        Region 1: I/O ports at 0be0 [size=4]
        Region 2: I/O ports at 0960 [size=8]
        Region 3: I/O ports at 0b60 [size=4]
        Region 4: I/O ports at c400 [size=16]
        Region 5: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e4000000-ebffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fdb00000-fdbfffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

01:05.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company NX9500 Built-in Wireless
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 255
        Region 0: Memory at fdffc000 (32-bit, non-prefetchable) [size=8K]

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a61
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at bc00 [size=128]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=64M]
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at ea000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e8000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by GSF1200S on 2008-01-13
Just so you know, you can post all the commands in one reply. Just use the quote function in the "post reply" window...

First off, I dont use the firmware on my second lappie. I use ndiswrapper. You mentioned both, so now its important for us to determine which you are using. Only one can be used at a time. Please post the results of the following run in a terminal:

```
ndiswrapper -l
```

Installing ndiswrapper in itself will not make the wireless card work. You need to install the windows wireless driver into it, and then update modprobe and such..

So, lets say you go download the windows driver from broadcoms website or grab it from the drivers cd that came with the computer. You would do the following:

1) Lets say the windows wireless driver is on your desktop. You would put the following into the terminal:

```
sudo ndiswrapper -i /home/user/Desktop/bcmdriver.inf
``` (of course substituting username with your username and bcmdriver.inf with the name of the driver to use, respectively.)

Then, check to make sure its installed properly:

```
ndiswrapper -l
```

Then, write the changes to the appropriate places:

```
sudo ndiswrapper -m
```
```
sudo ndiswrapper -mi
```

Restart the computer, and all will be good. Remember to push the wireless button though- I thought it had failed because the light didnt come on. As I cursed, I pressed the button in futility and magically the bugger lit right up! Has worked great ever since ;)

---

### Post by DUDE_2000 on 2008-01-13
ndiswrapper -1 comes out with:
Error: no ndiswrapper utils found

---

### Post by DUDE_2000 on 2008-01-13
a note, this is a desktop, (i don't have the type of money for a laptop)

---

### Post by GSF1200S on 2008-01-13
> **DUDE_2000 said:**
> a note, this is a desktop, (i don't have the type of money for a laptop)

Go grab the windows wireless driver from their website. Then do as I put above to install the driver and mount the ndiswrapper 'program' (or module) at bootup. Report back with what the terminal reports and any problems you may have. Its a fairly easy process, so much so that I managed to confuse myself the first time ;)

---

### Post by DUDE_2000 on 2008-01-13
how do i mount ndiswrapper?

---

### Post by GSF1200S on 2008-01-14
> **DUDE_2000 said:**
> how do i mount ndiswrapper?

In my first post I included the commands necessary to add the module so it will start when you boot the computer- sorry i wasnt more clear about this :)

ndiswrapper --help

will kind of show you what the different options do.

After youve installed the driver as I listed in my first post, those other commands will actually update the files necessary and then a reboot will be all that is needed.

You may need to try a different wireless driver if the one your using doesnt work...

good luck ;)

---

### Post by DUDE_2000 on 2008-01-14
thanks, I may end up swithching to somethig like opensuse.
I tried pclos gnome last night, and while it was by far the ugliest distro I've seen, it discovered, and enabled the card right away.

---

### Post by GSF1200S on 2008-01-14
> **DUDE_2000 said:**
> thanks, I may end up swithching to somethig like opensuse.
I tried pclos gnome last night, and while it was by far the ugliest distro I've seen, it discovered, and enabled the card right away.

Whatever works for you ;) It really isnt that hard, so if all else fails, hop in the ubuntu IRC channel and get some help there.

I might suggest something based on debian, or something using apt. I recently tried Opensuse and while the distro itself is nice, the package management, er well,  for me just didnt cut it. Maybe Mepis (gaurantee your card works there) if youre not opposed to KDE...

---

### Post by DUDE_2000 on 2008-01-14
do you not have to pay for mepis?

---

### Post by kevdog on 2008-01-14
Dude -- are you in the market for a ndiswrapper guide?? 

Try this one:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by GSF1200S on 2008-01-14
> **DUDE_2000 said:**
> do you not have to pay for mepis?

Mepis is free, is based on KDE and has set every single wireless card Ive tried up out of the box on the live cd! Good distro overall...

I would consider sticking with trying to learn how to install ndiswrapper though- Ubuntu is a awesome distro when you have it operational...

---

### Post by DUDE_2000 on 2008-01-18
it looked like ndiswrapper didn't install right, but it works in mint fine. thanks!!

---

