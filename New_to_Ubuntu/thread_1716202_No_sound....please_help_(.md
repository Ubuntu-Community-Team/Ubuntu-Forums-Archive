---
title: "No sound....please help :("
date: 2011-03-28
forum: New to Ubuntu
---

### Post by DeathGrind on 2011-03-28
I have been trying to get the sound working on my msi m6275 laptop for a few days now.  I can't think of anything else so i am now reaching out for some help/support from the community.  
I just reinstalled ubuntu 10.10, so i have a clean install ready to troubleshoot.  
Please help me get my sound working. 
What is the first step i should take?  I can not remember the command to run to post the info about my sound card, so that would be a good place to start.

Thank you.

---

### Post by goldaryn on 2011-03-28
When I installed 10.10 the first thing I had to do was go to the speaker icon in the top right, click it and press "Unmute", and then it worked.

---

### Post by mastablasta on 2011-03-28
Command is
 
lspci
 
Have a look here on how to propperly troubleshoot sound and also some solutions: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by DeathGrind on 2011-03-28
well i know the sounds not muted.  but thanks for the suggestion.  i have tried a number of things to fix this with no luck.

---

### Post by DeathGrind on 2011-03-28
> **mastablasta said:**
> Command is
 
lspci
 
Have a look here on how to propperly troubleshoot sound and also some solutions: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

thanks looking into it.

---

### Post by DeathGrind on 2011-03-28
this is what i got when ruuning the cmd.  hopefully it will help someone figure out a way to help me. 


nate@nate-M6275:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
06:00.1 Audio device: ATI Technologies Inc RV710/730
nate@nate-M6275:~$

---

### Post by DeathGrind on 2011-03-28
more info....


nate@nate-M6275:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nate@nate-M6275:~$ 





nate@nate-M6275:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fdefec00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at fdef8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000cdf00000-00000000cdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe000000-fe9fffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ac00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fdeff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=32]
	Memory at fdeff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: medium devsel, IRQ 15
	Memory at fdeff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Physical Slot: 0-1
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at c800 [size=256]
	Memory at fdfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at cdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1067
	Physical Slot: 0-3
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

06:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 1016
	Physical Slot: 0
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at e000 [size=256]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

06:00.1 Audio device: ATI Technologies Inc RV710/730
	Subsystem: Micro-Star International Co., Ltd. Device aa38
	Physical Slot: 0
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at febec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

nate@nate-M6275:~$

---

### Post by goldaryn on 2011-03-28
What kind of jack are your speakers plugged into?

It looks like Ubuntu is detecting 3 possible ways to output sound: through laptop digital, laptop analog, and through your ATI video card (mine also does this).

It's worth checking that the default output for sound is the one that things are plugged into.. I imagine that the one you probably want to set as default is laptop analog (i.e. Intel analog)

---

### Post by DeathGrind on 2011-03-28
> **goldaryn said:**
> What kind of jack are your speakers plugged into?

It looks like Ubuntu is detecting 3 possible ways to output sound: through laptop digital, laptop analog, and through your ATI video card (mine also does this).

It's worth checking that the default output for sound is the one that things are plugged into.. I imagine that the one you probably want to set as default is laptop analog (i.e. Intel analog)

Just trying to get the internal laptop speakers to work.  I have tried all options in sound preferences, still no sound.

Im stumped.

---

### Post by mastablasta on 2011-03-28
Your card 
 
```
 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


```
```
Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]

```
 
is clearly recognised and as i know the 10.10 uses latest stable ALSA (linux drivers). maybe a module is missing?
 
Is there a card in sound preferences? Can you change it's output to analog stereo duplex?
 
Have you tried with 
 
```
alsamixer
``` 
 
in terminal? run it and if you can increase output on all available outputs and inputs to max. then try it out again.
 
HD intel is giving me hard time as well though it got better on upgrade to 10.10.
 
Also can you post the output of this command:
 
```
dmesg
```
 
it's like boot log and should show any mounting errors on boot.

---

### Post by DeathGrind on 2011-03-28
> Also can you post the output of this command:

Code:
dmesg
it's like boot log and should show any mounting errors on boot.

errrr...when I try to post output the forum says i am linking to too many images....weird

---

### Post by DeathGrind on 2011-03-28
since it wont let me post the dmesg output I saved it as an attachment.

---

### Post by DeathGrind on 2011-03-28
here are some screen caps to show that the sound card indeed is there.....it just doesn't work :(

Its late here, and i am tired.  Going to call it a night, get back to this later.  Thanks for the help, i really appreciate it.

---

### Post by DeathGrind on 2011-03-28
Back awake.  Ready to try to get this working if anyone would provide assistance.  Thank you.

---

