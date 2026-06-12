---
title: "hp6510b wireless problem"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by munja on 2011-03-24
Hello,

I have installed Ubuntu 10.10 on hp6510b. After instalation wireless was working perfectly. Then I installed updates and restarted. Wireless button was on, but nothing shows on Panel. I tried touching the button to turn off and on again, but it wouldn't light up again.
Then restarted again, the wireless light was on, but nothing shows on ubuntu panel...

```
/sbin/iwconfig
```      says wireless exists on interface wlan0 and

```
lspci
```      lists wireless card (intel Pro/Wireless 3945 ABG) is present

Thank you for any help on this.

---

### Post by Hippytaff on 2011-03-24
Whats the output of```
rfkill list
``` and can you ping succesfully```
ping www.google.com
```

---

### Post by munja on 2011-03-24
the output of ```
rfkill list
``` is:

0: hp-wifi: Wireless LAN
[INDENT]Soft blocked: no[/INDENT]
[INDENT]Hard blocked: no[/INDENT]
1: hp-bluetooth: Bluetooth
[INDENT]Soft blocked: yes[/INDENT]
[INDENT]Hard blocked: no[/INDENT]
2: phy0: Wireless LAN
[INDENT]Soft blocked: no[/INDENT]
[INDENT]Hard blocked: no[/INDENT]

```
ping www.google.com
```

does not ping succesfully, says "unknown host www.google.com"

---

### Post by Hippytaff on 2011-03-24
Can you post the output of these commands```
lsmod | grep -i ipw3945
``` and ```
lsmod | grep -i iwl3945
``` if any
 
And```
uname -a
```

---

### Post by munja on 2011-03-24
The first one doesn't give any outputs 
The output of ```
lsmod | grep - iwl3945
``` is:
iwl3945 85550 0
iwlcore 127415 1 iwl3945
mac80211 231959 2 iwl3945,iwlcore
cfg80211 144694 3 iwl3945, iwlcore,mac80211

and the last one is:

Linux HP 2.6.35-28-generic #49-Ubuntu SMP Tue Mar1 14:40:58 UTC 2011 i686 GNU/Linux

---

### Post by Hippytaff on 2011-03-24
ok...so the correct driver is installed for the kernel version. Can I see```
iwconfig
``` and ```
dmesg
``` (when you post the output, if you could highlight it and click the # it will wrap it in [code][/code ]tags so its easier to read :-) dmesg will be a mssive output

---

### Post by munja on 2011-03-24
Ok :)
iwconfig:

```
lo    no wireless extensions
eth0    no wireless extensions
wlan0   IEEE 802.11agb
              ESSID:off/any
              Mode:Managed 
              Access Point: Not-Associated
              Tx-Poewer=15 dBm
              Retry long limit:7 
              RTS thr:off 
              Fragment the:off
              Power Managment:off
```


