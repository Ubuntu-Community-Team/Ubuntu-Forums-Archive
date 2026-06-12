---
title: "Wifi Works Unencrypted, not w/ WEP"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by banana989 on 2006-11-11
Howdy- I can't connect to my router when I set it up with wep security. I have no problem connecting to it when I use no security at all. I have tried the built in Gnome network wireless configuration with no luck. I have also trid Wifi-radar with no luck. 

My laptop's Wifi card uses the ipw3945 driver. 

any ideas? thanks !

---

### Post by FrodoB on 2006-11-11
Here is a link to a generator that can give you the same keys in ASCII and HEX format.  

Normally HEX will work best for both. Put the same one in the router and in the Ubuntu and any other machines.

After you have set things up in the Networking panel you can check your work in a terminal widow with:

$ more /etc/network/interfaces

You will be able to verify the key that you entered.

---

### Post by rvickers on 2006-11-11
banana, I have a ipw3945 that I can't get to connect with or without a wep key. What are you using, Network Manager, System->Network, WiFi Radar or what? 
Thanks

---

### Post by banana989 on 2006-11-12
wifi-radar has always been the most reliable for me :)  also, check your dmesg for any errors loading the module , and make sure that you've done a  'depmod -a'

---

### Post by rvickers on 2006-11-12
At the end of dmesg:
[17190923.340000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17191049.464000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17191057.468000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17191057.472000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17191067.728000] eth0: no IPv6 routers present
[17199416.544000] ADDRCONF(NETDEV_UP): eth1: link is not ready

Any idea how I find out eth1 is not ready?

Thanks

---

### Post by FrodoB on 2006-11-12
There should have been more information about the attempt a loading the device up higher in the dmesg output.  Publish that and let's see what is happening.  Also what kind of device is it?

---

### Post by banana989 on 2006-11-12
I am also getting the "ADDRCONF ... link is not ready" message. 

I have tried using hex as my WEP key , still no results. The info in /etc/networks/interfaces is correct. Again - this does work when I use no security with my wireless router. 

I have tried Gnome's network settings as well as wifi-radar. One interesting thing i saw was that when wifi-radar was attempting to do DHCP , it sent this command > DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

---

