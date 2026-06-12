---
title: "Effects?"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by khjui on 2010-02-12
Hi
For some reason, when I try and run effects, I get a message saying: Desktop Effects Could Not Be Enabled.

Do I have to install anything extra to run effects?

Also, 
I have seen a you tube video in which the user of Ubuntu can make a 3d window view? And have 4 desktops open?

Thanks In Advance

-Tom

(I'm using Ubuntu 9.10)

---

### Post by audiomick on 2010-02-12
Hi.
For anyone to be able to help you, they will need to know what graphics card you are using.
Open a terminal, do
```
lspci
```
and post the result back here, if you don't already know what brand and model it is.

---

### Post by khjui on 2010-02-12
> **audiomick said:**
> Hi.
For anyone to be able to help you, they will need to know what graphics card you are using.
Open a terminal, do
```
lspci
```and post the result back here, if you don't already know what brand and model it is.

Thanks!
After doing that, I got this:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10
```

---

### Post by audiomick on 2010-02-12
Hallo
this
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
```is your graphics card.

You probably haven't got the proprietary driver activated. Go to
system> administration> hardware drivers
and select and activate the driver it offers you.

I am using nVidia, so after that, I am a bit hazy with ATI graphics. If you are still having problems, you might have to wait for someone with ATI experience.

---

### Post by khjui on 2010-02-12
> **audiomick said:**
> Hallo
this
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
```is your graphics card.

You probably haven't got the proprietary driver activated. Go to
system> administration> hardware drivers
and select and activate the driver it offers you.

I am using nVidia, so after that, I am a bit hazy with ATI graphics. If you are still having problems, you might have to wait for someone with ATI experience.

Ahhh, that did it! Thanks!

---

### Post by sandyd on 2010-02-12
[s]You can also use envyng, or download it from the ATI Site.[/s]
if it works, dont touch it....

---