dmesg:
```

[    0.353266] ACPI: ACPI bus type pnp unregistered
[    0.353270] PnPBIOS: Disabled by ACPI PNP
[    0.353282] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.353285] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.353289] system 00:00: [mem 0x00100000-0x7f7fffff] could not be reserved
[    0.353298] system 00:0b: [io  0x0500-0x055f] has been reserved
[    0.353301] system 00:0b: [io  0x0800-0x080f] has been reserved
[    0.353304] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.353307] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.353313] system 00:0d: [io  0x04d0-0x04d1] has been reserved
[    0.353316] system 00:0d: [io  0x1000-0x107f] has been reserved
[    0.353318] system 00:0d: [io  0x1100-0x113f] has been reserved
[    0.353321] system 00:0d: [io  0x1200-0x121f] has been reserved
[    0.353324] system 00:0d: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.353327] system 00:0d: [mem 0xfec00000-0xfec000ff] could not be reserved
[    0.353330] system 00:0d: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.353333] system 00:0d: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.353336] system 00:0d: [mem 0xfed90000-0xfed99fff] has been reserved
[    0.353341] system 00:0e: [mem 0x000cee00-0x000cffff] has been reserved
[    0.353344] system 00:0e: [mem 0xfeda0000-0xfedbffff] has been reserved
[    0.353347] system 00:0e: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.389480] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.389485] pci 0000:00:1c.1: BAR 15: assigned [mem 0x84000000-0x841fffff 64bit pref]
[    0.389488] pci 0000:00:1c.2: BAR 15: assigned [mem 0x84200000-0x843fffff 64bit pref]
[    0.389491] pci 0000:00:1c.4: BAR 15: assigned [mem 0x84400000-0x845fffff 64bit pref]
[    0.389495] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.389498] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    0.389501] pci 0000:00:1e.0: BAR 13: assigned [io  0x7000-0x7fff]
[    0.389504] pci 0000:00:1c.0: PCI bridge to [bus 08-08]
[    0.389506] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.389519] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.389528] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.389543] pci 0000:00:1c.1: PCI bridge to [bus 10-10]
[    0.389549] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.389562] pci 0000:00:1c.1:   bridge window [mem 0xe4100000-0xe41fffff]
[    0.389572] pci 0000:00:1c.1:   bridge window [mem 0x84000000-0x841fffff 64bit pref]
[    0.389586] pci 0000:00:1c.2: PCI bridge to [bus 18-18]
[    0.389592] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    0.389605] pci 0000:00:1c.2:   bridge window [mem 0xe4000000-0xe40fffff]
[    0.389615] pci 0000:00:1c.2:   bridge window [mem 0x84200000-0x843fffff 64bit pref]
[    0.389627] pci 0000:00:1c.4: PCI bridge to [bus 28-28]
[    0.389633] pci 0000:00:1c.4:   bridge window [io  0x2000-0x3fff]
[    0.389646] pci 0000:00:1c.4:   bridge window [mem 0xe0000000-0xe3ffffff]
[    0.389654] pci 0000:00:1c.4:   bridge window [mem 0x84400000-0x845fffff 64bit pref]
[    0.389672] pci 0000:02:04.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.389675] pci 0000:02:04.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.389678] pci 0000:02:04.0: BAR 13: assigned [io  0x7000-0x70ff]
[    0.389680] pci 0000:02:04.0: BAR 14: assigned [io  0x7400-0x74ff]
[    0.389683] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.389685] pci 0000:02:04.0:   bridge window [io  0x7000-0x70ff]
[    0.389693] pci 0000:02:04.0:   bridge window [io  0x7400-0x74ff]
[    0.389703] pci 0000:02:04.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.389711] pci 0000:02:04.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.389721] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.389727] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.389740] pci 0000:00:1e.0:   bridge window [mem 0xe4200000-0xe45fffff]
[    0.389750] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.389786]   alloc irq_desc for 16 on node -1
[    0.389788]   alloc kstat_irqs on node -1
[    0.389796] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.389806] pci 0000:00:1c.0: setting latency timer to 64
[    0.389823]   alloc irq_desc for 17 on node -1
[    0.389825]   alloc kstat_irqs on node -1
[    0.389829] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.389836] pci 0000:00:1c.1: setting latency timer to 64
[    0.389858]   alloc irq_desc for 18 on node -1
[    0.389860]   alloc kstat_irqs on node -1
[    0.389864] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.389868] pci 0000:00:1c.2: setting latency timer to 64
[    0.389886] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.389895] pci 0000:00:1c.4: setting latency timer to 64
[    0.389913] pci 0000:00:1e.0: setting latency timer to 64
[    0.389938] pci 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.389949] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.389951] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.389954] pci_bus 0000:10: resource 0 [io  0x5000-0x5fff]
[    0.389956] pci_bus 0000:10: resource 1 [mem 0xe4100000-0xe41fffff]
[    0.389959] pci_bus 0000:10: resource 2 [mem 0x84000000-0x841fffff 64bit pref]
[    0.389961] pci_bus 0000:18: resource 0 [io  0x6000-0x6fff]
[    0.389964] pci_bus 0000:18: resource 1 [mem 0xe4000000-0xe40fffff]
[    0.389966] pci_bus 0000:18: resource 2 [mem 0x84200000-0x843fffff 64bit pref]
[    0.389969] pci_bus 0000:28: resource 0 [io  0x2000-0x3fff]
[    0.389971] pci_bus 0000:28: resource 1 [mem 0xe0000000-0xe3ffffff]
[    0.389973] pci_bus 0000:28: resource 2 [mem 0x84400000-0x845fffff 64bit pref]
[    0.389976] pci_bus 0000:02: resource 0 [io  0x7000-0x7fff]
[    0.389978] pci_bus 0000:02: resource 1 [mem 0xe4200000-0xe45fffff]
[    0.389981] pci_bus 0000:02: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.389983] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.389986] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.389988] pci_bus 0000:03: resource 0 [io  0x7000-0x70ff]
[    0.389990] pci_bus 0000:03: resource 1 [io  0x7400-0x74ff]
[    0.389993] pci_bus 0000:03: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.389995] pci_bus 0000:03: resource 3 [mem 0x88000000-0x8bffffff]
[    0.390038] NET: Registered protocol family 2
[    0.390105] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.390365] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.390839] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.391073] TCP: Hash tables configured (established 131072 bind 65536)
[    0.391075] TCP reno registered
[    0.391078] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.391088] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.391164] NET: Registered protocol family 1
[    0.391182] pci 0000:00:02.0: Boot video device
[    0.391532] PCI: CLS 64 bytes, default 64
[    0.391745] cpufreq-nforce2: No nForce2 chipset.
[    0.391773] Scanning for low memory corruption every 60 seconds
[    0.391917] audit: initializing netlink socket (disabled)
[    0.391927] type=2000 audit(1300969915.388:1): initialized
[    0.402059] highmem bounce pool size: 64 pages
[    0.402065] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.403508] VFS: Disk quotas dquot_6.5.2
[    0.403572] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.404157] fuse init (API version 7.14)
[    0.404241] msgmni has been set to 1683
[    0.412960] Freeing initrd memory: 10500k freed
[    0.420992] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.420996] io scheduler noop registered
[    0.420998] io scheduler deadline registered
[    0.421014] io scheduler cfq registered (default)
[    0.421153] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.421255]   alloc irq_desc for 40 on node -1
[    0.421257]   alloc kstat_irqs on node -1
[    0.421275] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.421429] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.421523]   alloc irq_desc for 41 on node -1
[    0.421525]   alloc kstat_irqs on node -1
[    0.421540] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.421695] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.421786]   alloc irq_desc for 42 on node -1
[    0.421788]   alloc kstat_irqs on node -1
[    0.421803] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.421965] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.422065]   alloc irq_desc for 43 on node -1
[    0.422067]   alloc kstat_irqs on node -1
[    0.422082] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.422257] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.422354] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.422444] intel_idle: MWAIT substates: 0x22220
[    0.422446] intel_idle: does not run on family 6 model 15
[    0.426298] ACPI: AC Adapter [C239] (on-line)
[    0.426380] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.426387] ACPI: Sleep Button [C2BF]
[    0.426431] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.426495] ACPI: Lid Switch [C153]
[    0.426544] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.426547] ACPI: Power Button [PWRF]
[    0.426772] ACPI: Fan [C3BC] (off)
[    0.426952] ACPI: Fan [C3BD] (off)
[    0.427131] ACPI: Fan [C3BE] (off)
[    0.427314] ACPI: Fan [C3BF] (off)
[    0.427494] ACPI: Fan [C3C0] (off)
[    0.427776] ACPI: acpi_idle registered with cpuidle
[    0.430287] Monitor-Mwait will be used to enter C-1 state
[    0.430308] Monitor-Mwait will be used to enter C-2 state
[    0.430327] Monitor-Mwait will be used to enter C-3 state
[    0.430332] Marking TSC unstable due to TSC halts in idle
[    0.430401] Switching to clocksource hpet
[    0.459143] thermal LNXTHERM:01: registered as thermal_zone0
[    0.459151] ACPI: Thermal Zone [TZ0] (65 C)
[    0.463336] thermal LNXTHERM:02: registered as thermal_zone1
[    0.463344] ACPI: Thermal Zone [TZ1] (62 C)
[    0.467375] thermal LNXTHERM:03: registered as thermal_zone2
[    0.467383] ACPI: Thermal Zone [TZ3] (49 C)
[    0.477491] thermal LNXTHERM:04: registered as thermal_zone3
[    0.477499] ACPI: Thermal Zone [TZ4] (20 C)
[    0.481200] thermal LNXTHERM:05: registered as thermal_zone4
[    0.481208] ACPI: Thermal Zone [TZ5] (75 C)
[    0.481309] ERST: Table is not found!
[    0.481424] ACPI: Battery Slot [C23B] (battery absent)
[    0.481475] isapnp: Scanning for PnP cards...
[    0.487265] ACPI: Battery Slot [C23A] (battery absent)
[    0.487296] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.488828] brd: module loaded
[    0.489381] loop: module loaded
[    0.489542] ata_piix 0000:00:1f.1: version 2.13
[    0.489558] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.489610] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.489701] scsi0 : ata_piix
[    0.489773] scsi1 : ata_piix
[    0.490302] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x40c0 irq 14
[    0.490305] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x40c8 irq 15
[    0.490616] Fixed MDIO Bus: probed
[    0.490648] PPP generic driver version 2.4.2
[    0.490680] tun: Universal TUN/TAP device driver, 1.6
[    0.490682] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.490760] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.490787] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.490802] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.490808] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.490840] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.490887] ehci_hcd 0000:00:1a.7: debug port 1
[    0.494795] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.494814] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe4800000
[    0.498910] ata2: port disabled. ignoring.
[    0.509022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.509129] hub 1-0:1.0: USB hub found
[    0.509134] hub 1-0:1.0: 4 ports detected
[    0.509223]   alloc irq_desc for 20 on node -1
[    0.509225]   alloc kstat_irqs on node -1
[    0.509231] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.509245] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.509251] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.509286] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.509326] ehci_hcd 0000:00:1d.7: debug port 1
[    0.513226] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.513242] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe4808000
[    0.529018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.529127] hub 2-0:1.0: USB hub found
[    0.529131] hub 2-0:1.0: 6 ports detected
[    0.529206] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.529219] uhci_hcd: USB Universal Host Controller Interface driver
[    0.529240] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.529249] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.529255] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.529285] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.529329] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004020
[    0.529445] hub 3-0:1.0: USB hub found
[    0.529449] hub 3-0:1.0: 2 ports detected
[    0.529517] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.529528] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.529534] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.529568] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.529613] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00004040
[    0.529740] hub 4-0:1.0: USB hub found
[    0.529744] hub 4-0:1.0: 2 ports detected
[    0.529809] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.529817] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.529823] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.529852] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.529886] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00004060
[    0.530003] hub 5-0:1.0: USB hub found
[    0.530007] hub 5-0:1.0: 2 ports detected
[    0.530071]   alloc irq_desc for 21 on node -1
[    0.530073]   alloc kstat_irqs on node -1
[    0.530078] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.530088] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.530094] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.530126] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.530171] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00004080
[    0.530286] hub 6-0:1.0: USB hub found
[    0.530290] hub 6-0:1.0: 2 ports detected
[    0.530356] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.530365] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.530371] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.530401] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.530436] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000040a0
[    0.530551] hub 7-0:1.0: USB hub found
[    0.530555] hub 7-0:1.0: 2 ports detected
[    0.530695] PNP: PS/2 Controller [PNP0303:C298,PNP0f13:C299] at 0x60,0x64 irq 1,12
[    0.532327] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.533027] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.533034] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.533036] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.533039] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.533042] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.533094] mice: PS/2 mouse device common for all mice
[    0.533227] rtc_cmos 00:07: RTC can wake from S4
[    0.533260] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.533298] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.533394] device-mapper: uevent: version 1.0.3
[    0.533489] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.533559] device-mapper: multipath: version 1.1.1 loaded
[    0.533562] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.533668] EISA: Probing bus 0 at eisa.0
[    0.533677] Cannot allocate resource for EISA slot 1
[    0.533679] Cannot allocate resource for EISA slot 2
[    0.533681] Cannot allocate resource for EISA slot 3
[    0.533683] Cannot allocate resource for EISA slot 4
[    0.533685] Cannot allocate resource for EISA slot 5
[    0.533687] Cannot allocate resource for EISA slot 6
[    0.533689] Cannot allocate resource for EISA slot 7
[    0.533697] EISA: Detected 0 cards.
[    0.533834] cpuidle: using governor ladder
[    0.533933] cpuidle: using governor menu
[    0.534229] TCP cubic registered
[    0.534355] NET: Registered protocol family 10
[    0.534705] lo: Disabled Privacy Extensions
[    0.534937] NET: Registered protocol family 17
[    0.541061] Using IPI No-Shortcut mode
[    0.541137] PM: Resume from disk failed.
[    0.541152] registered taskstats version 1
[    0.541769]   Magic number: 3:534:532
[    0.541777] bdi 1:10: hash matches
[    0.541867] rtc_cmos 00:07: setting system clock to 2011-03-24 12:31:56 UTC (1300969916)
[    0.541870] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.541872] EDD information not available.
[    0.557502] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.677642] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, HH18, max MWDMA2
[    0.709293] ata1.00: configured for MWDMA2
[    0.839108] isapnp: No Plug & Play device found
[    0.846398] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D HH18 PQ: 0 ANSI: 5
[    0.884901] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.884904] Uniform CD-ROM driver Revision: 3.20
[    0.884987] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.885034] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.885139] Freeing unused kernel memory: 688k freed
[    0.885547] Write protecting the kernel text: 4936k
[    0.885605] Write protecting the kernel read-only data: 1980k
[    0.902052] udev[85]: starting version 163
[    0.968173] tg3.c:v3.110 (April 9, 2010)
[    0.968236] tg3 0000:18:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.968247] tg3 0000:18:00.0: setting latency timer to 64
[    1.002342] ahci 0000:00:1f.2: version 3.0
[    1.002364] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.002433]   alloc irq_desc for 44 on node -1
[    1.002436]   alloc kstat_irqs on node -1
[    1.002452] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.002498] ahci: SSS flag set, parallel bus scan disabled
[    1.002531] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    1.002534] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc 
[    1.002545] ahci 0000:00:1f.2: setting latency timer to 64
[    1.006522] firewire_ohci 0000:02:04.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.031478] scsi2 : ahci
[    1.051175] scsi3 : ahci
[    1.067913] scsi4 : ahci
[    1.068086] ata3: SATA max UDMA/133 abar m2048@0xe4809000 port 0xe4809100 irq 44
[    1.068089] ata4: DUMMY
[    1.068091] ata5: DUMMY
[    1.088031] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[    1.136037] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    1.148029] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[    1.156036] firewire_ohci: Added fw-ohci device 0000:02:04.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    1.209012] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[    1.210159] tg3 0000:18:00.0: eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address 00:1a:4b:75:10:d5
[    1.210162] tg3 0000:18:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.210166] tg3 0000:18:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.210168] tg3 0000:18:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.388089] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.393175] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.393179] ata3.00: ACPI cmd b1/c1:00:00:00:00:a0 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.393244] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[    1.393248] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.393706] ata3.00: ATA-7: TOSHIBA MK1637GSX, DL032C, max UDMA/100
[    1.393709] ata3.00: 312581808 sectors, multi 16: LBA48 
[    1.395954] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.395958] ata3.00: ACPI cmd b1/c1:00:00:00:00:a0 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.396027] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[    1.396031] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.396512] ata3.00: configured for UDMA/100
[    1.413134] ata3.00: configured for UDMA/100
[    1.413137] ata3: EH complete
[    1.413296] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL03 PQ: 0 ANSI: 5
[    1.413434] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.413529] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.413694] sd 2:0:0:0: [sda] Write Protect is off
[    1.413697] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.413764] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.413937]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8
[    1.540087] usb 7-2: new low speed USB device using uhci_hcd and address 2
[    1.547795]  sda9 >
[    1.562499] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.648146] firewire_core: created device fw0: GUID 00023f9929d54c0e, S400
[    1.729311] usbcore: registered new interface driver hiddev
[    1.742955] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input4
[    1.743040] generic-usb 0003:046D:C052.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    1.743055] usbcore: registered new interface driver usbhid
[    1.743057] usbhid: USB HID core driver
[    2.485852] REISERFS (device sda3): found reiserfs format "3.6" with standard journal
[    2.485861] REISERFS (device sda3): using ordered data mode
[    2.488799] REISERFS (device sda3): journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    2.489038] REISERFS (device sda3): checking transaction log (sda3)
[    2.515601] REISERFS (device sda3): Using r5 hash to sort names
[    3.544275] Adding 1000444k swap on /dev/sda2.  Priority:-1 extents:1 across:1000444k 
[    3.710245] udev[419]: starting version 163
[    4.294527] parport_pc 00:02: reported by Plug and Play ACPI
[    4.294607] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    4.311813] lp: driver loaded but no devices found
[    4.393245] lp0: using parport0 (interrupt-driven).
[    4.426239] ppdev: user-space parallel port driver
[    4.455111] Linux agpgart interface v0.103
[    4.456417] tpm_tis 00:03: 1.2 TPM (device-id 0xB, rev-id 16)
[    4.496231] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    4.497452] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    4.498606] input: HP WMI hotkeys as /devices/virtual/input/input5
[    4.503951] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    4.592388] type=1400 audit(1300969920.547:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=742 comm="apparmor_parser"
[    4.592406] type=1400 audit(1300969920.547:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=741 comm="apparmor_parser"
[    4.593169] type=1400 audit(1300969920.547:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=742 comm="apparmor_parser"
[    4.593179] type=1400 audit(1300969920.547:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=741 comm="apparmor_parser"
[    4.593532] type=1400 audit(1300969920.547:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=742 comm="apparmor_parser"
[    4.593550] type=1400 audit(1300969920.547:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=741 comm="apparmor_parser"
[    4.621889] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:30c0]
[    4.748749] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 16
[    4.748755] yenta_cardbus 0000:02:04.0: Socket status: 30000006
[    4.748759] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[    4.748769] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[    4.748773] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x70ff 0x7400-0x74ff
[    4.756203] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe4200000-0xe45fffff]
[    4.756206] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe4200000-0xe45fffff: excluding 0xe4200000-0xe423ffff
[    4.756220] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[    4.756223] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[    4.823218] lis3lv02d: hardware type NC651xx found.
[    4.823950] lis3lv02d: 12 bits sensor found
[    4.899451] [drm] Initialized drm 1.1.0 20060810
[    4.965496] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[    4.965626] Registered led device: hp::hddprotect
[    4.965646] lis3lv02d driver loaded.
[    4.991327] cfg80211: Calling CRDA to update world regulatory domain
[    5.092995] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[    5.095311] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[    5.096280] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    5.097101] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    5.098004] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
[    5.098064] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[    5.098124] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[    5.098183] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    5.195607] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.195614] i915 0000:00:02.0: setting latency timer to 64
[    5.218843]   alloc irq_desc for 45 on node -1
[    5.218847]   alloc kstat_irqs on node -1
[    5.218858] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    5.218871] [drm] set up 7M of stolen space
[    5.258826] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000/0x0
[    5.258831] serio: Synaptics pass-through port at isa0060/serio4/input0
[    5.299345] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[    5.324450] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    5.324763] [drm] initialized overlay support
[    5.344099] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    5.344102] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    5.345011] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.345931] iwl3945 0000:10:00.0: setting latency timer to 64
[    5.402090] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    5.402093] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    5.403934]   alloc irq_desc for 46 on node -1
[    5.403936]   alloc kstat_irqs on node -1
[    5.404462] iwl3945 0000:10:00.0: irq 46 for MSI/MSI-X
[    5.621051] Skipping EDID probe due to cached edid
[    5.815969] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    5.987751] Console: switching to colour frame buffer device 160x50
[    5.991005] fb0: inteldrmfb frame buffer device
[    5.991007] drm: registered panic notifier
[    5.991011] Slow work thread pool: Starting up
[    5.991100] Slow work thread pool: Ready
[    5.993599] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x0000000000000004) is beyond end of object (20100428/exoparg2-418)
[    5.993614] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.C003.C098._DOD] (Node f7021588), AE_AML_PACKAGE_LIMIT
[    5.993643] ACPI Exception: AE_AML_PACKAGE_LIMIT, Evaluating _DOD (20100428/video-1937)
[    5.994796] acpi device:00: registered as cooling_device7
[    5.996197] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    5.996310] ACPI: Video Device [C098] (multi-head: yes  rom: no  post: no)
[    5.996416] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.008039] Skipping EDID probe due to cached edid
[    7.012790] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[    7.012835] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[    7.012845] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.012908]   alloc irq_desc for 47 on node -1
[    7.012910]   alloc kstat_irqs on node -1
[    7.012925] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    7.012960] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.780017] REISERFS (device sda8): found reiserfs format "3.6" with standard journal
[    7.780036] REISERFS (device sda8): using ordered data mode
[    7.780271] REISERFS (device sda8): journal params: device sda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    7.780583] REISERFS (device sda8): checking transaction log (sda8)
[    7.799781] REISERFS (device sda8): Using r5 hash to sort names
[    7.871161] REISERFS (device sda1): found reiserfs format "3.6" with standard journal
[    7.871181] REISERFS (device sda1): using ordered data mode
[    7.871425] REISERFS (device sda1): journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    7.871758] REISERFS (device sda1): checking transaction log (sda1)
[    7.885968] REISERFS (device sda1): Using r5 hash to sort names
[    8.114145] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[    8.114163] REISERFS (device sda7): using ordered data mode
[    8.114405] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    8.114688] REISERFS (device sda7): checking transaction log (sda7)
[    8.143953] REISERFS (device sda7): Using r5 hash to sort names
[    8.478937] REISERFS (device sda5): found reiserfs format "3.6" with standard journal
[    8.478959] REISERFS (device sda5): using ordered data mode
[    8.483221] REISERFS (device sda5): journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    8.483501] REISERFS (device sda5): checking transaction log (sda5)
[    8.521157] REISERFS (device sda5): Using r5 hash to sort names
[    9.113013] EXT3-fs: barriers not enabled
[    9.127377] kjournald starting.  Commit interval 5 seconds
[    9.129725] EXT3-fs (sda9): using internal journal
[    9.129730] EXT3-fs (sda9): mounted filesystem with ordered data mode
[    9.438761] EXT3-fs: barriers not enabled
[    9.438968] kjournald starting.  Commit interval 5 seconds
[    9.439201] EXT3-fs (sda6): using internal journal
[    9.439210] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   10.771666] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[   10.853763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.818055] type=1400 audit(1300969927.771:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1066 comm="apparmor_parser"
[   11.818832] type=1400 audit(1300969927.771:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1066 comm="apparmor_parser"
[   12.623588] type=1400 audit(1300969928.575:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1095 comm="apparmor_parser"
[   12.624250] type=1400 audit(1300969928.579:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1095 comm="apparmor_parser"
[   12.624591] type=1400 audit(1300969928.579:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1095 comm="apparmor_parser"
[   12.724564] type=1400 audit(1300969928.679:13): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1094 comm="apparmor_parser"
[   12.728612] type=1400 audit(1300969928.683:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1098 comm="apparmor_parser"
[   12.729414] type=1400 audit(1300969928.683:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1098 comm="apparmor_parser"
[   12.771776] type=1400 audit(1300969928.723:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1099 comm="apparmor_parser"
[   12.978505] type=1400 audit(1300969928.935:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1096 comm="apparmor_parser"
[   15.235761]   alloc irq_desc for 48 on node -1
[   15.235764]   alloc kstat_irqs on node -1
[   15.235782] tg3 0000:18:00.0: irq 48 for MSI/MSI-X
[   15.264925] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.116132] Skipping EDID probe due to cached edid
[   17.420108] Skipping EDID probe due to cached edid
[   19.973093] Skipping EDID probe due to cached edid
[   20.289063] Skipping EDID probe due to cached edid
[   20.593063] Skipping EDID probe due to cached edid
[   20.897063] Skipping EDID probe due to cached edid
[   34.329076] Skipping EDID probe due to cached edid
[   34.640098] Skipping EDID probe due to cached edid
[   34.952093] Skipping EDID probe due to cached edid
[   35.257058] Skipping EDID probe due to cached edid
[   39.644057] Skipping EDID probe due to cached edid
[   41.440065] Skipping EDID probe due to cached edid
[  786.505016] NET: Registered protocol family 24
[ 1687.372092] Skipping EDID probe due to cached edid
[ 3699.133124] Skipping EDID probe due to cached edid
[ 5944.333110] Skipping EDID probe due to cached edid
[ 7332.952075] Skipping EDID probe due to cached edid
[ 7757.824120] Skipping EDID probe due to cached edid
 


```

