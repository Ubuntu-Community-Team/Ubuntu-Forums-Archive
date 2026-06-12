---
title: "Can't find soundcard after fresh 10.04 install"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by zeezam on 2010-07-30
$ aplay -l
aplay: device_list:223: no soundcards found...


Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 836c
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

No hardware listed under Sound Preferences.
Any ideas?

---

### Post by cariboo on 2010-07-31
Does your sound card show when you run:

```
lspci
```

and

```
sudo lshw -C multimedia
```

---

### Post by alistairwitt on 2010-08-04
I have the same problem. lspci gives my device as:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)


and sudo lshw -C multimedia gives my device as:

 *-multimedia
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:e8181000-e81811ff memory:e8182000-e81820ff



No devices are listed under the hardware tab in Sound Preferences. Under the output tab there is a "Dummy Output, Stereo" listing. Any ideas here?

---

### Post by zeezam on 2010-08-10
> **cariboo907 said:**
> Does your sound card show when you run:

```
lspci
```

$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


```
sudo lshw -C multimedia
```

*-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:f9ff4000-f9ff7fff

---

### Post by mastablasta on 2010-08-10
YES! I am not the only one with Intel HDA issue.
 
I solved it by upgrading alsa, only to have the whole thing broken a few days later on and even today it's not working as it should and it even managed to crash the system. 
 
only in my case the card showed up but dissapeared after some time.

---

### Post by zeezam on 2010-08-10
> **mastablasta said:**
> YES! I am not the only one with Intel HDA issue.
 
I solved it by upgrading alsa, only to have the whole thing broken a few days later on and even today it's not working as it should and it even managed to crash the system. 
 
only in my case the card showed up but dissapeared after some time.

How did you upgrade alsa?

---

### Post by zeezam on 2010-08-10
The problem was solved with some updates I ran today.

---