### Post by rvickers on 2006-11-12
lspci shows:   ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1019792k/1038784k available (1910k kernel code, 18300k reserved, 1070k data, 308k init, 121280k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1596.045 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3196.93 BogoMIPS (lpj=6393872)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000140 0000c189 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179570.428000] Freeing initrd memory: 5563k freed
[17179570.428000] ACPI: Core revision 20060707
[17179570.428000] ACPI: Looking for DSDT ... not found!
[17179570.500000] CPU0: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[17179570.500000] SMP alternatives: switching to SMP code
[17179570.500000] Booting processor 1/1 eip 3000
[17179570.512000] Initializing CPU#1
[17179570.592000] Calibrating delay using timer specific routine.. 3192.13 BogoMIPS (lpj=6384278)
[17179570.592000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179570.592000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179570.592000] monitor/mwait feature present.
[17179570.592000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.592000] CPU: L2 cache: 2048K
[17179570.592000] CPU: Hyper-Threading is disabled
[17179570.592000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000140 0000c189 00000000 00000000
[17179570.592000] CPU1: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[17179570.592000] Total of 2 processors activated (6389.07 BogoMIPS).
[17179570.592000] ENABLING IO-APIC IRQs
[17179570.592000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.740000] checking TSC synchronization across 2 CPUs: passed.
[17179570.744000] Brought up 2 CPUs
[17179570.912000] migration_cost=4000
[17179570.912000] NET: Registered protocol family 16
[17179570.912000] EISA bus registered
[17179570.912000] ACPI: bus type pci registered
[17179570.912000] PCI: Using MMCONFIG
[17179570.912000] Setting up standard PCI resources
[17179570.924000] ACPI: Interpreter enabled
[17179570.924000] ACPI: Using IOAPIC for interrupt routing
[17179570.928000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.928000] PCI: Probing PCI hardware (bus 00)
[17179571.000000] Boot video device is 0000:00:02.0
[17179571.000000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179571.000000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.000000] PCI: Bus #08 (-#0b) is hidden behind transparent bridge #07 (-#07) (try 'pci=assign-busses')
[17179571.000000] Please report the result to linux-kernel to fix this permanently
[17179571.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179571.132000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.156000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179571.156000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.156000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.156000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179571.156000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.156000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179571.160000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.160000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.160000] ACPI: Embedded Controller [EC0] (gpe 22) interrupt mode.
[17179571.220000] ACPI: Power Resource [FN00] (off)
[17179571.220000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.220000] pnp: PnP ACPI init
[17179571.316000] pnp: PnP ACPI: found 10 devices
[17179571.316000] PnPBIOS: Disabled by ACPI PNP
[17179571.316000] PCI: Using ACPI for IRQ routing
[17179571.316000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.316000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.316000] PCI: Bridge: 0000:00:1c.0
[17179571.316000]   IO window: disabled.
[17179571.316000]   MEM window: disabled.
[17179571.316000]   PREFETCH window: disabled.
[17179571.316000] PCI: Bridge: 0000:00:1c.1
[17179571.316000]   IO window: 2000-2fff
[17179571.316000]   MEM window: d8000000-d9ffffff
[17179571.316000]   PREFETCH window: d2000000-d3ffffff
[17179571.316000] PCI: Bridge: 0000:00:1c.2
[17179571.316000]   IO window: 3000-3fff
[17179571.316000]   MEM window: da000000-dbffffff
[17179571.316000]   PREFETCH window: d4000000-d5ffffff
[17179571.316000] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[17179571.316000]   IO window: 00004400-000044ff
[17179571.316000]   IO window: 00004800-000048ff
[17179571.316000]   PREFETCH window: 50000000-51ffffff
[17179571.316000]   MEM window: 52000000-53ffffff
[17179571.316000] PCI: Bridge: 0000:00:1e.0
[17179571.316000]   IO window: 4000-4fff
[17179571.316000]   MEM window: dc000000-dc0fffff
[17179571.316000]   PREFETCH window: 50000000-51ffffff
[17179571.316000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.316000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.316000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179571.316000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.316000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.316000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.316000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.316000] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[17179571.316000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179571.316000] NET: Registered protocol family 2
[17179571.364000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.364000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.364000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)


****************** too many images so I had to break it up into 2 segments

---

### Post by rvickers on 2006-11-12
Can't get all of dmesg to post, message about too many images...
I'll keep trying

---

### Post by rvickers on 2006-11-12
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 1019792k/1038784k available (1910k kernel code, 18300k reserved, 1070k data, 308k init, 121280k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1596.045 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3196.93 BogoMIPS (lpj=6393872)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000140 0000c189 00000000 00000000
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179570.428000] Freeing initrd memory: 5563k freed
[17179570.428000] ACPI: Core revision 20060707
[17179570.428000] ACPI: Looking for DSDT ... not found!
[17179570.500000] CPU0: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[17179570.500000] SMP alternatives: switching to SMP code
[17179570.500000] Booting processor 1/1 eip 3000
[17179570.512000] Initializing CPU#1
[17179570.592000] Calibrating delay using timer specific routine.. 3192.13 BogoMIPS (lpj=6384278)
[17179570.592000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179570.592000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179570.592000] monitor/mwait feature present.
[17179570.592000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.592000] CPU: L2 cache: 2048K
[17179570.592000] CPU: Hyper-Threading is disabled
[17179570.592000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000140 0000c189 00000000 00000000
[17179570.592000] CPU1: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[17179570.592000] Total of 2 processors activated (6389.07 BogoMIPS).
[17179570.592000] ENABLING IO-APIC IRQs
[17179570.592000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.740000] checking TSC synchronization across 2 CPUs: passed.
[17179570.744000] Brought up 2 CPUs
[17179570.912000] migration_cost=4000
[17179570.912000] NET: Registered protocol family 16
[17179570.912000] EISA bus registered
[17179570.912000] ACPI: bus type pci registered
[17179570.912000] PCI: Using MMCONFIG
[17179570.912000] Setting up standard PCI resources
[17179570.924000] ACPI: Interpreter enabled
[17179570.924000] ACPI: Using IOAPIC for interrupt routing
[17179570.928000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.928000] PCI: Probing PCI hardware (bus 00)
[17179571.000000] Boot video device is 0000:00:02.0
[17179571.000000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179571.000000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.000000] PCI: Bus #08 (-#0b) is hidden behind transparent bridge #07 (-#07) (try 'pci=assign-busses')
[17179571.000000] Please report the result to linux-kernel to fix this permanently
[17179571.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179571.128000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179571.132000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.156000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179571.156000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.156000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.156000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179571.156000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.156000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179571.160000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179571.160000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.160000] ACPI: Embedded Controller [EC0] (gpe 22) interrupt mode.
[17179571.220000] ACPI: Power Resource [FN00] (off)
[17179571.220000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.220000] pnp: PnP ACPI init
[17179571.316000] pnp: PnP ACPI: found 10 devices
[17179571.316000] PnPBIOS: Disabled by ACPI PNP
[17179571.316000] PCI: Using ACPI for IRQ routing
[17179571.316000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.316000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.316000] PCI: Bridge: 0000:00:1c.0
[17179571.316000]   IO window: disabled.
[17179571.316000]   MEM window: disabled.
[17179571.316000]   PREFETCH window: disabled.
[17179571.316000] PCI: Bridge: 0000:00:1c.1
[17179571.316000]   IO window: 2000-2fff
[17179571.316000]   MEM window: d8000000-d9ffffff
[17179571.316000]   PREFETCH window: d2000000-d3ffffff
[17179571.316000] PCI: Bridge: 0000:00:1c.2
[17179571.316000]   IO window: 3000-3fff
[17179571.316000]   MEM window: da000000-dbffffff
[17179571.316000]   PREFETCH window: d4000000-d5ffffff
[17179571.316000] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[17179571.316000]   IO window: 00004400-000044ff
[17179571.316000]   IO window: 00004800-000048ff
[17179571.316000]   PREFETCH window: 50000000-51ffffff
[17179571.316000]   MEM window: 52000000-53ffffff
[17179571.316000] PCI: Bridge: 0000:00:1e.0
[17179571.316000]   IO window: 4000-4fff
[17179571.316000]   MEM window: dc000000-dc0fffff
[17179571.316000]   PREFETCH window: 50000000-51ffffff
[17179571.316000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.316000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.316000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179571.316000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.316000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.316000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.316000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.316000] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[17179571.316000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179571.316000] NET: Registered protocol family 2
[17179571.364000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.364000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.364000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.364000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.364000] TCP reno registered
[17179571.364000] Simple Boot Flag at 0x36 set to 0x1
[17179571.368000] audit: initializing netlink socket (disabled)
[17179571.368000] audit(1163308434.368:1): initialized
[17179571.368000] highmem bounce pool size: 64 pages
[17179571.368000] VFS: Disk quotas dquot_6.5.1
[17179571.368000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.368000] Initializing Cryptographic API
[17179571.368000] io scheduler noop registered
[17179571.368000] io scheduler anticipatory registered
[17179571.368000] io scheduler deadline registered
[17179571.368000] io scheduler cfq registered (default)
[17179571.368000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.368000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.368000] assign_interrupt_mode Found MSI capability
[17179571.368000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179571.368000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179571.368000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179571.368000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179571.368000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.368000] assign_interrupt_mode Found MSI capability
[17179571.368000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179571.368000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179571.368000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179571.368000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179571.368000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179571.368000] assign_interrupt_mode Found MSI capability
[17179571.368000] Allocate Port Service[0000:00:1c.2:pcie00]
[17179571.368000] Allocate Port Service[0000:00:1c.2:pcie02]
[17179571.368000] Allocate Port Service[0000:00:1c.2:pcie03]
[17179571.368000] isapnp: Scanning for PnP cards...
[17179571.724000] isapnp: No Plug & Play device found
[17179571.768000] Real Time Clock Driver v1.12ac
[17179571.768000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.768000] mice: PS/2 mouse device common for all mice
[17179571.768000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.768000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.768000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.768000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.772000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.772000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.772000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.772000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.796000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.816000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.816000] EISA: Probing bus 0 at eisa.0
[17179571.816000] Cannot allocate resource for EISA slot 1
[17179571.816000] Cannot allocate resource for EISA slot 2
[17179571.816000] Cannot allocate resource for EISA slot 3
[17179571.816000] Cannot allocate resource for EISA slot 4
[17179571.816000] EISA: Detected 0 cards.
[17179571.816000] TCP bic registered
[17179571.816000] NET: Registered protocol family 1
[17179571.816000] NET: Registered protocol family 8
[17179571.816000] NET: Registered protocol family 20
[17179571.816000] Starting balanced_irq
[17179571.816000] Using IPI No-Shortcut mode
[17179571.816000] ACPI: (supports S0 S3 S4 S5)
[17179571.816000] Freeing unused kernel memory: 308k freed
[17179571.936000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.960000] Capability LSM initialized
[17179573.016000] ACPI: Transitioning device [FAN0] to D3
[17179573.016000] ACPI: Transitioning device [FAN0] to D3
[17179573.016000] ACPI: Fan [FAN0] (off)
[17179573.024000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[17179573.024000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[17179573.024000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.024000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.028000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[17179573.028000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[17179573.028000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[17179573.028000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179573.028000] ACPI: Thermal Zone [TZ00] (45 C)
[17179573.032000] ACPI: Invalid passive threshold
[17179573.036000] ACPI: Transitioning device [FAN0] to D0
[17179573.036000] ACPI: Transitioning device [FAN0] to D0
[17179573.036000] ACPI: Unable to turn cooling device [dffe839c] 'on'
[17179573.036000] ACPI: Thermal Zone [TZ01] (38 C)
[17179573.664000] SCSI subsystem initialized
[17179573.672000] libata version 1.20 loaded.
[17179573.672000] ata_piix 0000:00:1f.2: version 1.05
[17179573.672000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179573.672000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179573.672000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x18B0 irq 14
[17179573.840000] ata1: dev 0 cfg 49:0f00 82:746b 83:7f69 84:6063 85:f469 86:3d49 87:6063 88:203f
[17179573.840000] ata1: dev 0 ATA-7, max UDMA/100, 195371568 sectors: LBA48
[17179573.848000] ata1: dev 0 configured for UDMA/100
[17179573.848000] scsi0 : ata_piix
[17179573.848000]   Vendor: ATA       Model: HTS541010G9SA00   Rev: MBZO
[17179573.848000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179573.848000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18B8 irq 15
[17179574.176000] ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179574.176000] ata2: dev 0 ATAPI, max UDMA/33
[17179574.176000] ata2(0): applying bridge limits
[17179574.348000] ata2: dev 0 configured for UDMA/33
[17179574.348000] scsi1 : ata_piix
[17179574.348000]   Vendor: MATSHITA  Model: DVD-RAM UJ-841S   Rev: 1.60
[17179574.348000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179574.372000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179574.372000] sda: Write Protect is off
[17179574.372000] sda: Mode Sense: 00 3a 00 00
[17179574.372000] SCSI device sda: drive cache: write back
[17179574.372000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179574.372000] sda: Write Protect is off
[17179574.372000] sda: Mode Sense: 00 3a 00 00
[17179574.372000] SCSI device sda: drive cache: write back
[17179574.372000]  sda: sda1 sda2 sda3 < sda5 >
[17179574.428000] sd 0:0:0:0: Attached scsi disk sda
[17179574.444000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[17179574.444000] Uniform CD-ROM driver Revision: 3.20
[17179574.444000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179574.832000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179574.832000] ide0: ports already in use, skipping probe
[17179574.832000] ide1: I/O resource 0x170-0x177 not free.
[17179574.832000] ide1: ports already in use, skipping probe
[17179574.868000] usbcore: registered new driver usbfs
[17179574.868000] usbcore: registered new driver hub
[17179574.868000] USB Universal Host Controller Interface driver v3.0
[17179574.868000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 233
[17179574.868000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.868000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.868000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.868000] uhci_hcd 0000:00:1d.0: irq 233, io base 0x00001820
[17179574.868000] usb usb1: configuration #1 chosen from 1 choice
[17179574.868000] hub 1-0:1.0: USB hub found
[17179574.868000] hub 1-0:1.0: 2 ports detected
[17179574.952000] ieee1394: Initialized config rom entry `ip1394'
[17179574.972000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179574.972000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.972000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.972000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.972000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x00001840
[17179574.972000] usb usb2: configuration #1 chosen from 1 choice
[17179574.972000] hub 2-0:1.0: USB hub found
[17179574.972000] hub 2-0:1.0: 2 ports detected
[17179575.076000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179575.076000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.076000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.076000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.076000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001860
[17179575.076000] usb usb3: configuration #1 chosen from 1 choice
[17179575.076000] hub 3-0:1.0: USB hub found
[17179575.076000] hub 3-0:1.0: 2 ports detected
[17179575.180000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179575.180000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179575.180000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179575.180000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179575.180000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179575.180000] usb usb4: configuration #1 chosen from 1 choice
[17179575.180000] hub 4-0:1.0: USB hub found
[17179575.180000] hub 4-0:1.0: 2 ports detected
[17179575.284000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 233
[17179575.284000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.284000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.284000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179575.284000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.284000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.284000] ehci_hcd 0000:00:1d.7: irq 233, io mem 0xdc444000
[17179575.288000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.288000] usb usb5: configuration #1 chosen from 1 choice
[17179575.288000] hub 5-0:1.0: USB hub found
[17179575.288000] hub 5-0:1.0: 8 ports detected
[17179575.316000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179575.392000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 169
[17179575.440000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[169]  MMIO=[dc006000-dc0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179575.476000] Attempting manual resume
[17179575.512000] kjournald starting.  Commit interval 5 seconds
[17179575.512000] EXT3-fs: mounted filesystem with ordered data mode.
[17179575.820000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[17179575.992000] usb 2-1: configuration #1 chosen from 1 choice
[17179587.072000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.100000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.104000] agpgart: Detected an Intel 945GM Chipset.
[17179587.104000] agpgart: Detected 7932K stolen memory.
[17179587.124000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179587.312000] hw_random: cannot enable RNG, aborting
[17179588.136000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179588.136000] sdhci: Copyright(c) Pierre Ossman
[17179588.136000] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[17179588.136000] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 185
[17179588.136000] mmc0: SDHCI at 0xdc006800 irq 185 DMA
[17179588.196000] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 185
[17179588.240000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[17179588.240000] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[17179588.260000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179588.260000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179588.260000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 50
[17179588.296000] e100: eth0: e100_probe: addr 0xdc005000, irq 50, MAC addr 00:A0:D1:5A:5D:7F
[17179588.304000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179588.308000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.552000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179588.552000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179588.576000] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179588.576000] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[17179588.576000] Yenta: Enabling burst memory read transactions
[17179588.576000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179588.576000] Yenta: Routing CardBus interrupts to PCI
[17179588.576000] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[17179588.592000] usbcore: registered new driver hiddev
[17179588.616000] input: Logitech Optical USB Mouse as /class/input/input2
[17179588.616000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
[17179588.616000] usbcore: registered new driver usbhid
[17179588.616000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179588.640000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179588.644000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[17179588.672000] ts: Compaq touchscreen protocol output
[17179588.808000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 185
[17179588.808000] Socket status: 30000006
[17179588.808000] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[17179588.808000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[17179588.808000] cs: IO port probe 0x4000-0x4fff: clean.
[17179588.808000] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[17179588.808000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179588.816000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179588.816000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179588.816000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179588.816000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179588.820000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179588.944000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 58
[17179588.944000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179589.288000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179589.360000] cs: IO port probe 0x100-0x3af: excluding 0x370-0x377
[17179589.364000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x407 0x4d0-0x4d7
[17179589.364000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.364000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.368000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.068000] lp: driver loaded but no devices found
[17179590.104000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179590.104000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.148000] Adding 1485972k swap on /dev/disk/by-uuid/176c0f80-69d9-4a90-988e-e08316f058c4.  Priority:-1 extents:1 across:1485972k
[17179590.232000] EXT3 FS on sda2, internal journal
[17179590.920000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17179591.980000] NET: Registered protocol family 17
[17179595.832000] ACPI: AC Adapter [ADP0] (off-line)
[17179595.900000] ACPI: Battery Slot [BAT0] (battery present)
[17179595.936000] ACPI: Power Button (FF) [PWRF]
[17179595.936000] ACPI: Lid Switch [LID]
[17179595.936000] ACPI: Power Button (CM) [PWRB]
[17179596.108000] ACPI: Error installing notify handler
[17179596.272000] ibm_acpi: ec object not found
[17179596.320000] pcc_acpi: loading...
[17179596.540000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179596.540000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179599.720000] [drm] Initialized drm 1.0.1 20051102
[17179599.720000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179599.720000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179600.016000] apm: BIOS not found.
[17179603.480000] Bluetooth: Core ver 2.8
[17179603.480000] NET: Registered protocol family 31
[17179603.480000] Bluetooth: HCI device and connection manager initialized
[17179603.480000] Bluetooth: HCI socket layer initialized
[17179603.508000] Bluetooth: L2CAP ver 2.8
[17179603.508000] Bluetooth: L2CAP socket layer initialized
[17179603.556000] Bluetooth: RFCOMM socket layer initialized
[17179603.556000] Bluetooth: RFCOMM TTY layer initialized
[17179603.556000] Bluetooth: RFCOMM ver 1.7
[17179615.388000] NET: Registered protocol family 10
[17179615.388000] lo: Disabled Privacy Extensions
[17179615.388000] IPv6 over IPv4 tunneling driver
[17179711.720000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179830.644000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179841.568000] eth0: no IPv6 routers present
[17179964.644000] e100: eth0: e100_watchdog: link down
[17180250.572000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17180261.340000] eth0: no IPv6 routers present
[17185969.832000] usb 2-1: USB disconnect, address 3
[17186086.740000] usb 2-1: new low speed USB device using uhci_hcd and address 4
[17186086.920000] usb 2-1: configuration #1 chosen from 1 choice
[17186086.940000] input: Logitech Optical USB Mouse as /class/input/input3
[17186086.940000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
[17190923.340000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17191049.464000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17191057.468000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17191057.472000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17191067.728000] eth0: no IPv6 routers present
[17199416.544000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by FrodoB on 2006-11-12
OK it looks like you have and Intel ipw3945. Do a search on the forums for 3945 there is a lot of thread activity on it such as this:

[http://www.ubuntuforums.org/showthread.php?t=298129&highlight=3945](http://www.ubuntuforums.org/showthread.php?t=298129&highlight=3945)

and others.

---

### Post by rvickers on 2006-11-12
Yes, I know the threads well. They're the reason I had to reinstall. I'm afraid to go tinkering too much until I know precisely what the problem is.
Thanks

---

### Post by banana989 on 2006-11-12
I'm still having problems :-/

---

### Post by rvickers on 2006-11-12
Yep, something is definitely stinky with edgy and Intel ipw3945. Since my wired is working, I think I'll wait until I see a proven way to get it to work. I've seen on some of the other posts to use dapper to fix the problem but hopefully the good people at ubuntu will fix the edgy problem soon. 
Good Luck and keep me informed if you get it working.
Thanks :)

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