---

### Post by Hippytaff on 2011-03-24
Can you see if ```
sudo ifconfig wlan0 up
``` kick starts it? and can you post the dmesg output to see if the driver is being loaded at boot correctly

---

### Post by munja on 2011-03-24
```
sudo ifconfig wlan0 up
```

does not work (I tried it before as well...)

I just edited the previous post and added the output of dmesg

---

### Post by Hippytaff on 2011-03-24
```
[    5.344102] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    5.345011] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.345931] iwl3945 0000:10:00.0: setting latency timer to 64
[    5.402090] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    5.402093] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
```
 
The driver seems to be loading without any errors.
 
If you right click on the Network Manager icon do you see any wireless networks?

---

### Post by munja on 2011-03-24
I don't see the Network Manager icon...

---

### Post by Hippytaff on 2011-03-24
The one that looks like a radar thing on the top right

---

### Post by munja on 2011-03-24
yeah, it's not there. Tried removing and adding Notification area but it didn't appear. It was there when ubuntu was first installed and after restart it disapeared.
Network Manager is installed and according to Startup Applications it starts when Ubuntu is booted.

---

### Post by Hippytaff on 2011-03-24
what happens when you do this ```
sudo cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by munja on 2011-03-24
It says:
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

### Post by Hippytaff on 2011-03-24
do you have any other laptops pcs with wireless. Does the router work ok with those?
 
I've PM'd someone to have a look at the thread in case I'm over looking something, but they are not online right now so if you can wait we will endeavour to resolve this yet :-)

---

### Post by munja on 2011-03-24
Ok, thanks for your help.
My router is working ok and wireless on another computer is working as well.

---

### Post by Hippytaff on 2011-03-24
If the worst comes to the worst you can try using the windows XP driver with Ndisgtk. If you can get a copy of the xp driver you need to extract the .inf and .sys files to a folder. then install ndisgtk```
sudo apt-get install ndisgtk
``` then open ndisgtk```
gksudo ndisgtk
``` then point ndisgtk at the .inf file. It should install the xp driver and blacklist the current driver. But this is probably a last resort.

---

### Post by munja on 2011-03-24
I think Network Manager was creating problems because now I removed it and installed Wicd Network Manager and now my wireless is working and showing available networks. 

Thanks for your help :)

---

### Post by Hippytaff on 2011-03-24
Excellent
 
Glad you sorted it. Remember to mark the thread as solved in the thread tools at the top of the page :-)

---

