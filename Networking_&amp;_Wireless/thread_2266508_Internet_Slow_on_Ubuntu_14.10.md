---
title: "Internet Slow on Ubuntu 14.10"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by Ira_Lee on 2015-02-23
Hello, I just installed Ubuntu 14.10 on my HP Pavillion dm1 and the first thing I noticed was that my internet connection became very slow and unstable. I read some other threads concerning this topic, but I could not find a solution that worked for me.

I am very new to Ubuntu and Linux in general, but can anyone help me out with my problem? Please and thank you!! :)

- Ira

---

### Post by Visual Echo on 2015-02-23
Okay... I think you're talking about wi-fi and not the ethernet connector.  According to HP ( [http://www.hp.com/ctg/Manual/c02214672.pdf](http://www.hp.com/ctg/Manual/c02214672.pdf) ), you've got a mini-PCI wireless module.  I've had an HP before, and I think they use a lot of different modules like this, we need to find out more about this module - specifically, what the number of the chip is, and then we can ensure that the driver is working okay.

You said you were new, but I'm going to have to make you use that command line thing...  what do you get when you run the command:
> lspci -v
Something in the output from that will be the wireless card. Also check:
> lsmod
which should show the drivers loaded.  This command:
> ifconfig
will show information about the network binding to the device.

Check these out, do a few web searches on any errors you find, and you're still stuck, post the important bits back here.

---

### Post by Ira_Lee on 2015-02-24
Hello! Thank you for replying! Also you are correct! It is just my wireless that is insanely slow. When I plug in my ethernet cable, I get about 55 Mbps, which is about right. Sorry I did not clarify.

I also found out that network card is Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01). I do not know if that will help.

 I am not quite sure what to make of the results. I do not see any error, but then again I am not sure where to look.

lspci -v
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f0400000-f05fffff
    Prefetchable memory behind bridge: 00000000f0600000-00000000f07fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4118 [size=8]
    I/O ports at 4124 [size=4]
    I/O ports at 4110 [size=8]
    I/O ports at 4120 [size=4]
    I/O ports at 4100 [size=16]
    Memory at f034e000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000f0100000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0349000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f0348000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 1795
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: bcma-pci-bridge

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 3387
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 2000 [size=256]
    Memory at f0104000 (64-bit, prefetchable) [size=4K]
    Memory at f0100000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

```

lsmod returned
```

Module                  Size  Used by
ctr                    13049  3 
ccm                    17731  3 
arc4                   12608  2 
snd_hda_codec_idt      63632  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_idt
snd_hda_codec_hdmi     47547  1 
brcmsmac              571212  0 
cordic                 12574  1 brcmsmac
brcmutil               15579  1 brcmsmac
mac80211              660592  1 brcmsmac
cfg80211              510218  2 brcmsmac,mac80211
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
bnep                   19543  2 
rfcomm                 69509  8 
uvcvideo               81065  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15682  1 videobuf2_core
btusb                  32448  0 
kvm                   459835  0 
snd_hda_intel          30420  7 
videodev              149725  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_controller     35152  1 snd_hda_intel
media                  21963  2 uvcvideo,videodev
snd_hda_codec         139675  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
bluetooth             446190  22 bnep,btusb,rfcomm
snd_pcm               104102  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
6lowpan_iphc           18702  1 bluetooth
snd_seq_midi           13564  0 
radeon               1416582  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
joydev                 17344  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13434  0 
snd_timer              29513  2 snd_pcm,snd_seq
k10temp                13144  0 
ttm                    89406  1 radeon
snd                    87611  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
sp5100_tco             13999  0 
drm_kms_helper         61627  1 radeon
bcma                   52443  2 brcmsmac
i2c_piix4              22159  0 
drm                   310919  6 ttm,drm_kms_helper,radeon
soundcore              15052  2 snd,snd_hda_codec
shpchp                 37040  0 
wmi                    19193  1 hp_wmi
i2c_algo_bit           13406  1 radeon
hp_accel               26034  0 
lis3lv02d              20156  1 hp_accel
video                  20128  0 
input_polldev          14607  1 lis3lv02d
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ums_realtek            18045  0 
uas                    23215  0 
usb_storage            66398  2 uas,ums_realtek
psmouse               106593  0 
r8169                  71471  0 
mii                    13934  1 r8169
ahci                   34062  2 
libahci                32424  1 ahci

```

ifconfig returned
```
eth0      Link encap:Ethernet  HWaddr ec:9a:74:42:c8:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:145687 (145.6 KB)  TX bytes:145687 (145.6 KB)

wlan0     Link encap:Ethernet  HWaddr e4:d5:3d:08:04:fb  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fe08:4fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31684483 (31.6 MB)  TX bytes:2091019 (2.0 MB)

```

Thank you again!
- Ira Lee

---

### Post by Ira_Lee on 2015-02-27
Hello, sorry for bumping this thread, but I really need help on this! :(

---

