---
title: "Need help installing realtek ALC662 driver"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by discoduckling on 2009-07-12
Hi,
I'm brand new to ubuntu/linux, and everything that *does* work is pleasant, however i'm tremendously frustrated because i can't install my realtek driver for my audio. I downloaded the compatible driver from the realtek site, but i don't understand how to install it. Anyway, I'm open to ANY suggestions.

Thanks

---

### Post by gobberpooper on 2009-07-12
Check your Sound options through System>Preferences>Sound
Check what you have for each thing. If on one of them it says that the Realtek device is disconnected, then it means that you have to get the Linux ALSA mixer driver. Look for it here:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
Download the driver, extract it, and then follow the install instructions

---

### Post by ~sHyLoCk~ on 2009-07-12
> **discoduckling said:**
> Hi,
I'm brand new to ubuntu/linux, and everything that *does* work is pleasant, however i'm tremendously frustrated because i can't install my realtek driver for my audio. I downloaded the compatible driver from the realtek site, but i don't understand how to install it. Anyway, I'm open to ANY suggestions.

Thanks

ALSA is already pre-installed, are you not getting any sound at all? During Login?

Type ```
alsamixer
``` and set everything to max.
Do ```
sudo alsactl store
```

---

### Post by discoduckling on 2009-07-12
i have the newest alsa 1.0.20

and to shylock, i tried what you said, but it didn't do anything. there is no sound at login, and the only sound there is is the speakers buzzing when i turn them up

---

### Post by ~sHyLoCk~ on 2009-07-12
> **discoduckling said:**
> i have the newest alsa 1.0.20

and to shylock, i tried what you said, but it didn't do anything. there is no sound at login, and the only sound there is is the speakers buzzing when i turn them up

Is your card getting detected?
Post output of ```
aplay -l
``` and ```
lspci -v
```
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=205449") thread.

Ubuntu doesn't use alsaconf so if all fails you can try [OSS]("https://help.ubuntu.com/community/OpenSound").

---

### Post by discoduckling on 2009-07-12
This is what i got:
> ~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3407
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3407
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at fc00 [size=64]
    I/O ports at 1c00 [size=64]
    I/O ports at f400 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 3407
    Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
    Subsystem: Biostar Microtech Int'l Corp Device 3407
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
    Subsystem: Biostar Microtech Int'l Corp Device 3407
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fd800000-fd8fffff
    Prefetchable memory behind bridge: fdf00000-fdffffff
    Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 820f
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f565:3407
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 2505
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ec00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5405
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d800 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5405
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c400 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device 1405
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

---

### Post by discoduckling on 2009-07-13
is there anything else i can do?

---

