---
title: "How do I make Starcraft run faster in Ubuntu?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Appolyta on 2009-04-30
Greetings,

I am new to Ubuntu, so I don't know my way around it :(

I installed Starcraft in my laptop and it runs VERY slow... I want the game to run at the speed it's supposed to run at.

Here is some info:

1. Computer:
Sony Vaio Model PCG-4G2L
Subsystem: Sony Corporation Device 81e2

2. Website:
I went to the Ubuntu forums and I found this link:
[http://ubuntuforums.org/showthread.php?t=1139173&highlight=starcraft](http://ubuntuforums.org/showthread.php?t=1139173&highlight=starcraft)

3. Website:
Then I ended up (for some reason I no longer recall) here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

4. Steps:
I was following the steps in this link...
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

...and I got as far as part_ **4**_, which says: *To fix the MTRR issue you will need two pieces of information*
I did all that jazz by running the command 
Code:
$ lspci -v 
5. Problems:
Here is where my difficulties start...

I am "supposed" (according to the forum) get the following output:
Code...00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Dell Device 0164
    Flags: bus master, fast devsel, latency 0, IRQ 11
**    Memory at f0000000 (32-bit, prefetchable) [size=128M]**
    Memory at faf80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at c000 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb
Unfortunately, I get the following...
Code: 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Sony Corporation Device 81e2
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    **Memory at c0000000 (32-bit, prefetchable) [size=256M]**
    Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb


6. Questions:
I know that my computer hardware is different that the person who posted that link...

(1)  Should I continue with the installation, even if one of the lines is different?

(2) I was told by my friend to make a post and ask this question because Ubuntu might not be reading things right.

--- --- --- --- --- ---

Anyway, I hope that my explanation will shed light in the problem I have. Starcrat is a 10 year old game and it should run in my machine.In fact, I was running it just fine when I used Windows XP, but I don't want to go back to Windows.

Let me know if you need more info to address this problem.

Regards,
A.

---

### Post by sandyd on 2009-04-30
your video card is MORE SUPERIOR to the poster's video card. Thats all. 

for more info, read here ;)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=72](http://appdb.winehq.org/objectManager.php?sClass=application&iId=72)

---

### Post by Appolyta on 2009-04-30
Thank you very much :)

---

### Post by LowSky on 2009-04-30
Sony Vaio Model PCG-4G2L

I tried to look up the model but found nearly nothing, could you post the specs please, use this codes

```
lshw
```
```
lspci
```

for instance here is mine

```
john-desktop              
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 4864MiB
     *-cpu
          product: AMD Phenom(tm) 9950 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs cpufreq
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:d0:99:c9:07
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.201 latency=0 module=r8169 multicast=yes
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=32 module=ahci
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=32
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=32 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:03:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
     *-pci:1
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:ca:1c:39:f7:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

john@john-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


```

---

