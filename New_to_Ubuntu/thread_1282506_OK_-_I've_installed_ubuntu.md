---
title: "OK - I've installed ubuntu"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by waste301 on 2009-10-04
The graphics are not right - something like 800x600 and I cannot get online with a broadcom 802.11 wireless network card.

---

### Post by LewRockwell on 2009-10-04
some equipment takes a little extra cuddling

.

---

### Post by aysiu on 2009-10-04
Can you copy and paste (with your mouse) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
lspci -v
cat /etc/lsb-release
uname -a
``` and then paste the output back here in three separate [noparse]```
put output here
```[/noparse] tags?

---

### Post by waste301 on 2009-10-04
> **aysiu said:**
> Can you copy and paste (with your mouse) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
lspci -v
cat /etc/lsb-release
uname -a
``` and then paste the output back here in three separate [noparse]```
put output here
```[/noparse] tags?

here is the first command:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fd900000-fd9fffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2301
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Linksys Device 0042
	Flags: bus master, fast devsel, latency 32, IRQ 18
	Memory at fdefe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

matt@matt-desktop:~$ 

here is the second:

matt@matt-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
matt@matt-desktop:~$ 

here is the third:

matt@matt-desktop:~$ uname -a
Linux matt-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
matt@matt-desktop:~$ 

I hope this helps

---

### Post by aysiu on 2009-10-04
Okay, if you go to System > Administration > Hardware Drivers, does it prompt you to activate any plugins? If so, see if activating the STA or BC43XX drivers helps with the wireless card. You may also want to enable the Nvidia drivers, too.

And, in both cases, a reboot may be necessary for the change to take full effect.

---

### Post by waste301 on 2009-10-04
> **aysiu said:**
> Okay, if you go to System > Administration > Hardware Drivers, does it prompt you to activate any plugins? If so, see if activating the STA or BC43XX drivers helps with the wireless card. You may also want to enable the Nvidia drivers, too.

And, in both cases, a reboot may be necessary for the change to take full effect.

It says that no proprietary drivers are in use on the system.

---

### Post by LewRockwell on 2009-10-04
> **waste301 said:**
> here is the first command:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fd900000-fd9fffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2301
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a5b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Linksys Device 0042
	Flags: bus master, fast devsel, latency 32, IRQ 18
	Memory at fdefe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

matt@matt-desktop:~$ 

here is the second:

matt@matt-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
matt@matt-desktop:~$ 

here is the third:

matt@matt-desktop:~$ uname -a
Linux matt-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
matt@matt-desktop:~$ 

I hope this helps

how did it run using the LiveCD

.

---

### Post by LewRockwell on 2009-10-04
[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)

.

---

### Post by LewRockwell on 2009-10-04
[http://ubuntuforums.org/showthread.php?t=384392](http://ubuntuforums.org/showthread.php?t=384392)

.

---

### Post by LewRockwell on 2009-10-04
[http://ubuntuforums.org/showthread.php?t=1249723](http://ubuntuforums.org/showthread.php?t=1249723)


[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntudriver-not-working-for-nvidia-6150-se-geforce-717941/?](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntudriver-not-working-for-nvidia-6150-se-geforce-717941/?)


.

---

### Post by waste301 on 2009-10-04
> **LewRockwell said:**
> [http://ubuntuforums.org/showthread.php?t=1249723](http://ubuntuforums.org/showthread.php?t=1249723)


[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntudriver-not-working-for-nvidia-6150-se-geforce-717941/?](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntudriver-not-working-for-nvidia-6150-se-geforce-717941/?)


.

Ok - I have tried all of the suggestions in the links you posted, but they are all to old.  I have installed ndiswrapper successfully, but get permission denied when I try to install the driver.

I am pretty sure that those guides are not directing me to the correct blacklist file.  Where is the file in 9.0.4?

---

