---
title: "Mic is not working under ubuntu 10.04 64-bit"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-03-19
Hi, 

I am using ubuntu 10.04 under 10.04 machine. The mic (internally or line-in) is not working. Here I posted the related hardware of the machine after invoking "lspci":

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

Any ideas?

---

### Post by cariboo on 2011-03-19
I found with my Compaq Mini 110 netbook that the mic volume was not set high enough to be useful. I used alsamixer to adjust the volume. 

Open an Applications->Accessories->Termianl and type:

```
alsamixer
```

use the arrow keys to navigate and change volume levels. Once you have set the mic volume to what you want, press esc to exit, then in the same terminal type:

```
sudo alsactl store
```

to same your settings.

---

### Post by alfa_80 on 2011-03-19
> **cariboo907 said:**
> I found with my Compaq Mini 110 netbook that the mic volume was not set high enough to be useful. I used alsamixer to adjust the volume. 

Open an Applications->Accessories->Termianl and type:

```
alsamixer
```use the arrow keys to navigate and change volume levels. Once you have set the mic volume to what you want, press esc to exit, then in the same terminal type:

```
sudo alsactl store
```to same your settings.


To my knowledge, everything is already up to the maximum, but it's still problematic. The alsamixer screenshot is taken as in the attachment.

---

### Post by ajgreeny on 2011-03-19
The screenshot does not show your microphone, so is that also set high enough, or is it perhaps muted (showing MM beneath the level shown) as in my screenshot, even though the level is set high.

Note that in alsamixer I have a mic-boost next to the mic, also shown in my screenshot, which is turned on and off by pressing M, the same as the mute control for the mic.

---

### Post by alfa_80 on 2011-03-20
> **ajgreeny said:**
> The screenshot does not show your microphone, so is that also set high enough, or is it perhaps muted (showing MM beneath the level shown) as in my screenshot, even though the level is set high.

Note that in alsamixer I have a mic-boost next to the mic, also shown in my screenshot, which is turned on and off by pressing M, the same as the mute control for the mic.

That's interesting, yours one got microphone option while mine one is not there, how to make it there? any ideas..By the way, I've tried to "unmute" all of the options but still it's not working..huhu. Attached is the latest screenshot..

---

### Post by alfa_80 on 2011-03-20
> **alfa_80 said:**
> That's interesting, yours one got microphone option while mine one is not there, how to make it there? any ideas..By the way, I've tried to "unmute" all of the options but still it's not working..huhu. Attached is the latest screenshot..

I've also tried to use GNOME alsamixer, and tick the mic, but still not working. I've attached the screenshot as well.

---

