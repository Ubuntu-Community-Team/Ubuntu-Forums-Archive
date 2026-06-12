---
title: "Another realtek alc650 issue!"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by spikeyjohn on 2009-07-31
Hi, hoping someone can help. Been loving Ubuntu for a while now on my laptop which just installed and worked so decided to go that way on my desktop/media pc as well. I have trawled through just about every post I can find and tried just about everything I can find to get the sound working!

The main difference with my desktop PC is it's older with the nforce2 chipset and therefore ac 97 realtek sound. The alc650 in this case. 

I really hope someone can help me get this working so I don't have to go back to windows!

When I run aplay -l i get:

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And when I run lspci -v I get:

00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [40] AGP version 2.0
    Capabilities: [60] HyperTransport: Host or Secondary Interface
    Kernel driver in use: agpgart-nvidia
    Kernel modules: nvidia-agp

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [48] HyperTransport: Slave or Primary Interface

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: 66MHz, fast devsel, IRQ 5
    I/O ports at e400 [size=32]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at e8080000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at e8083000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at e8086000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0080
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at e8087000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d000 [size=8]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
    Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [44] Power Management version 2

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    I/O ports at d400 [size=256]
    I/O ports at d800 [size=128]
    Memory at e8081000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Kernel modules: shpchp

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f297:f541
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f000 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd

00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3) (prog-if 10)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device f541
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at e8084000 (32-bit, non-prefetchable) [size=2K]
    Memory at e8085000 (32-bit, non-prefetchable) [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
    Flags: bus master, 66MHz, medium devsel, latency 32
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: e4000000-e5ffffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
    Subsystem: Albatron Corp. Device 8009
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
    Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Memory at d8000000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at d8080000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 2.0
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb, rivafb


Any help apprecited. Cheers

---

### Post by spikeyjohn on 2009-08-01
Please someone help? :(

---

