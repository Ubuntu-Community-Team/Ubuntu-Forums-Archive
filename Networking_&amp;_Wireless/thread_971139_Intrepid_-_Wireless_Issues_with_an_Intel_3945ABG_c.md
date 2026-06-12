---
title: "Intrepid - Wireless Issues with an Intel 3945ABG card."
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Hekerr on 2008-11-04
Okay, so I recently bought an Fujitsi Siemens Li2735 laptop.

I've played around ubuntu a bit and now I seriously want to get this wireless card to work. A while ago I made a post about this problem but no-one responded. I'm going to post a few command i/o then describe my problem.

```
 kerr@kerr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


```

```
kerr@kerr-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:ce:1e:81
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.80.38 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:6d:1c:df
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:e7:55:21:12:c7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```


```
kerr@kerr-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ce:1e:81  
          inet addr:192.168.80.38  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fece:1e81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11039331 (11.0 MB)  TX bytes:607170 (607.1 KB)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16346 (16.3 KB)  TX bytes:16346 (16.3 KB)

```

```
kerr@kerr-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ce:1e:81  
          inet addr:192.168.80.38  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fece:1e81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11039571 (11.0 MB)  TX bytes:607170 (607.1 KB)
          Interrupt:219 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16346 (16.3 KB)  TX bytes:16346 (16.3 KB)

pan0      Link encap:Ethernet  HWaddr 1e:e7:55:21:12:c7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:6d:1c:df  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-6D-1C-DF-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
kerr@kerr-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device

kerr@kerr-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

kerr@kerr-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured

```

