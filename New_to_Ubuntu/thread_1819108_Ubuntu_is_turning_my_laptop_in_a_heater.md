---
title: "Ubuntu is turning my laptop in a heater"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by computerandu on 2011-08-05
Hi all,

I have been facing this problem for over a month. When I am logged in to Ubuntu 11.04 my laptop fan never stops...it keeps on making sound..blurrrrr....the bottom of my dell inspiron n4010 is so hot that i can barely keep it in my lap.....what is worse...in past one month my battery life has been reduced by approx 60%....

The problem is when I use Windows 7 ...my laptop is not that hot...its behavior is quite normal....but in ubuntu...aaahhh...

Any suggestion how to handle it?

---

### Post by Toz on 2011-08-05
What video card do you have and what video driver are you using?
In a terminal window:
```
sudo lspci -vnn
```
If you are not using proprietary drivers, maybe installing them might help.

Do you have i8kutils installed?
> Description: utilities for Dell Inspiron and Latitude laptops
 This is a collection of utilities to control Dell Inspiron and Latitude
 laptops. It includes programs to turn the fan on and off, to read fan
 status, CPU temperature, BIOS version and to handle the volume buttons
 and Fn-keys.


Possibly related to 2.6.38 power regression? See: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by LowSky on 2011-08-05
Arccording to this it has an ATI graphics card:
[http://www.pcworld.com/product/552981/dell_inspiron_14r_model_n4010.html?p=specs](http://www.pcworld.com/product/552981/dell_inspiron_14r_model_n4010.html?p=specs)

If that is true are you using the proprietary drivers? They will control the graphics card better than the open source drivers.

Is i8kutils installed? it is a utility program for Dell Laptops.

```
sudo apt-get install i8kutils
```

Note it may need some customization once installed. Check Google for ideas, I don't want to point you into any certain direction,  screwing up the fan speeds can break your computer I dont want that on me.

---

### Post by tkn4everb on 2011-08-06
I'm having the same issues and made a topic about it here: 

[http://ubuntuforums.org/showthread.php?t=1817770](http://ubuntuforums.org/showthread.php?t=1817770)

---

### Post by computerandu on 2011-08-06
> **Toz said:**
> What video card do you have and what video driver are you using?
In a terminal window:
```
sudo lspci -vnn
```If you are not using proprietary drivers, maybe installing them might help.

Do you have i8kutils installed?


Possibly related to 2.6.38 power regression? See: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)



The output of sudo lspci -vnn

```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at f0806800 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0807000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: bc000000-bc1fffff
    Prefetchable memory behind bridge: 00000000bc200000-00000000bc3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device [1028:0456]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0500000-f05fffff
    Prefetchable memory behind bridge: 00000000bc400000-00000000bc5fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device [1028:0456]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0400000-f04fffff
    Prefetchable memory behind bridge: 00000000bc600000-00000000bc7fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device [1028:0456]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0807400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: [50] Subsystem: Dell Device [1028:0456]

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 1840 [size=8]
    I/O ports at 1814 [size=4]
    I/O ports at 1818 [size=8]
    I/O ports at 1810 [size=4]
    I/O ports at 1820 [size=32]
    Memory at f0806000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Dell Device [1028:0456]
    Flags: medium devsel, IRQ 10
    Memory at f0807800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1860 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
    Subsystem: Dell Device [1028:0456]
    Flags: fast devsel, IRQ 18
    Memory at f0605000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0010]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-a1-ff-ff-c2-70-f1
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: brcm80211
    Kernel modules: brcm80211

04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Dell Device [1028:0456]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-67-11-46-b8-ac-6f-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0


```

---

### Post by computerandu on 2011-08-06
I'll check other option and will post the findings.

---

### Post by Toz on 2011-08-06
Have you tried the **acpi_osi=\"Linux\"** kernel parameter?

---

### Post by sffvba[e0rt on 2011-08-06
There is a performance regression that has been found in the kernels that are currently in use for 11.04...

[Source]("http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1")

What has helped me in the past is to install a newer kernel... 3.0 is available ([how to install]("http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html"))but I had a few but I had a few kernel panics after installing Virtualbox with this one...

The kernel that worked the best for me so far is 3.0-rc2 ... ([How to install]("http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal"))

---

### Post by computerandu on 2011-08-06
> **Toz said:**
> Have you tried the **acpi_osi=\"Linux\"** kernel parameter?

Could you please give some more details?

---

### Post by Toz on 2011-08-06
See: [http://ubuntuforums.org/showpost.php?p=11124786&postcount=14]("http://ubuntuforums.org/showpost.php?p=11124786&postcount=14")

---

### Post by computerandu on 2011-08-08
> **Toz said:**
> See: [http://ubuntuforums.org/showpost.php?p=11124786&postcount=14](http://ubuntuforums.org/showpost.php?p=11124786&postcount=14)


I have already tried it....no effects....

One thing which I just remembered is that I installed MacUbuntu theme to make my ubuntu look like Mac...this theme have an uninstall option which doesn't work...i tried various ways to uninstall it but it is uninstalled only partially....

If I recall peoperly, the problem started when I installed MacUbuntu....

any suggestions?

---

### Post by amjjawad on 2011-08-08
> **computerandu said:**
> I have already tried it....no effects....

One thing which I just remembered is that I installed MacUbuntu theme to make my ubuntu look like Mac...this theme have an uninstall option which doesn't work...i tried various ways to uninstall it but it is uninstalled only partially....

If I recall peoperly, the problem started when I installed MacUbuntu....

any suggestions?

Perhaps:

```
sudo apt-get purge <packagename> -y

```

---

### Post by sffvba[e0rt on 2011-08-08
> **not found said:**
> There is a performance regression that has been found in the kernels that are currently in use for 11.04...

[Source]("http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1")

What has helped me in the past is to install a newer kernel... 3.0 is available ([how to install]("http://linuxpoison.blogspot.com/2011/08/how-to-install-latest-kernel-30-on.html"))but I had a few but I had a few kernel panics after installing Virtualbox with this one...

The kernel that worked the best for me so far is 3.0-rc2 ... ([How to install]("http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal"))

Hey OP... not to hammer on something you may be ignoring on purpose... but have you considered this post of mine I made earlier?

---

### Post by computerandu on 2011-08-08
> **not found said:**
> Hey OP... not to hammer on something you may be ignoring on purpose... but have you considered this post of mine I made earlier?

I searched on it only to find that the problem has not been solved even in kernel 3.0 (webupd8 and omg ubuntu)

---

### Post by sffvba[e0rt on 2011-08-08
> **computerandu said:**
> I searched on it only to find that the problem has not been solved even in kernel 3.0 (webupd8 and omg ubuntu)

Oh wow... OK... It did seem to be better for me using the RC2... Good luck sorting it out :)

---

