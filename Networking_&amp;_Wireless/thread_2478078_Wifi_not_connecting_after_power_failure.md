---
title: "Wifi not connecting after power failure"
date: 2022-08-16
forum: Networking &amp; Wireless
---

### Post by rguerra on 2022-08-16
Hi,

After a power failure in my home, my pc  is not able to connect to the wifi anymore. Is there any way to know if the hardware is damaged? The output of lspci -v is

```
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer 8th Gen Core Processor Host Bridge/DRAM Registers
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: skl_uncore


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff [size=4K]
    Memory behind bridge: 7e000000-7f0fffff [size=17M]
    Prefetchable memory behind bridge: 0000000090000000-00000000a1ffffff [size=288M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile) (prog-if 00 [VGA controller])
    DeviceName: Onboard - Video
    Subsystem: CLEVO/KAPOK Computer UHD Graphics 630 (Mobile)
    Flags: bus master, fast devsel, latency 0, IRQ 131
    Memory at 7d000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
    Flags: fast devsel, IRQ 255
    Memory at 7f41e000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>


00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Cannon Lake PCH Thermal Controller
    Flags: fast devsel, IRQ 16
    Memory at 7f41d000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal


00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10) (prog-if 30 [XHCI])
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Cannon Lake PCH USB 3.1 xHCI Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 126
    Memory at 7f400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Cannon Lake PCH Shared SRAM
    Flags: fast devsel
    Memory at 7f416000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Memory at 7f41c000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>


00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Cannon Lake PCH HECI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 130
    Memory at 7f41b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:17.0 SATA controller: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller (rev 10) (prog-if 01 [AHCI 1.0])
    DeviceName: Onboard - SATA
    Subsystem: CLEVO/KAPOK Computer Cannon Lake Mobile PCH SATA AHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 128
    Memory at 7f414000 (32-bit, non-prefetchable) [size=8K]
    Memory at 7f41a000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5090 [size=8]
    I/O ports at 5080 [size=4]
    I/O ports at 5060 [size=32]
    Memory at 7f419000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: [disabled]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.5 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: 7f300000-7f3fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.6 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #15 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff [size=4K]
    Memory behind bridge: 7f200000-7f2fffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1f.0 ISA bridge: Intel Corporation HM470 Chipset LPC/eSPI Controller (rev 10)
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Device 852b
    Flags: bus master, medium devsel, latency 0


00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    DeviceName: Onboard - Sound
    Subsystem: CLEVO/KAPOK Computer Cannon Lake PCH cAVS
    Flags: bus master, fast devsel, latency 32, IRQ 138
    Memory at 7f410000 (64-bit, non-prefetchable) [size=16K]
    Memory at 7f100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci


00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Cannon Lake PCH SMBus Controller
    Flags: medium devsel, IRQ 16
    Memory at 7f418000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801


00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
    DeviceName: Onboard - Other
    Subsystem: CLEVO/KAPOK Computer Cannon Lake PCH SPI Controller
    Flags: fast devsel
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]


01:00.0 VGA compatible controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Ti Mobile] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer GP107M [GeForce GTX 1050 Ti Mobile]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at 7e000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    Memory at a0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [disabled] [size=128]
    Expansion ROM at 7f000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau


01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 7f080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


03:00.0 Network controller: Intel Corporation Wireless-AC 9260 (rev 29)
    Subsystem: Intel Corporation Wireless-AC 9260
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 7f300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
    Subsystem: CLEVO/KAPOK Computer RTL8411B PCI Express Card Reader
    Flags: bus master, fast devsel, latency 0, IRQ 127
    Memory at 7f215000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at 7f200000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci


04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at 3000 [size=256]
    Memory at 7f214000 (64-bit, non-prefetchable) [size=4K]
    Memory at 7f210000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

I would be very grateful if someone could help me to figure out what is happening. Thanks is advance,

Rui

---

### Post by TheFu on 2022-08-16
Power spikes destroy electronics all the time.  Years ago, I had 3 modems destroyed in 6 months due to power strikes.  The solution is to get a quality UPS and run all computing and network device power through it.

Is the wifi issue only for this 1 machine? 
Do all other devices still work?
Was there a new kernel installed?  For some network chips, new kernels break support that was working.  
Can you boot from an older kernel? 
Does it work then?
If this 1 machine, if you boot from a flash "Try Ubuntu" drive, does it work?

Those steps will determine if the wifi-AP is the problem  and if the OS/settings are the issue or not.  The answers for each question provide a little more detail for how to reduce the problem down to 1 element just a little further.

I have a 10 yr old USB wifi adapter, which has always "just worked" (though I haven't used it recently).  If you have an old spare USB wifi adapter that is known to work with Linux, might try using that in the meantime.  $20 is what a cheap wifi-AC adapter costs these days.

Of course, for many people my next suggestion will come as a shock, but why not use wired eithernet?  It is more stable and faster than any wifi.

---

### Post by nikaim811 on 2022-09-14
Same problem i am also facing after booting it do same connecting problem after few hours.
                                                                        [[SIZE=1][COLOR=#ffffff]Stylish Frenchies[/COLOR][/SIZE]]("https://www.stylishfrenchies.com/do-french-bulldogs-shed/") [SIZE=1][COLOR=#ffffff]is the leading source to provide information about french bulldog care and there behaviour.[/COLOR][/SIZE]

     
I have good quality ups but still some times it also fails.   
 


I have 15 smart devices working on that ups.

---

