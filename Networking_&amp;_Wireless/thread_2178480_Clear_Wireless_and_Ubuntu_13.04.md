---
title: "Clear Wireless and Ubuntu 13.04?"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by Jacob_Bazzrea on 2013-10-03
Currently running Ubuntu 13.04, and I read a solution for a wireless hub that mentioned a net-tools package.  I have been unable to locate such a package on synaptic, and am experiencing some issues with getting the OS to recognize the wireless device.  It's not the clear hub, but rather, a USB wireless receiver.  

Now, has anyone encountered this, or found a solution to it?  (there may already be a thread about this, though my search-fu would have failed me as the first 2 pages had nothing about clear wireless broadband when I searched for it)

Any help is appreciated.

If there are some command lines that need to be used, I can operate the terminal, though the commands would be helpful...still finding my way through Ubuntu after 18 years on Windoze.

EDIT: Currently running 64 bit Ubuntu with the default kernel.

Not currently at the machine to be able to give any of the ifconfig info.

However, if you want to know the hardware:

CPU: AMD FX 8350
CPU HSF: CM Hyper 212 EVO
MB: Asus M5A97 R2.0
RAM: G.Skill (2x4 GB) DDR3-2400 MHz
GPU: Sapphire Radeon HD 7870XT
HDD: WD Caviar Blue 1 TB 7200 RPM 64 MB Cache
Optical: Samsung DVD/CD RW
CASE: Gigabyte GZG2 Plus
PSU: CM Silent Pro M2 620W Semi Modular

I have a Wi-Fi adapter that is an Asus USB N-53, and Ubuntu picks it up just fine, but I can't get the clear device to work properly, which would give me access to the Internet.  On the regular Wi-Fi adapter I can get Wi-Fi from my apartment complex, but it's ridiculously slow (takes 20-30 minutes to download 5-10 MB).

---

### Post by Jacob_Bazzrea on 2013-10-04
Can anyone at least tell me if there is another name for the net-tools package, or if there is another package that contains the same functions?

Ok, so I have discovered that it is a Foxconn / Hon Hai Ubee, this is the lshw:

```
  description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7904MiB
     *-cpu
          product: AMD FX(tm)-8350 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices [AMD] nee ATI
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 ioport:e000(size=4096) memory:fea00000-feafffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Tahiti LE [Radeon HD 7870 XT]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:89 memory:c0000000-cfffffff memory:fea00000-fea3ffff ioport:e000(size=256) memory:fea40000-fea5ffff
           *-multimedia
                description: Audio device
                product: Tahiti XT HDMI Audio [Radeon HD 7970 Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:90 memory:fea60000-fea63fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 ioport:d000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 09
                serial: 74:d0:2b:32:2f:2d
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:88 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:2
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port E)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 memory:fe900000-fe9fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:46 memory:fe900000-fe907fff
        *-pci:3
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port G)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:53 memory:fe800000-fe8fffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:50 memory:fe800000-fe807fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f040(size=8) ioport:f030(size=4) ioport:f020(size=8) ioport:f010(size=4) ioport:f000(size=16) memory:feb0b000-feb0b3ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb0a000-feb0afff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb09000-feb090ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:20 memory:feb08000-feb08fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:feb07000-feb070ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:feb06000-feb06fff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:22 memory:feb05000-feb05fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:23 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@8:2
       logical name: wlan0
       serial: 50:46:5d:4b:be:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.8.0-31-generic firmware=0.29 ip=10.2.152.101 link=yes multicast=yes wireless=IEEE 802.11abgn


```

This is lsusb:

```
 Bus 001 Device 004: ID 0489:e016 Foxconn / Hon Hai Ubee PXU1900 WiMAX Adapter [Beceem BCSM250]
Bus 004 Device 002: ID 1532:0015 Razer USA, Ltd 
Bus 005 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


```

iwconfig:

```
eth0      no wireless extensions.

lo        no wireless extensions.


```

---

### Post by Jacob_Bazzrea on 2013-10-05
I think perhaps that I need to reconfigure the drivers, though, I cannot seem to find a driver for the Foxconn WiMAX adapter.  Any ideas?

---

### Post by Jacob_Bazzrea on 2013-10-05
Seriously?  No one knows anything about this issue?

---

### Post by Jacob_Bazzrea on 2013-10-06
Look, I have tried google, and several other sources, I have read something about trying to use ndiswrapper, however, the wireless adapter I have is not listed as supported on that site.  Additionally, the windows drivers, to try to use ndiswrapper with, are part of a software suite from Clear in the form of a connection manager program.

Surely someone has tried to make this work before...?  In all the time Clear wireless has offered service, no one using Ubuntu has ever tried to get a wireless USB device of theirs to work?

---

### Post by Jacob_Bazzrea on 2013-10-09
Thanks for the multitude of help...I really appreciate the effort that was made to help me resolve the issue.

---

