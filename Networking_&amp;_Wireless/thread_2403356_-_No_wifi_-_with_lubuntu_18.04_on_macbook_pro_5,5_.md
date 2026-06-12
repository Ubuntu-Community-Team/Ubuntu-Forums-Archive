---
title: "- No wifi - with lubuntu 18.04 on macbook pro 5,5 mid 2009"
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by onkeleugen on 2018-10-10
Hi there dear ubuntu community...

Im completely new in the linux-world, no clue about it - but excited to learn about it!
 My macbook was slow with 'el capitan' os (pro model mid 2009) and I got kind of bored of apple anyways. So I prepared lubuntu on a usb-stick and installed it on my macbook - lubuntu only, the rest is gone. I thought about it and did it right away, a fresh start, woop woop! I dont feel attached to any software or data on my computer, or this is the experiment, maybe ill find out now, that I might am with one or the other thing - we ll see :) - 
lubuntu works pretty fine I think, definately faster than my el capitan os, although 2 issues I have Im struggling with which are kind of urgent:

1) how do I get my wifi connection working on lubuntu 18.04 with this mentioned macbook?

and

2) my external hard drive gets detected and i can open some folders and files, but for example for the backup folders created with time machine on macOS i have "no authorization"...can we do something about this? or is it gonna be a fresh start to the fullest extend without any data from the past? :)

I say thank you very much for any kind of help in advance.

See ya soon!

Saludos,
uncle E.

---

### Post by praseodym on 2018-10-10
Hi,

lets check the hardware in use:

Open a terminal with CTRL+ALT+T and show the outputs of these commands
```

lspci -nnk
lsusb
lsmod
```
Does the LAN connection work?

---

### Post by onkeleugen on 2018-10-11
Hi, thank you for your quick reply.
I'm right now online, using lubuntu with this hardware - connected with ethernet cable.
here are the outputs, thank you very much:

```
onkeleugen@Melody:~$ **lspci -nnk**
00:00.0 Host bridge [0600]: NVIDIA Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: NVIDIA Corporation MCP79 LPC Bridge [10de:0aae] (rev b3)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
00:03.1 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: NVIDIA Corporation MCP79 SMBus [10de:0aa2] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c_nforce2, nv_tco
00:03.3 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.4 RAM memory [0500]: NVIDIA Corporation MCP79 Memory Controller [10de:0a98] (rev b1)
    Subsystem: NVIDIA Corporation iMac 9,1 [10de:cb79]
00:03.5 Co-processor [0b40]: NVIDIA Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
00:04.0 USB controller [0c03]: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: ohci-pci
00:04.1 USB controller [0c03]: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: ehci-pci
00:06.0 USB controller [0c03]: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: ohci-pci
00:06.1 USB controller [0c03]: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: ehci-pci
00:08.0 Audio device [0403]: NVIDIA Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:09.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
00:0b.0 SATA controller [0106]: NVIDIA Corporation MCP79 AHCI Controller [10de:0ab9] (rev b1)
    Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:10.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
    Kernel modules: shpchp
00:15.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 PCI bridge [0604]: NVIDIA Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C79 [GeForce 9400M] [10de:0863] (rev b1)
    Subsystem: Apple Inc. C79 [GeForce 9400M] [106b:00b9]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
03:00.0 Network controller [0280]: Broadcom Limited BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
04:00.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW643 [TrueFire] PCIe 1394b Controller [11c1:5901] (rev 07)
    Subsystem: LSI Corporation FW643 [TrueFire] PCIe 1394b Controller [11c1:5900]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci
```
```
onkeleugen@Melody:~$ lsusb
Bus 002 Device 003: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
onkeleugen@Melody:~$lsmod
Module                  Size  Used by
bnep                   20480  2
nls_iso8859_1          16384  1
joydev                 24576  0
snd_hda_codec_cirrus    20480  1
snd_hda_codec_generic    73728  1 snd_hda_codec_cirrus
applesmc               20480  0
input_polldev          16384  1 applesmc
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
b43                   413696  0
btusb                  45056  0
bcma                   57344  1 b43
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  26 btrtl,btintel,bnep,btbcm,btusb
mac80211              778240  1 b43
ecdh_generic           24576  1 bluetooth
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
input_leds             16384  0
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
bcm5974                16384  0
cfg80211              622592  2 b43,mac80211
shpchp                 36864  0
snd_hda_intel          40960  3
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_cirrus
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_cirrus
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_timer              32768  1 snd_pcm
snd                    81920  13 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_generic,snd_hda_codec_cirrus,snd_pcm
soundcore              16384  1 snd
sbs                    20480  0
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
sbshc                  16384  1 sbs
industrialio           69632  2 acpi_als,kfifo_buf
mac_hid                16384  0
sch_fq_codel           20480  2
apple_bl               16384  0
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_apple              16384  0
hid_generic            16384  0
uas                    24576  0
usb_storage            69632  1 uas
hid_appleir            16384  0
usbhid                 49152  0
hid                   118784  4 hid_appleir,hid_generic,usbhid,hid_apple
nouveau              1716224  2
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
video                  45056  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                   106496  1 nouveau
firewire_ohci          40960  0
drm_kms_helper        172032  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
firewire_core          65536  1 firewire_ohci
forcedeth              69632  0
drm                   401408  5 nouveau,ttm,drm_kms_helper
ssb                    57344  1 b43
crc_itu_t              16384  1 firewire_core
ahci                   36864  2
libahci                32768  1 ahci
i2c_nforce2            16384  0
```

---

