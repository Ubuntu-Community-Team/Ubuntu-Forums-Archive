---
title: "wifi internet connection on a notebook"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by giggs76 on 2010-07-13
[COLOR=black][FONT=&quot]Hi, I have bought eeePC Notebooks  Speed MN 1020 for my two young daughters. At the first run, the system  was working properly even wifi connection. The system advised to update  Ubuntu version to LTS 10.04. Since this update, Internet connection is  only possible via wired connection. I have looked at various solution  (installation of WICD, connection to hidden internet connections,..),  nothing seems to work.[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]I have even thought of  installing Fedora which works on my PC but it is impossible to boot on  an USB key![/FONT][/COLOR]
  [COLOR=black][FONT=&quot]I am absolute beginner so  help![/FONT][/COLOR]

---

### Post by skyjacker on 2010-07-13
Try this... hook up to an ethernet connection and "run" the following ```
Hardware Drivers
```. This should pick an available driver for your wireless card... Mine is Broadcom STA, yours may be something else. Choose one and let it install. then you should get a wireless icon on the top bar....... be sure to set up your wireless info.

---

### Post by anewguy on 2010-07-13
You probably lost your wireless driver in the update.

If you can hard-wire a connection, try the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

- close the terminal window

- check in System/Administration/Hardware Drivers and see if a restricted driver is listed there - if so, enable it.

- be sure to physically disconnect the hard-wire connection before seeing if wireless will work

You may need to check in network manager (on the top status bar) to be sure "Enable Wireless" is checked.

If this doesn't work, please do the following:

- open a terminal window (Applications/Accessories/Terminal

- type:

lspci <press enter>  Copy/paste the output to a reply here

lsusb <press enter>  Copy/paste the output to a reply here

lshw <press enter>  Copy the output of this into a editor window.  Remove everything that isn't under a network or wireless section, then copy/paste the output to a reply here

lsmod <press enter>  Copy/paste the output to a reply here


That should be enough to get us started.

Dave ;)

---

### Post by giggs76 on 2010-07-13
Hi Dave,
i tried all the step from your list of advises.... First of all, thank you.....

administrator@administrator-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
01:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
01:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
01:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
01:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)




administrator@administrator-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID eb1a:2771 eMPIA Technology, Inc.
Bus 001 Device 002: ID 160a:3184 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




administrator@administrator-laptop:~$ lshw
WARNING: you should run this program as super-user.
administrator-laptop     
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm pse cpufreq
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fea80000-feafffff ioport:dc80(size=8) memory:d0000000-dfffffff(prefetchable) memory:fea40000-fea7ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fe980000-fe9fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fea38000-fea3bfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:feb00000-febfffff memory:40000000-401fffff(prefetchable)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:febffc00-febffcff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:febff800-febff8ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:01:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:febff400-febff4ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:01:00.4
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:febff000-febff0ff
           *-network
                description: Ethernet interface
                product: JMC260 PCI Express Fast Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: X.X
                bus info: pci@XXXX:XX:XX.X
                logical name: eth3
                version: 02
                serial: XX:XX:XX:XX:XX:XX
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=jme driverversion=1.0.5 ip=XXX.XXX.X.XX latency=0 multicast=yes
                resources: irq:25 memory:febf8000-febfbfff ioport:ec80(size=128) ioport:e800(size=256)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:dc00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d880(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d480(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fea37c00-fea37fff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11-a/b/g
administrator@administrator-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1
ppdev                   5259  0
snd_hda_codec_realtek   203310  1
fbcon                  35102  71
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0
vgastate                8961  1 vga16fb
joydev                  8708  0
snd_hda_intel          21941  2
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0
snd_seq_oss            26726  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  285076  2
uvcvideo               56990  0
jmb38x_ms               7311  0
jme                    27953  0
drm_kms_helper         29297  1 i915
drm                   162377  3 i915,drm_kms_helper
vt6656_stage          199522  0
intel_agp              24119  2 i915
soundcore               6620  1 snd
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
sdhci_pci               5470  0
mii                     4381  1 jme
memstick                8237  1 jmb38x_ms
psmouse                63245  0
i2c_algo_bit            5028  1 i915
sdhci                  15462  1 sdhci_pci
serio_raw               3978  0
led_class               2864  1 sdhci
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0
parport                32635  2 ppdev,lp


Thanks a lot.....

Guillaume

---

### Post by anewguy on 2010-07-17
I've been doing a lot of online research regarding a driver for your wireless device (usb manufacturer/deviceid 160a:3184) which is a VIA integrated USB wireless adapter VNT6656.

There was a lot of talk late last year and early this year on launchpad for problems with the driver and (1) 64-bit OS's and (2) certain kernel versions.

The link below is to the download for your driver:

[http://www.wireless-driver.com/download/other/VIA-VT6656-WLAN-Module-Windows-XP-Driver.htm]("http://www.wireless-driver.com/download/other/VIA-VT6656-WLAN-Module-Windows-XP-Driver.htm")

You'll see the link information for the Windows XP driver first, and then a small mention of the Linux driver ( a 15+mb download).

You should start by downloading that and then clicking on the file to unpack it.  It may be a source file, in which case there is hopefully a readme file included.  Usually this involves using the command line, changing default directory to the directory the file unpacked to, then running ./configure, make and make install (as sudo....), but definitely look for a readme for more specific instructions.  If you have any questions just post back.  I'm currently on Windows, and I don't have your adapter, so I'll have to go by what you see.

If the readme does say you need to do the make, etc., then you should first go to Synaptic Package Manager and install build-essential first.

Dave ;)

---

