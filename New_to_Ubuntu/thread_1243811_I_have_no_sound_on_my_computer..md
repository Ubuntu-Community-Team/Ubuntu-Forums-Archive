---
title: "I have no sound on my computer."
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Katty2008 on 2009-08-18
[FONT=Comic Sans MS][SIZE=4]:confused::(:confused:I have a HP Pavilion dv4-1225dx notebook. It came with Window Vista 64bit edition. My husband to be try putting kubuntu are it first and the computer wouldn't take it. So, he put ubuntu on it and forced it to change to kubuntu. I've never really used ubuntu before and I only know very little about computer. I don't have sound on my computer anymore  and I saw that many people with this type of notebook had this problem and they showed how they fixed it, but I can't understand what they are talking about. I have no sound in my speakers or my headphone jacks and I'm really confused. Someone please help me!!![/SIZE][/FONT]:confused::(:confused:

---

### Post by impert on 2009-08-18
The first place to start is here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Katty2008 on 2009-08-19
I whet to it and it's not clear to me. What does it mean to open "a shell"???

---

### Post by sumeshgupta on 2009-08-19
Open a shell means open a terminal. You can do that by going to **Applications > Accessories > Terminal**. A new window will pop up like the C:> prompt in windows. Thats the shell.

---

### Post by Katty2008 on 2009-08-20
Thanks you so much on clearing that up for me.:P

---

### Post by simransingh on 2009-08-20
hi mate..im new to ubuntu too (and linux)....just started using it yday and i had the smae prob.
I switched off "external amplifier" setting in sound preferences and that did the job for me!

---

### Post by Katty2008 on 2009-08-20
Okay, this as far as I've gotten. 

kat@Mary:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kat@Mary:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: d2300000-d24fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00006fff
    Memory behind bridge: d1300000-d22fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: d1200000-d12fffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000b00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: d1100000-d11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: b0100000-b01fffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8038 [size=8]
    I/O ports at 804c [size=4]
    I/O ports at 8030 [size=8]
    I/O ports at 8048 [size=4]
    I/O ports at 8010 [size=16]
    Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d2508500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d2508400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
    I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 7000 [size=256]
    Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
    Memory at d2300000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
    Subsystem: ATI Technologies Inc RS780 Azalia controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1200300 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at b0000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: fast devsel, IRQ 17
    Memory at d1200200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d1200100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d1200000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 137c
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d1100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30fb
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at 2000 [size=256]
    Memory at d1010000 (64-bit, prefetchable) [size=4K]
    Memory at d1000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

kat@Mary:~$ 

I'm now trying to find my soundcard in it, so that I can find out if there is an alsa driver. I'm sorry if I sound like an idiot, but I don't know much about computers and I'm just learning it now.

---

### Post by Don1500 on 2009-08-20
You have : ATI RS780 Azalia sound controller

---

