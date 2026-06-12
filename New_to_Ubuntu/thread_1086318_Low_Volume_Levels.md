---
title: "Low Volume Levels"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by expatCM on 2009-03-03
The volume level is either poor or terrible …...  so I am looking for suggestions of how to increase the default.  Any ideas of how to proceed appreciated :)

I get the best sound level from either Alsa or Pulse (system / preferences / sound / test). That means you can hear it if you are quiet.  Both OSS and Asus Virtuoso 200 are there but you need to be within 1 cm of the speaker to know.

I have looked round /etc/pulse/daemon.conf but cannot see anything useful to play with.

The following was delivered by amixer

```
Simple mixer control 'Master',0

  Capabilities: pvolume pswitch pswitch-joined

  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer

  Limits: Playback 0 - 65536

  Mono:

  Front Left: Playback 65536 [100%] [on]

  Front Right: Playback 65536 [100%] [on]

  Rear Left: Playback 65536 [100%] [on]

  Rear Right: Playback 65536 [100%] [on]

  Front Center: Playback 65536 [100%] [on]

  Woofer: Playback 65536 [100%] [on]

Simple mixer control 'Capture',0

  Capabilities: cvolume cswitch cswitch-joined

  Capture channels: Front Left - Front Right

  Limits: Capture 0 - 65536

  Front Left: Capture 65536 [100%] [on]

  Front Right: Capture 65536 [100%] [on]


```

aplay correctly identifies the sound card
```

**** List of PLAYBACK Hardware Devices ****

card 0: D2X [Xonar D2X], device 0: Analog [Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: D2X [Xonar D2X], device 1: Digital [Digital]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


```

and /etc/moeprobe.d/alsa-base may be helpful but I cannot make much sense of it

```
# autoloader aliases

install sound-slot-0 /sbin/modprobe snd-card-0

install sound-slot-1 /sbin/modprobe snd-card-1

install sound-slot-2 /sbin/modprobe snd-card-2

install sound-slot-3 /sbin/modprobe snd-card-3

install sound-slot-4 /sbin/modprobe snd-card-4

install sound-slot-5 /sbin/modprobe snd-card-5

install sound-slot-6 /sbin/modprobe snd-card-6

install sound-slot-7 /sbin/modprobe snd-card-7



# Cause optional modules to be loaded above generic modules

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }

install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }

install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }

install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }

# Cause optional modules to be loaded above sound card driver modules

install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }

install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }



# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)

install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }



# Load snd-seq for devices that don't have hardware midi;

#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for

#   non-Creative Labs PCI hardware

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }

# Prevent abnormal drivers from grabbing index 0

options bt87x index=-2

options cx88_alsa index=-2

options saa7134-alsa index=-2

options snd-atiixp-modem index=-2

options snd-intel8x0m index=-2

options snd-via82xx-modem index=-2

options snd-usb-audio index=-2

options snd-usb-usx2y index=-2

options snd-usb-caiaq index=-2

# Ubuntu #62691, enable MPU for snd-cmipci

options snd-cmipci mpu_port=0x330 fm_port=0x388

# Keep snd-pcsp from beeing loaded as first soundcard

options snd-pcsp index=-2

```

---

### Post by asmoore82 on 2009-03-03
I would say ```
alsamixer
``` and be sure to play with the Mute settings 'm' and 'up' and 'down' arrows on the special controls that don't have volume sliders.

---

### Post by expatCM on 2009-03-03
already been there ...  but thanks for the suggestion.  I think amixer is a text summary of the alsamixer gui ........ but I have tried to move things about ......

---

### Post by ntrgc89 on 2009-03-03
Check your PCM sliders. I was having audio issues on my T400 where I just heard some crackles and pops at full volume, and I just pushed the PCM sliders (from the volume bar on my gnome-panel) up and I got sound.

---

### Post by expatCM on 2009-03-04
I think that sound settings must vary a lot .... I do not see any PCM Sliders.......

---

### Post by expatCM on 2009-03-04
Not the answer by any means but there is a work around......

This does not affect the system sounds levels, only the media player.

There is a player called smplayer, I think it is a pretty front end for mplayer.  Works well.

In the settings you can change the default sound output to some astronomical value.  I increased mine to 750 and at least I now have sound that I can hear.  

When I find the solution I must remember to put this back to the default or there will be a rude awakening.

---