```
 [    0.581151] ACPI: bus type pnp registered
[    0.588102] pnp: PnP ACPI: found 10 devices
[    0.588102] ACPI: ACPI bus type pnp unregistered
[    0.588102] PnPBIOS: Disabled by ACPI PNP
[    0.588102] PCI: Using ACPI for IRQ routing
[    0.596040] NET: Registered protocol family 8
[    0.596043] NET: Registered protocol family 20
[    0.596058] NetLabel: Initializing
[    0.596058] NetLabel:  domain hash size = 128
[    0.596058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.596062] NetLabel:  unlabeled traffic allowed by default
[    0.596070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.596075] hpet0: 3 64-bit timers, 14318180 Hz
[    0.597553] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.597556]    actual entries 65620
[    0.597649] AppArmor: AppArmor Filesystem Enabled
[    0.597677] ACPI: RTC can wake from S4
[    0.600040] Switched to high resolution mode on CPU 0
[    0.600529] Switched to high resolution mode on CPU 1
[    0.604021] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.604024] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.604027] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.604030] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.604034] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.604037] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.604040] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.604048] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    0.604055] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.604058] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.604061] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.604064] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.604067] system 00:06: iomem range 0xff800000-0xff800fff could not be reserved
[    0.639184] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.639188] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.639195] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.639201] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.639210] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.639214] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.639221] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.639226] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.639235] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:08
[    0.639239] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.639245] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
[    0.639251] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.639260] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:10
[    0.639262] pci 0000:00:1e.0:   IO window: disabled
[    0.639268] pci 0000:00:1e.0:   MEM window: disabled
[    0.639273] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.639292] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.639298] pci 0000:00:1c.0: setting latency timer to 64
[    0.639309] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.639314] pci 0000:00:1c.1: setting latency timer to 64
[    0.639325] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.639330] pci 0000:00:1c.2: setting latency timer to 64
[    0.639340] pci 0000:00:1e.0: setting latency timer to 64
[    0.639344] bus: 00 index 0 io port: [0, ffff]
[    0.639346] bus: 00 index 1 mmio: [0, ffffffff]
[    0.639348] bus: 02 index 0 io port: [2000, 2fff]
[    0.639350] bus: 02 index 1 mmio: [f6000000, f7ffffff]
[    0.639352] bus: 02 index 2 mmio: [f0000000, f1ffffff]
[    0.639354] bus: 02 index 3 mmio: [0, 0]
[    0.639356] bus: 04 index 0 io port: [3000, 3fff]
[    0.639358] bus: 04 index 1 mmio: [f8000000, f9ffffff]
[    0.639361] bus: 04 index 2 mmio: [f2000000, f3ffffff]
[    0.639362] bus: 04 index 3 mmio: [0, 0]
[    0.639364] bus: 08 index 0 io port: [4000, 4fff]
[    0.639367] bus: 08 index 1 mmio: [fa000000, fbffffff]
[    0.639369] bus: 08 index 2 mmio: [f4000000, f5ffffff]
[    0.639371] bus: 08 index 3 mmio: [0, 0]
[    0.639373] bus: 10 index 0 mmio: [0, 0]
[    0.639374] bus: 10 index 1 mmio: [0, 0]
[    0.639376] bus: 10 index 2 mmio: [0, 0]
[    0.639378] bus: 10 index 3 io port: [0, ffff]
[    0.639380] bus: 10 index 4 mmio: [0, ffffffff]
[    0.639388] NET: Registered protocol family 2
[    0.652048] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.652277] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.652651] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.652847] TCP: Hash tables configured (established 131072 bind 65536)
[    0.652850] TCP reno registered
[    0.656071] NET: Registered protocol family 1
[    0.656185] checking if image is initramfs... it is
[    1.341991] Freeing initrd memory: 7988k freed
[    1.342173] Simple Boot Flag at 0x36 set to 0x1
[    1.343106] audit: initializing netlink socket (disabled)
[    1.343130] type=2000 audit(1225839629.341:1): initialized
[    1.349036] highmem bounce pool size: 64 pages
[    1.349042] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.351331] VFS: Disk quotas dquot_6.5.1
[    1.351416] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.351515] msgmni has been set to 1725
[    1.351629] io scheduler noop registered
[    1.351632] io scheduler anticipatory registered
[    1.351634] io scheduler deadline registered
[    1.351645] io scheduler cfq registered (default)
[    1.351659] pci 0000:00:02.0: Boot video device
[    1.351902] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.351956] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.352010] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.352053] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.352092] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.352207] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.352259] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.352310] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.352347] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.352384] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.352498] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.352550] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.352601] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.352642] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.352680] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.353017] isapnp: Scanning for PnP cards...
[    1.707114] isapnp: No Plug & Play device found
[    1.739090] hpet_resources: 0xfed00000 is busy
[    1.739156] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.741387] brd: module loaded
[    1.741454] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.741574] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.752007] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.758300] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.758305] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.758308] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.758311] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.758313] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.758658] mice: PS/2 mouse device common for all mice
[    1.758781] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.758813] rtc0: alarms up to one month, y3k, hpet irqs
[    1.758936] EISA: Probing bus 0 at eisa.0
[    1.758943] Cannot allocate resource for EISA slot 1
[    1.758946] Cannot allocate resource for EISA slot 2
[    1.758948] Cannot allocate resource for EISA slot 3
[    1.758950] Cannot allocate resource for EISA slot 4
[    1.758970] EISA: Detected 0 cards.
[    1.758973] cpuidle: using governor ladder
[    1.758976] cpuidle: using governor menu
[    1.759477] TCP cubic registered
[    1.759502] Using IPI No-Shortcut mode
[    1.759667] registered taskstats version 1
[    1.759793]   Magic number: 0:732:48
[    1.759895] rtc_cmos 00:07: setting system clock to 2008-11-04 23:00:31 UTC (1225839631)
[    1.759898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.759900] EDD information not available.
[    1.760134] Freeing unused kernel memory: 424k freed
[    1.760170] Write protecting the kernel text: 2576k
[    1.760196] Write protecting the kernel read-only data: 936k
[    1.800019] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.889625] fuse init (API version 7.9)
[    1.921513] ACPI: SSDT BF6D3760, 0238 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[    1.921954] ACPI: SSDT BF6D30F1, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[    1.940032] Monitor-Mwait will be used to enter C-1 state
[    1.940036] Monitor-Mwait will be used to enter C-2 state
[    1.940039] Monitor-Mwait will be used to enter C-3 state
[    1.940232] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.940290] processor ACPI0007:00: registered as cooling_device0
[    1.940654] ACPI: SSDT BF6D3998, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20060912)
[    1.941044] ACPI: SSDT BF6D36DB, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20060912)
[    1.941946] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.941993] processor ACPI0007:01: registered as cooling_device1
[    1.949004] Marking TSC unstable due to TSC halts in idle
[    2.072789] thermal LNXTHERM:01: registered as thermal_zone0
[    2.085905] ACPI: Thermal Zone [TZS0] (50 C)
[    2.092814] thermal LNXTHERM:02: registered as thermal_zone1
[    2.096346] ACPI: Thermal Zone [TZS1] (45 C)
[    2.389354] usbcore: registered new interface driver usbfs
[    2.389377] usbcore: registered new interface driver hub
[    2.398249] usbcore: registered new device driver usb
[    2.401525] USB Universal Host Controller Interface driver v3.0
[    2.401579] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.401589] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.401593] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.401635] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.401674] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    2.401829] usb usb1: configuration #1 chosen from 1 choice
[    2.401855] hub 1-0:1.0: USB hub found
[    2.401863] hub 1-0:1.0: 2 ports detected
[    2.471638] No dock devices found.
[    2.501464] SCSI subsystem initialized
[    2.509709] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.509719] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.509724] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.509748] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.509786] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    2.509880] usb usb2: configuration #1 chosen from 1 choice
[    2.509906] hub 2-0:1.0: USB hub found
[    2.509913] hub 2-0:1.0: 2 ports detected
[    2.517598] libata version 3.00 loaded.
[    2.612452] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.612472] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.612476] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.612502] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    2.616429] ehci_hcd 0000:00:1a.7: debug port 1
[    2.616437] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.616452] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc404800
[    2.656020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.656159] usb usb3: configuration #1 chosen from 1 choice
[    2.656196] hub 3-0:1.0: USB hub found
[    2.656205] hub 3-0:1.0: 4 ports detected
[    2.760440] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.760452] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.760456] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.760484] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.760524] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    2.760617] usb usb4: configuration #1 chosen from 1 choice
[    2.760644] hub 4-0:1.0: USB hub found
[    2.760652] hub 4-0:1.0: 2 ports detected
[    2.864497] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.864508] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.864512] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.864538] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    2.864576] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    2.864672] usb usb5: configuration #1 chosen from 1 choice
[    2.864699] hub 5-0:1.0: USB hub found
[    2.864706] hub 5-0:1.0: 2 ports detected
[    2.968414] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.968421] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.968425] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.968454] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    2.968485] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    2.968576] usb usb6: configuration #1 chosen from 1 choice
[    2.968601] hub 6-0:1.0: USB hub found
[    2.968607] hub 6-0:1.0: 2 ports detected
[    3.000115] Clocksource tsc unstable (delta = -155738317 ns)
[    3.072524] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.072540] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.072544] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.072570] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.076483] ehci_hcd 0000:00:1d.7: debug port 1
[    3.076490] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.076496] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    3.092141] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.092287] usb usb7: configuration #1 chosen from 1 choice
[    3.092344] hub 7-0:1.0: USB hub found
[    3.092351] hub 7-0:1.0: 6 ports detected
[    3.197677] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.197711] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.197725] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.197754] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.197765] ahci 0000:00:1f.2: version 3.0
[    3.197769] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.197779] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.197789] r8169 0000:02:00.0: setting latency timer to 64
[    3.197952] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    3.197955] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    3.197962] ahci 0000:00:1f.2: setting latency timer to 64
[    3.198238] eth0: RTL8101e at 0xf889a000, 00:0a:e4:ce:1e:81, XID 34200000 IRQ 219
[    3.199862] scsi0 : ahci
[    3.200305] scsi1 : ahci
[    3.200403] scsi2 : ahci
[    3.200604] ata1: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 220
[    3.200608] ata2: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 220
[    3.200611] ata3: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404200 irq 220
[    3.520158] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.521565] ata1.00: _GTF unexpected object type 0x1
[    3.522682] ata1.00: ATA-7: ST9160821AS, 3.ALE, max UDMA/133
[    3.522689] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.527098] ata1.00: _GTF unexpected object type 0x1
[    3.528240] ata1.00: configured for UDMA/133
[    3.864133] ata2: SATA link down (SStatus 0 SControl 300)
[    4.200137] ata3: SATA link down (SStatus 0 SControl 300)
[    4.216294] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
[    4.221013] ata_piix 0000:00:1f.1: version 2.12
[    4.221026] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.221070] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.221311] scsi3 : ata_piix
[    4.221965] scsi4 : ata_piix
[    4.222698] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    4.222701] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    4.228422] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.241299] Driver 'sd' needs updating - please use bus_type methods
[    4.241878] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.241904] sd 0:0:0:0: [sda] Write Protect is off
[    4.241907] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.241952] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.242038] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.242062] sd 0:0:0:0: [sda] Write Protect is off
[    4.242065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.242109] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.242113]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    4.328748] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.384600] ata4.00: ATAPI: Optiarc DVD RW AD-7590A, 1.41, max UDMA/33
[    4.400521] ata4.00: configured for UDMA/33
[    4.569042] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7590A  1.41 PQ: 0 ANSI: 5
[    4.569258] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    4.601471] Driver 'sr' needs updating - please use bus_type methods
[    4.608553] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.608560] Uniform CD-ROM driver Revision: 3.20
[    4.608726] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.066506] PM: Starting manual resume from disk
[    5.066510] PM: Resume from partition 8:6
[    5.066512] PM: Checking hibernation image.
[    5.066692] PM: Resume from disk failed.
[    5.121201] kjournald starting.  Commit interval 5 seconds
[    5.121229] EXT3-fs: mounted filesystem with ordered data mode.
[   12.701414] udevd version 124 started
[   13.185588] iTCO_vendor_support: vendor-support=0
[   13.215781] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.216237] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   13.216360] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.271312] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.365742] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.378159] Linux agpgart interface v0.103
[   13.411683] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.429041] ACPI: Power Button (FF) [PWRF]
[   13.429164] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   13.431206] ACPI: Lid Switch [LID0]
[   13.431273] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.461034] ACPI: Sleep Button (CM) [SLPB]
[   13.461251] ACPI: WMI: Mapper loaded
[   13.485472] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   13.485961] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   13.499711] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   13.609816] acpi device:05: registered as cooling_device2
[   13.610237] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input5
[   13.633040] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.706341] ACPI: AC Adapter [ADP1] (on-line)
[   13.968079] cfg80211: Using static regulatory domain info
[   13.968082] cfg80211: Regulatory domain: US
[   13.968085] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.968087] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   13.968090] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.968092] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.968095] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.968097] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.968100] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   13.968102] cfg80211: Calling CRDA for country: US
[   13.978682] ACPI: Battery Slot [BAT0] (battery present)
[   13.982722] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.997132] lib80211: common routines for IEEE802.11 drivers
[   14.369493] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.369497] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.369586] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.369600] iwl3945 0000:08:00.0: setting latency timer to 64
[   14.369622] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.433239] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.441163] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.707161] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1280b1, caps: 0xa04711/0xa04000
[   14.761648] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   14.885327] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.885362] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.893685] iwl3945 0000:08:00.0: PCI INT A disabled
[   14.922032] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   15.754655] lp: driver loaded but no devices found
[   15.924287] Adding 7847712k swap on /dev/sda6.  Priority:-1 extents:1 across:7847712k
[   16.466366] EXT3 FS on sda5, internal journal
[   17.545758] type=1505 audit(1225839646.981:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4183
[   17.706300] type=1505 audit(1225839647.142:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4188
[   17.706508] type=1505 audit(1225839647.142:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4188
[   17.882403] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.303649] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.383155] apm: BIOS not found.
[   19.568231] ppdev: user-space parallel port driver
[   21.086552] Bluetooth: Core ver 2.13
[   21.088160] NET: Registered protocol family 31
[   21.088170] Bluetooth: HCI device and connection manager initialized
[   21.088175] Bluetooth: HCI socket layer initialized
[   21.124982] Bluetooth: L2CAP ver 2.11
[   21.124995] Bluetooth: L2CAP socket layer initialized
[   21.202303] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.202314] Bluetooth: BNEP filters: protocol multicast
[   21.245586] Bridge firewalling registered
[   21.245828] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   21.289046] Bluetooth: SCO (Voice Link) ver 0.6
[   21.289058] Bluetooth: SCO socket layer initialized
[   21.359007] Bluetooth: RFCOMM socket layer initialized
[   21.360509] Bluetooth: RFCOMM TTY layer initialized
[   21.360520] Bluetooth: RFCOMM ver 1.10
[   25.497815] r8169: eth0: link up
[   25.497833] r8169: eth0: link up
[   25.501167] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.501347] iwl3945 0000:08:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   25.501664] firmware: requesting iwlwifi-3945-1.ucode
[   25.650717] iwl3945: Radio disabled by HW RF Kill switch
[   25.650825] iwl3945 0000:08:00.0: PCI INT A disabled
[   25.668239] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.668412] iwl3945 0000:08:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   25.668717] iwl3945: Radio disabled by HW RF Kill switch
[   25.668795] iwl3945 0000:08:00.0: PCI INT A disabled
[   25.674068] [drm] Initialized drm 1.1.0 20060810
[   25.711600] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.711618] pci 0000:00:02.0: setting latency timer to 64
[   25.711844] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   25.816880] NET: Registered protocol family 17
[   63.033793] CPU0 attaching NULL sched-domain.
[   63.033808] CPU1 attaching NULL sched-domain.
[   63.035773] CPU0 attaching sched-domain:
[   63.035781]  domain 0: span 0-1 level MC
[   63.035786]   groups: 0 1
[   63.035797] CPU1 attaching sched-domain:
[   63.035801]  domain 0: span 0-1 level MC
[   63.035807]   groups: 1 0
[   79.766390] NET: Registered protocol family 10
[   79.767921] lo: Disabled Privacy Extensions
[   90.064036] eth0: no IPv6 routers present
[  127.697075] r8169: eth0: link up
[  127.700949] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  127.701140] iwl3945 0000:08:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[  127.701446] iwl3945: Radio disabled by HW RF Kill switch
[  127.701524] iwl3945 0000:08:00.0: PCI INT A disabled
[  130.889792] type=1503 audit(1225839760.326:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5944/net/" pid=5944 profile="/usr/sbin/cupsd"
[  131.919294] type=1503 audit(1225839761.354:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6005/net/" pid=6005 profile="/usr/sbin/cupsd"
[  131.919354] type=1503 audit(1225839761.354:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919366] type=1503 audit(1225839761.354:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919380] type=1503 audit(1225839761.354:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919392] type=1503 audit(1225839761.354:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919404] type=1503 audit(1225839761.354:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919416] type=1503 audit(1225839761.354:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919430] type=1503 audit(1225839761.354:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  131.919442] type=1503 audit(1225839761.354:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6005 profile="/usr/sbin/cupsd"
[  138.168166] eth0: no IPv6 routers present
[  333.700402] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  333.700416] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  333.702409] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  333.702437] iwl3945 0000:08:00.0: setting latency timer to 64
[  333.702470] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  333.743943] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  333.747678] phy1: Selected rate control algorithm 'iwl-3945-rs'
[  337.796552] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  337.797030] firmware: requesting iwlwifi-3945-1.ucode
[  337.802703] iwl3945: Radio disabled by HW RF Kill switch
[  337.821080] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  337.822661] iwl3945: Radio disabled by HW RF Kill switch
[  355.436522] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  355.436538] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  355.436702] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  355.436722] iwl3945 0000:08:00.0: setting latency timer to 64
[  355.436751] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  355.478631] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[  355.481074] phy2: Selected rate control algorithm 'iwl-3945-rs'
[  359.520534] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  359.521030] firmware: requesting iwlwifi-3945-1.ucode
[  359.526878] iwl3945: Radio disabled by HW RF Kill switch
[  359.546249] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  359.549131] iwl3945: Radio disabled by HW RF Kill switch
[  787.660011] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  787.660485] iwl3945: Radio disabled by HW RF Kill switch
[  908.888283] iwl3945 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  908.888764] iwl3945: Radio disabled by HW RF Kill switch

```

I just included all of dmesg. Yes I know it says it needs the firmware but I thought i'd just post this while I have time and see the replies. The kill switch doesn't seem to work (FN+F2 on this model).

The modules, backports and restricted modules (on a fresh install) did nothing. Just can't seen to do anything.

What confuses me is the fact iwconfig sees the device, yet ifconfig says it isn't enabled and can't find it when trying to enable it.

Ndiswrapper drivers don't work well for me either, they make it visible but I can't connect to **** all (and prefer using the drivers built into ubuntu).

Can anyone help me/come up with any suggestions?

Thanks in advance, please don't ignore this.

HeKerr

---

