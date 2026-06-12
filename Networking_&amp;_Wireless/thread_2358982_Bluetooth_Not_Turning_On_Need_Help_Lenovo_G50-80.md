---
title: "Bluetooth Not Turning On Need Help Lenovo G50-80"
date: 2017-04-19
forum: Networking &amp; Wireless
---

### Post by kellyjoshua08 on 2017-04-19
Hello everyone recently made the switch from windows 10 currently dual booting Ubuntu 17.04 and  windows 10 going to make complete switch soon. I was having an issue with my blue tooth. My laptop came with blue-tooth functioning out of the box but now its saying it doesn't exist. :(

---

### Post by slickymaster on 2017-04-19
Thread moved to **Networking & Wireless** for a better fit

---

### Post by kellyjoshua08 on 2017-04-19
Thank you.

---

### Post by jeremy31 on 2017-04-19
Please open a terminal window- CTRL + ALT + t and enter the following and post the results
```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```

---

### Post by kellyjoshua08 on 2017-04-20
```
joshua@joshua-Lenovo-G50-80:~$ lspci -nnk00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
    Subsystem: Lenovo Haswell-ULT DRAM Controller [17aa:390b]
    Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
    Subsystem: Lenovo Haswell-ULT Integrated Graphics Controller [17aa:390b]
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: Lenovo Haswell-ULT HD Audio Controller [17aa:390b]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: Lenovo 8 Series USB xHCI HC [17aa:390b]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
    Subsystem: Lenovo 8 Series HECI [17aa:390b]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Lenovo 8 Series HD Audio Controller [17aa:390b]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
    Subsystem: Lenovo 8 Series LPC Controller [17aa:390b]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: Lenovo 8 Series SATA Controller 1 [AHCI mode] [17aa:390b]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
    Subsystem: Lenovo 8 Series SMBus Controller [17aa:390b]
    Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3821]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
joshua@joshua-Lenovo-G50-80:~$ grep -iA2net; lsusb; rfkill list all; dmesg
grep: 2net: invalid context length argument
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:014f Acer, Inc 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 2a70:f00e  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.000000] ACPI: BGRT 0x000000009CFD1000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015f5fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x15f5fb000-0x15f5fffff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000015f5fffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x0000000000085fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x0000000096f79fff]
[    0.000000]   node   0: [mem 0x000000009787a000-0x000000009c48efff]
[    0.000000]   node   0: [mem 0x000000009cfff000-0x000000009cffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000015f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000015f5fffff]
[    0.000000] On node 0 totalpages: 1028372
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3972 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9903 pages used for memmap
[    0.000000]   DMA32 zone: 633744 pages, LIFO batch:31
[    0.000000]   Normal zone: 6104 pages used for memmap
[    0.000000]   Normal zone: 390656 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics memory at 0x000000009da00000-0x000000009f9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00086000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d34000-0x95d34fff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d41000-0x95d41fff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d42000-0x95d42fff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d52000-0x95d52fff]
[    0.000000] PM: Registered nosave memory: [mem 0x96f7a000-0x97879fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9c48f000-0x9ce7efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9ce7f000-0x9cf7efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9cf7f000-0x9cffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d000000-0x9d9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9da00000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] percpu: Embedded 36 pages/cpu @ffff8bc11f200000 s107864 r8192 d31400 u262144
[    0.000000] pcpu-alloc: s107864 r8192 d31400 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1012279
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-46-generic.efi.signed root=UUID=cc7a1116-d203-4bd8-b6e2-72f759d6b1aa ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3867900K/4113488K available (8829K kernel code, 1441K rwdata, 3832K rodata, 1548K init, 1296K bss, 245588K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=512 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:33024 nr_irqs:760 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1895.647 MHz processor
[    0.000029] Calibrating delay loop (skipped), value calculated using timer frequency.. 3791.29 BogoMIPS (lpj=7582588)
[    0.000032] pid_max: default: 32768 minimum: 301
[    0.000044] ACPI: Core revision 20160422
[    0.377739] ACPI: 5 ACPI AML tables successfully acquired and loaded


[    0.379180] Security Framework initialized
[    0.379182] Yama: becoming mindful.
[    0.379201] AppArmor: AppArmor initialized
[    0.379491] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.380428] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.380860] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.380866] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.381161] CPU: Physical Processor ID: 0
[    0.381162] CPU: Processor Core ID: 0
[    0.381167] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.381167] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.381172] mce: CPU supports 7 MCE banks
[    0.381192] process: using mwait in idle threads
[    0.381196] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
[    0.381197] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.381635] Freeing SMP alternatives memory: 32K (ffffffffb9aed000 - ffffffffb9af5000)
[    0.739546] ftrace: allocating 33449 entries in 131 pages
[    0.757801] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.757803] smpboot: Max logical packages: 4
[    0.757815] DMAR: Host address width 39
[    0.757817] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.757822] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.757823] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.757827] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.757828] DMAR: RMRR base: 0x0000009ce24000 end: 0x0000009ce43fff
[    0.757829] DMAR: RMRR base: 0x0000009d800000 end: 0x0000009f9fffff
[    0.757830] DMAR: ANDD device: 1 name: \_SB.PCI0.SDMA
[    0.757831] DMAR: ANDD device: 2 name: \_SB.PCI0.SDHC
[    0.757833] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.757834] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.757835] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.757836] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    1.110571] DMAR-IR: Enabled IRQ remapping in xapic mode
[    1.110572] x2apic: IRQ remapping doesn't support X2APIC mode
[    1.111202] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.502900] TSC deadline timer enabled
[    1.502903] smpboot: CPU0: Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz (family: 0x6, model: 0x45, stepping: 0x1)
[    1.502907] Performance Events: PEBS fmt2+, Haswell events, 16-deep LBR, full-width counters, Intel PMU driver.
[    1.502951] ... version:                3
[    1.502952] ... bit width:              48
[    1.502953] ... generic registers:      4
[    1.502953] ... value mask:             0000ffffffffffff
[    1.502954] ... max period:             00007fffffffffff
[    1.502954] ... fixed-purpose events:   3
[    1.502955] ... event mask:             000000070000000f
[    1.504038] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    1.504126] x86: Booting SMP configuration:
[    1.504127] .... node  #0, CPUs:      #1 #2 #3
[    1.513407] x86: Booted up 1 node, 4 CPUs
[    1.513410] smpboot: Total of 4 processors activated (15165.17 BogoMIPS)
[    1.518028] devtmpfs: initialized
[    1.518096] x86/mm: Memory block size: 128MB
[    1.520363] evm: security.selinux
[    1.520364] evm: security.SMACK64
[    1.520364] evm: security.SMACK64EXEC
[    1.520365] evm: security.SMACK64TRANSMUTE
[    1.520365] evm: security.SMACK64MMAP
[    1.520366] evm: security.ima
[    1.520367] evm: security.capability
[    1.520432] PM: Registering ACPI NVS region [mem 0x9ce7f000-0x9cf7efff] (1048576 bytes)
[    1.520511] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    1.520553] pinctrl core: initialized pinctrl subsystem
[    1.520658] RTC time:  0:18:19, date: 04/21/17
[    1.520759] NET: Registered protocol family 16
[    1.533789] cpuidle: using governor ladder



```