### Post by kansasnoob on 2009-03-04
Install gnome-alsamixer either from synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Look at mine:

[ATTACH]105308[/ATTACH]

[ATTACH]105309[/ATTACH]

Especially notice the first 3 and last 4 (VIA) toggles and external amp if that applies.

---

### Post by LowSky on 2009-03-04
PCM should definatly be an option from alsamixer
could you do us a favor and post your hardware with this command

```
lspci -v
```

---

### Post by expatCM on 2009-03-05
Installed gnome-alsamixer ....  the option to select an external amp I guess is nice but I do not seem to have that...  I do not seem to have anything like what you see.  The screenshot is what I have ..

---

### Post by expatCM on 2009-03-05
output of lspci -v is as below

```
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 8353
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [9c] HyperTransport: #1a
	Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 8353
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=8]
	I/O ports at 8000 [size=4]
	I/O ports at 7000 [size=16]
	Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f7fff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f7ffa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ff9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation Device 0641 (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82be
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fbe80000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [60] Express PCI/PCI-X Bridge, MSI 00
	Capabilities: [100] Power Budgeting <?>
	Kernel modules: shpchp

03:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Device 82b7
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at d800 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: AV200
	Kernel modules: snd-virtuoso

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 82c6
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f6ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 81-68-10-ec-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by swoody on 2009-03-05
> **expatCM said:**
> I think that sound settings must vary a lot .... I do not see any PCM Sliders.......

My PCM sliders were not shown by default, either. When you right-click your volume control panel icon, select 'Open Volume Control' and then click on 'Preferences', and then check the box for PCM. Then it should show your PCM sliders in Volume Control next to Master. I have to make sure my PCM volume is maxed out, or my videos are very quiet. 

Let me know if this helps you out at all :)

---

### Post by expatCM on 2009-03-05
nope ....  cannot see the PCM sliders at all.  The image shows the options I have in preferences.  I just deselected IEC958 ... no idea what it is so perhaps it should go.  I also wonder if the Analog Loopback should also be deselected, also on the basis of not having a clue what it does ...

---

### Post by ex-wirecutter on 2009-03-05
May I ask , does it make any difference if the external amplifier box is ticked ?

---

### Post by HousieMousie2 on 2009-03-24
Um, this is probably WAY off base and since this thread hasn't seen any action in two weeks... may be a waste of time, but...

I have read some issues with the ASUS Xonar series power plug that if it is even the tiniest bit loose then you can end up with dramatically decreased sound levels.

If that is the case with your machine/card... you might get some tiny zip ties (panduits) to hold that puppy in tight.

---

### Post by expatCM on 2009-03-24
May not be off base though ........  well worth exploring ......  thank you for making the post :)

---

### Post by HousieMousie2 on 2009-03-27
You're most welcome.  If you are still having problems be sure you keep posting, eventually someone with the right answer will find you.

Best of luck!

---

### Post by expatCM on 2009-03-28
Well I just booted the system from the 9.04 beta.  I would not call the volume levels brilliant by any means but they are a LOT improved.

So it is decision time .....  do I press the upgrade button and see what happens on the assumption that I will have more settings manageable than from the live CD or do I fresh install.....  Might be smarter to wait for a month ....

---

### Post by expatCM on 2009-03-29
HousieMousie2 -- you appear to have had a good idea .....  I just took out the soundcard and sprayed the contacts with a cleaner (to motherboard and power) and then put it back together.

The result is an instant change, whereas I needed to run volume at 100% and listen carefully before, now I can listen at only 25% without issue.  5:1 sound in use but the side speakers are dead.  Not sorted that one out yet but delighted that I have the volume now..........

So I think my strategy will be to wait for Ubuntu 9.04 to be released in a month and then reinstall and explore ..............

---

### Post by HousieMousie2 on 2009-03-31
Excellent, glad to hear you have it (mostly) fixed!

---

### Post by Mozzer on 2009-04-09
Hi, I've got 9.04 running on my Acer Aspire 5710 and like some other people have been saying, the master volume is very low up to about 50% then increases exponentially after that. However the PCM volume control seems to be linear and works as you would expect. Is there any way to fix this... or is there some way of making the volume control PCM by default?

---

### Post by corpsehacker on 2009-04-09
One word. Alsamixer. I had the same problem as you one time and I went into Alsamixer, turned everything up to 100 and it was perfect.

---

