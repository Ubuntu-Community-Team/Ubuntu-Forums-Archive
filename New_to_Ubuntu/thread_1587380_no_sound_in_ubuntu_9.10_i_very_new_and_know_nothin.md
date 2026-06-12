---
title: "no sound in ubuntu 9.10 i very new and know nothing about linux"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by hamurabizero on 2010-10-03
```
root@hamurabi-desktop:~# lspci
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)
```
```

root@hamurabi-desktop:~# root@hamurabi-desktop:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@hamurabi-desktop:~# 
root@hamurabi-desktop:~# alsa force-reload 
Terminating processes: 2100.
Unloading ALSA sound driver modules: snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
root@hamurabi-desktop:~# alsa force-reload 

root@hamurabi-desktop:~# lspci -v
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 4f00 [size=256]

00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 4900 [size=64]
    I/O ports at 4d00 [size=64]
    I/O ports at 4e00 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: 66MHz, fast devsel

00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1) (prog-if 10)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1) (prog-if 20)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at febfec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0098
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
    Subsystem: Elitegroup Computer Systems Device 2813
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Capabilities: [b8] Subsystem: Elitegroup Computer Systems Device 1359

00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Subsystem: Elitegroup Computer Systems Device 1359
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: [40] Subsystem: Elitegroup Computer Systems Device 1359
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: [40] Subsystem: Elitegroup Computer Systems Device 1359
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
    I/O ports at e480 [size=8]
    I/O ports at e400 [size=4]
    I/O ports at e080 [size=8]
    I/O ports at e000 [size=4]
    I/O ports at dc00 [size=16]
    Memory at febfc000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Capabilities: [8c] SATA HBA <?>
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
    Kernel driver in use: ahci

00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 28
    Memory at febf7000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d880 [size=8]
    Memory at febfe800 (32-bit, non-prefetchable) [size=256]
    Memory at febfe400 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)
    Subsystem: Elitegroup Computer Systems Device 1359
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

root@hamurabi-desktop:~# 








************************************************************************* 
************************************************************************* 
*                                                                       * 
*                            Sound Directory                            * 
*                              README FILE                              * 
*                                                                       * 
*  =================================================================    * 
*    [HD Audio    ] Realtek High Definition Audio Driver                * 
*                   Version R1.77, 2007/09/17                           * 
*                                                                       * 
*    [IDT         ] IDT High Definition Audio driver.                   * 
*                   Version 0.40 , Release 2007/11/22.                  * 
*                                                                       * 
*  =================================================================    * 
*                                                                       * 
************************************************************************* 
************************************************************************* 
 
 
```
* All brand or product names mentioned are trademarks or registered 
  trademarks of their respective holders.



i am very thankfull, if somebody genius solve my problem, and send ur advice to my email id.,  [email]snip[/email].

---

### Post by overdrank on 2010-10-03
Hi and welcome, Moved to  Absolute Beginner Talk. Also not a good idea with the email because of spam. :)

---