---

### Post by lordgallen on 2017-04-20
I just happened to be in the networking section, and read this post. I also have a Lenovo G50-80, and I don't have any issues with Bluetooth. I am not certain that we both have the same hardware. 

```


$ lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3821]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
	Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 13d3:5727 IMC Networks 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
[    0.156947] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   34.976136] Bluetooth: Core ver 2.22
[   34.976156] Bluetooth: HCI device and connection manager initialized
[   34.976159] Bluetooth: HCI socket layer initialized
[   34.976161] Bluetooth: L2CAP socket layer initialized
[   34.976166] Bluetooth: SCO socket layer initialized
[   34.999611] Bluetooth: hci0: read Intel version: 3707100100012d0d27
[   34.999613] Bluetooth: hci0: Intel device is already patched. patch num: 27
[   35.251685] iwlwifi 0000:03:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
[   38.698443] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.698444] Bluetooth: BNEP filters: protocol multicast
[   38.698448] Bluetooth: BNEP socket layer initialized
[   49.492285] Bluetooth: RFCOMM TTY layer initialized
[   49.492295] Bluetooth: RFCOMM socket layer initialized
[   49.492304] Bluetooth: RFCOMM ver 1.11
[ 2024.677561] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 2024.677569] Bluetooth: HIDP socket layer initialized
[ 2024.684201] input: Bluetooth Mouse M336/M337/M535 as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/bluetooth/hci0/hci0:256/0005:046D:B014.0001/input/input14
[ 2024.684823] hid-generic 0005:046D:B014.0001: input,hidraw0: BLUETOOTH HID v12.00 Mouse [Bluetooth Mouse M336/M337/M535] on b4:6d:83:c9:3f:46


```

