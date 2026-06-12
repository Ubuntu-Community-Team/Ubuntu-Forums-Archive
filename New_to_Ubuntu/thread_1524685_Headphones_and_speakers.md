---
title: "Headphones and speakers"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by rogeliodelarosa97 on 2010-07-05
hello i have  ubuntu desktop 32 bit 10.4 for about 2 weeks and the headphones mix  with the built in stereo for example you can hear the headphones but you can hear the built in stereo to playing the media outside plz help!!!!
my sound card is 

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4700000 irq 22
plz i am really new so explain with detail

---

### Post by s.fox on 2010-07-05
Hello,

Is this on a laptop?  If so can you provide make and model please :)

Could you also open a terminal and submit the following command:

```
lspci -v
```

-Silver Fox

---

### Post by rogeliodelarosa97 on 2010-07-05
i put in the command and it said

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Memory at d2500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 50e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 50c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 50a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d4705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d3700000-d46fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d14fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2600000-d36fffff
	Prefetchable memory behind bridge: 00000000d1500000-00000000d24fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 5040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d4705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at d4705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: medium devsel, IRQ 11
	Memory at d4706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: fast devsel, IRQ 11
	Memory at d4704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at 3000 [size=256]
	Memory at d0410000 (64-bit, prefetchable) [size=4K]
	Memory at d0400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d0420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 303f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k
adn yes it is a laptop

---

### Post by s.fox on 2010-07-06
Hello,

Looks like its a hp laptop and using intel chipset.

I would have a look at [this]("http://ubuntuforums.org/showthread.php?t=907759") thread ( post #4 may be the approach you will need to take )

Sorry I cannot assist further.

-Silver Fox

---

### Post by lidex on 2010-07-07
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by mid_life_crisis on 2010-07-22
I have the identical problem to the OP.
My computer is a Compaq Laptop with Lenovo Audio.
I've tried adding the line
options snd-hda-intel model=laptop-hp
with and without the "-hp".
I've also tried changing the "intel" to "lenovo".
I still get the same interface listing only the speakers.
Any suggestions?
I'm running live off a USB stick.
This is the closest I've come to getting a Linux installation running properly in years of trying off and on.  I really don't want to have to drop it for another year when I'm so close.

---

### Post by lidex on 2010-07-23
> **mid_life_crisis said:**
> I have the identical problem to the OP.
My computer is a Compaq Laptop with Lenovo Audio.
I've tried adding the line
options snd-hda-intel model=laptop-hp
with and without the "-hp".
I've also tried changing the "intel" to "lenovo".
I still get the same interface listing only the speakers.
Any suggestions?
I'm running live off a USB stick.
This is the closest I've come to getting a Linux installation running properly in years of trying off and on.  I really don't want to have to drop it for another year when I'm so close.

Well the OP isn't using the thread so have at it. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by mid_life_crisis on 2010-07-23
Thanks for the quick response.  I'll do that tonight when I get home.

---

### Post by mid_life_crisis on 2010-07-25
Compaq Presario CQ60 Laptop

```
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

```
```
Codec: Conexant ID 5067

```

---

### Post by lidex on 2010-07-25
When was the last time you updated your system? Try this:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by mid_life_crisis on 2010-07-25
> **lidex said:**
> When was the last time you updated your system? Try this:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

I'm currently running off USB.  The update failed due to a disk space issue.  It claimed zero bytes left but the disk analyzer shows it as half full.  I am almost willing to assume that this is something to do with the running from USB thing, but I'm still reluctant to take the plunge again and install it until I know it will all work.

---

### Post by lidex on 2010-07-25
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by mid_life_crisis on 2010-07-25
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

The only card in the list is Intel.  I have a Conexant Pebble High Definition Audio SmartAudio.  If I do F6 it can't find the directory.

---

### Post by lidex on 2010-07-25
OK. Makes it easier to choose when only one choice. How is the audio?

---

### Post by mid_life_crisis on 2010-07-26
> **lidex said:**
> OK. Makes it easier to choose when only one choice. How is the audio?

No change.

---