I can provide additional information if you would like.

---

### Post by jeremy31 on 2017-04-22
> **kellyjoshua08 said:**
> ```
joshua@joshua-Lenovo-G50-80:~$ lspci -nnk00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
    Subsystem: Lenovo Haswell-ULT DRAM Controller [17aa:390b]
    Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
    Subsystem: Lenovo Haswell-ULT Integrated Graphics Controller [17aa:390b]
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: Lenovo Haswell-ULT HD Audio Controller [17aa:390b]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: Lenovo 8 Series USB xHCI HC [17aa:390b]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series HECI #0 [8086:9c3a] (rev 04)
    Subsystem: Lenovo 8 Series HECI [17aa:390b]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Lenovo 8 Series HD Audio Controller [17aa:390b]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 1 [8086:9c10] (rev e4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 3 [8086:9c14] (rev e4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 8 Series LPC Controller [8086:9c43] (rev 04)
    Subsystem: Lenovo 8 Series LPC Controller [17aa:390b]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: Lenovo 8 Series SATA Controller 1 [AHCI mode] [17aa:390b]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series SMBus Controller [8086:9c22] (rev 04)
    Subsystem: Lenovo 8 Series SMBus Controller [17aa:390b]
    Kernel modules: i2c_i801
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3821]
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
joshua@joshua-Lenovo-G50-80:~$ grep -iA2net; lsusb; rfkill list all; dmesg
grep: 2net: invalid context length argument
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 5986:014f Acer, Inc 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 2a70:f00e  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.000000] ACPI: BGRT 0x000000009CFD1000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015f5fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x15f5fb000-0x15f5fffff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000015f5fffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x0000000000085fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x0000000096f79fff]
[    0.000000]   node   0: [mem 0x000000009787a000-0x000000009c48efff]
[    0.000000]   node   0: [mem 0x000000009cfff000-0x000000009cffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000015f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000015f5fffff]
[    0.000000] On node 0 totalpages: 1028372
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3972 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9903 pages used for memmap
[    0.000000]   DMA32 zone: 633744 pages, LIFO batch:31
[    0.000000]   Normal zone: 6104 pages used for memmap
[    0.000000]   Normal zone: 390656 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics memory at 0x000000009da00000-0x000000009f9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00086000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d34000-0x95d34fff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d41000-0x95d41fff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d42000-0x95d42fff]
[    0.000000] PM: Registered nosave memory: [mem 0x95d52000-0x95d52fff]
[    0.000000] PM: Registered nosave memory: [mem 0x96f7a000-0x97879fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9c48f000-0x9ce7efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9ce7f000-0x9cf7efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9cf7f000-0x9cffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9d000000-0x9d9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9da00000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] percpu: Embedded 36 pages/cpu @ffff8bc11f200000 s107864 r8192 d31400 u262144
[    0.000000] pcpu-alloc: s107864 r8192 d31400 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1012279
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-46-generic.efi.signed root=UUID=cc7a1116-d203-4bd8-b6e2-72f759d6b1aa ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3867900K/4113488K available (8829K kernel code, 1441K rwdata, 3832K rodata, 1548K init, 1296K bss, 245588K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=512 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:33024 nr_irqs:760 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1895.647 MHz processor
[    0.000029] Calibrating delay loop (skipped), value calculated using timer frequency.. 3791.29 BogoMIPS (lpj=7582588)
[    0.000032] pid_max: default: 32768 minimum: 301
[    0.000044] ACPI: Core revision 20160422
[    0.377739] ACPI: 5 ACPI AML tables successfully acquired and loaded


[    0.379180] Security Framework initialized
[    0.379182] Yama: becoming mindful.
[    0.379201] AppArmor: AppArmor initialized
[    0.379491] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.380428] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.380860] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.380866] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.381161] CPU: Physical Processor ID: 0
[    0.381162] CPU: Processor Core ID: 0
[    0.381167] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.381167] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.381172] mce: CPU supports 7 MCE banks
[    0.381192] process: using mwait in idle threads
[    0.381196] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
[    0.381197] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.381635] Freeing SMP alternatives memory: 32K (ffffffffb9aed000 - ffffffffb9af5000)
[    0.739546] ftrace: allocating 33449 entries in 131 pages
[    0.757801] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.757803] smpboot: Max logical packages: 4
[    0.757815] DMAR: Host address width 39
[    0.757817] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.757822] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.757823] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.757827] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.757828] DMAR: RMRR base: 0x0000009ce24000 end: 0x0000009ce43fff
[    0.757829] DMAR: RMRR base: 0x0000009d800000 end: 0x0000009f9fffff
[    0.757830] DMAR: ANDD device: 1 name: \_SB.PCI0.SDMA
[    0.757831] DMAR: ANDD device: 2 name: \_SB.PCI0.SDHC
[    0.757833] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.757834] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.757835] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.757836] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    1.110571] DMAR-IR: Enabled IRQ remapping in xapic mode
[    1.110572] x2apic: IRQ remapping doesn't support X2APIC mode
[    1.111202] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.502900] TSC deadline timer enabled
[    1.502903] smpboot: CPU0: Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz (family: 0x6, model: 0x45, stepping: 0x1)
[    1.502907] Performance Events: PEBS fmt2+, Haswell events, 16-deep LBR, full-width counters, Intel PMU driver.
[    1.502951] ... version:                3
[    1.502952] ... bit width:              48
[    1.502953] ... generic registers:      4
[    1.502953] ... value mask:             0000ffffffffffff
[    1.502954] ... max period:             00007fffffffffff
[    1.502954] ... fixed-purpose events:   3
[    1.502955] ... event mask:             000000070000000f
[    1.504038] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    1.504126] x86: Booting SMP configuration:
[    1.504127] .... node  #0, CPUs:      #1 #2 #3
[    1.513407] x86: Booted up 1 node, 4 CPUs
[    1.513410] smpboot: Total of 4 processors activated (15165.17 BogoMIPS)
[    1.518028] devtmpfs: initialized
[    1.518096] x86/mm: Memory block size: 128MB
[    1.520363] evm: security.selinux
[    1.520364] evm: security.SMACK64
[    1.520364] evm: security.SMACK64EXEC
[    1.520365] evm: security.SMACK64TRANSMUTE
[    1.520365] evm: security.SMACK64MMAP
[    1.520366] evm: security.ima
[    1.520367] evm: security.capability
[    1.520432] PM: Registering ACPI NVS region [mem 0x9ce7f000-0x9cf7efff] (1048576 bytes)
[    1.520511] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    1.520553] pinctrl core: initialized pinctrl subsystem
[    1.520658] RTC time:  0:18:19, date: 04/21/17
[    1.520759] NET: Registered protocol family 16
[    1.533789] cpuidle: using governor ladder



```

Either your wifi card doesn't have bluetooth or the kernel just can't find it on the USB subsystem.  If you are sure it does have bluetooth, file a bug report.. see guide @https://ubuntuforums.org/showthread.php?t=1011078
File the bug against package linux.

If you look at lordgallen's results, I see a device in the lsusb results, ID 8087:07dc Intel Corp that I know is an Intel Bluetooth device.  The lack of a HCI device showing in the rfkill list all results also indicates that you may not have bluetooth on the wireless card, you just have an ideapad_bluetooth showing that might be caused by the ideapad_laptop module.

Your result for rfkill ```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Results from lordgallen with a working bluetooth
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

The hci0 is a sure sign that a bluetooth device has been found just as phy0 is a sign that a wifi device is present

---

