---
title: "Can't connect to intertnet."
date: 2011-06-03
forum: New to Ubuntu
---

### Post by gordon33 on 2011-06-03
Hello All

Can't connect to internet with HP G60t-200 laptop.  I am running Ubuntu 10.04  

The wireless list connections are gone.  

When I connect a wire to the computer I still can not connect to the internet.  I get a message box that says "Off Line Mode"  I follow the directions and Click  "Work Offline".  When I hit the "Try Again" button I get a box titled "Server Not Found".

I am using my desk top to send out this request for help.

What can I do to help resolve this block?

Gordon33

---

### Post by alphacrucis2 on 2011-06-03
> **gordon33 said:**
> Hello All

Can't connect to internet with HP G60t-200 laptop.  I am running Ubuntu 10.04  

The wireless list connections are gone.  

When I connect a wire to the computer I still can not connect to the internet.  I get a message box that says "Off Line Mode"  I follow the directions and Click  "Work Offline".  When I hit the "Try Again" button I get a box titled "Server Not Found".

I am using my desk top to send out this request for help.

What can I do to help resolve this block?

Gordon33

Can you open up a terminal and enter this command:

```
nm-tool | grep Driver
```

You should get two lines of output - the drivers being used for ethernet and wireless if any. Just nm-tool will give a lot more info but probably best to take it slow. Notice the capital D in Driver. All lowercase driver wont work. Can you report back the output (there may be none)

---

### Post by gordon33 on 2011-06-03
Hello alphacrucis2

Thank you or your reply.

I was able to get the results from "nm-tool | grep Driver" and some other terminal commands: such as: rfkill list, lspci -nn, lshw -C Network, and sudo iwlist scan. 

" lshw -C Network" reporterd " *-network DISABLED ' but I knew that.   




gordon@gordon-laptop:~$ nm-tool | grep Driver 
  Driver:            r8169 
  Driver:            ath5k 
gordon@gordon-laptop:~$ 




gordon@gordon-laptop:~$ rfkill list 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 


gordon@gordon-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) 
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) 
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03) 
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03) 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) 
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01) 


gordon@gordon-laptop:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network DISABLED      
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1f:16:76:dc:4b 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes 
       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable) 
  *-network DISABLED 
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:24:2b:af:c5:33 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:17 memory:d2600000-d260ffff 


gordon@gordon-laptop:~$ sudo iwlist scan 
[sudo] password for gordon: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     Interface doesn't support scanning : Network is down 

gordon@gordon-laptop:~$ 

Gordon33

---

### Post by alphacrucis2 on 2011-06-03
This thread indicates some sort of problem with the realtech ethernet driver in Lucid. 

[URL="http://ubuntuforums.org/showthread.php?t=1468288"]http://ubuntuforums.org/showthread.php?t=1468288
[/URL]

Not quite the same though. They say it was just a bit crippled. You could check dmesg to see if an error occurs when the drivers are loaded. The above thread seems to suggest that stopping and starting networking may help. For the wireless I suggest searching the forums and/or launchpad for issues with the atheros. A last resort might be to try the 10.10 live CD and see if that works.

---

### Post by gordon33 on 2011-06-03
Hello alphacrucis2


I did not see an error message from the results of dmesg.  

What would I need to do to stop and start networking?

I will work on generating a live CD.

Both wire and wireless connections worked yesterday.

dmesg results

[    0.227226] libata version 3.00 loaded. 
[    0.227305] usbcore: registered new interface driver usbfs 
[    0.227317] usbcore: registered new interface driver hub 
[    0.227342] usbcore: registered new device driver usb 
[    0.227516] ACPI: WMI: Mapper loaded 
[    0.227519] PCI: Using ACPI for IRQ routing 
[    0.227716] NetLabel: Initializing 
[    0.227718] NetLabel:  domain hash size = 128 
[    0.227720] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.227735] NetLabel:  unlabeled traffic allowed by default 
[    0.227772] HPET: 4 timers in total, 0 timers will be used for per-cpu timer 
[    0.227780] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0 
[    0.227786] hpet0: 4 comparators, 64-bit 14.318180 MHz counter 
[    0.232225] Switching to clocksource tsc 
[    0.234133] AppArmor: AppArmor Filesystem Enabled 
[    0.234154] pnp: PnP ACPI init 
[    0.234172] ACPI: bus type pnp registered 
[    0.236016] pnp: PnP ACPI: found 9 devices 
[    0.236019] ACPI: ACPI bus type pnp unregistered 
[    0.236022] PnPBIOS: Disabled by ACPI PNP 
[    0.236036] system 00:01: ioport range 0x164e-0x164f has been reserved 
[    0.236039] system 00:01: ioport range 0x600-0x60f has been reserved 
[    0.236045] system 00:01: ioport range 0x610-0x610 has been reserved 
[    0.236048] system 00:01: ioport range 0x800-0x80f has been reserved 
[    0.236051] system 00:01: ioport range 0x810-0x817 has been reserved 
[    0.236054] system 00:01: ioport range 0x820-0x823 has been reserved 
[    0.236057] system 00:01: ioport range 0x830-0x83b has been reserved 
[    0.236060] system 00:01: ioport range 0x400-0x47f has been reserved 
[    0.236062] system 00:01: ioport range 0x500-0x53f has been reserved 
[    0.236067] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved 
[    0.236070] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved 
[    0.236073] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved 
[    0.236076] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved 
[    0.236079] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved 
[    0.236082] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.236085] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved 
[    0.236088] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved 
[    0.236092] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved 
[    0.236095] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved 
[    0.236098] system 00:01: iomem range 0xff800000-0xff800fff has been reserved 
[    0.270812] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff] 
[    0.270861] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01 
[    0.270865] pci 0000:00:1c.0:   IO window: 0x3000-0x4fff 
[    0.270872] pci 0000:00:1c.0:   MEM window: 0xd3700000-0xd46fffff 
[    0.270878] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0400000-0x000000d14fffff 
[    0.270886] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02 
[    0.270890] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff 
[    0.270897] pci 0000:00:1c.1:   MEM window: 0xd2600000-0xd36fffff 
[    0.270902] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1500000-0x000000d24fffff 
[    0.270911] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03 
[    0.270913] pci 0000:00:1e.0:   IO window: disabled 
[    0.270919] pci 0000:00:1e.0:   MEM window: disabled 
[    0.270924] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.270951]   alloc irq_desc for 21 on node -1 
[    0.270953]   alloc kstat_irqs on node -1 
[    0.270962] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    0.270969] pci 0000:00:1c.0: setting latency timer to 64 
[    0.270980]   alloc irq_desc for 20 on node -1 
[    0.270982]   alloc kstat_irqs on node -1 
[    0.270985] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20 
[    0.270991] pci 0000:00:1c.1: setting latency timer to 64 
[    0.271000] pci 0000:00:1e.0: setting latency timer to 64 
[    0.271005] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.271007] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff] 
[    0.271010] pci_bus 0000:01: resource 0 io:  [0x3000-0x4fff] 
[    0.271013] pci_bus 0000:01: resource 1 mem: [0xd3700000-0xd46fffff] 
[    0.271015] pci_bus 0000:01: resource 2 pref mem [0xd0400000-0xd14fffff] 
[    0.271018] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff] 
[    0.271021] pci_bus 0000:02: resource 1 mem: [0xd2600000-0xd36fffff] 
[    0.271023] pci_bus 0000:02: resource 2 pref mem [0xd1500000-0xd24fffff] 
[    0.271026] pci_bus 0000:03: resource 3 io:  [0x00-0xffff] 
[    0.271029] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff] 
[    0.271070] NET: Registered protocol family 2 
[    0.271174] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.271510] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.271959] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.272260] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.272263] TCP reno registered 
[    0.272371] NET: Registered protocol family 1 
[    0.272395] pci 0000:00:02.0: Boot video device 
[    0.272788] Simple Boot Flag value 0x9 read from CMOS RAM was invalid 
[    0.272790] Simple Boot Flag at 0x44 set to 0x1 
[    0.272959] cpufreq-nforce2: No nForce2 chipset. 
[    0.272986] Scanning for low memory corruption every 60 seconds 
[    0.273101] audit: initializing netlink socket (disabled) 
[    0.273114] type=2000 audit(1307107832.271:1): initialized 
[    0.283640] highmem bounce pool size: 64 pages 
[    0.283646] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    0.285102] VFS: Disk quotas dquot_6.5.2 
[    0.285166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    0.285767] fuse init (API version 7.13) 
[    0.285858] msgmni has been set to 1615 
[    0.286084] alg: No test for stdrng (krng) 
[    0.286145] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[    0.286148] io scheduler noop registered 
[    0.286150] io scheduler anticipatory registered 
[    0.286153] io scheduler deadline registered 
[    0.286195] io scheduler cfq registered (default) 
[    0.286363]   alloc irq_desc for 24 on node -1 
[    0.286365]   alloc kstat_irqs on node -1 
[    0.286377] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X 
[    0.286390] pcieport 0000:00:1c.0: setting latency timer to 64 
[    0.286554]   alloc irq_desc for 25 on node -1 
[    0.286556]   alloc kstat_irqs on node -1 
[    0.286566] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X 
[    0.286577] pcieport 0000:00:1c.1: setting latency timer to 64 
[    0.286686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.287081] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 2940 ss_vid 0 ss_did 0 
[    0.287125] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded 
[    0.287152] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 2942 ss_vid 0 ss_did 0 
[    0.287189] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded 
[    0.287198] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.288083] ACPI: AC Adapter [ADP1] (on-line) 
[    0.288150] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0 
[    0.289735] ACPI: Lid Switch [LID0] 
[    0.289786] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1 
[    0.289793] ACPI: Sleep Button [SLPB] 
[    0.289848] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[    0.289850] ACPI: Power Button [PWRF] 
[    0.290739] ACPI: SSDT b9fb3c98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117) 
[    0.291367] ACPI: SSDT b9fb1598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117) 
[    0.291916] Monitor-Mwait will be used to enter C-1 state 
[    0.291953] Monitor-Mwait will be used to enter C-2 state 
[    0.291960] Marking TSC unstable due to TSC halts in idle 
[    0.292024] processor LNXCPU:00: registered as cooling_device0 
[    0.292529] ACPI: SSDT b9fb2e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117) 
[    0.293032] ACPI: SSDT b9fb3f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117) 
[    0.293477] Switching to clocksource hpet 
[    0.300874] processor LNXCPU:01: registered as cooling_device1 
[    0.315748] thermal LNXTHERM:01: registered as thermal_zone0 
[    0.315760] ACPI: Thermal Zone [TZS0] (45 C) 
[    0.321184] thermal LNXTHERM:02: registered as thermal_zone1 
[    0.321195] ACPI: Thermal Zone [TZS1] (45 C) 
[    0.322838] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    0.324210] brd: module loaded 
[    0.324678] loop: module loaded 
[    0.324774] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[    0.325218] Fixed MDIO Bus: probed 
[    0.325251] PPP generic driver version 2.4.2 
[    0.325289] tun: Universal TUN/TAP device driver, 1.6 
[    0.325291] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.325381] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.325410]   alloc irq_desc for 18 on node -1 
[    0.325412]   alloc kstat_irqs on node -1 
[    0.325419] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 18 (level, low) -> IRQ 18 
[    0.325437] ehci_hcd 0000:00:1a.7: setting latency timer to 64 
[    0.325440] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
[    0.325477] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1 
[    0.325517] ehci_hcd 0000:00:1a.7: debug port 1 
[    0.329404] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported 
[    0.329451] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd4705c00 
[    0.330395] isapnp: Scanning for PnP cards... 
[    0.348092] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00 
[    0.348220] usb usb1: configuration #1 chosen from 1 choice 
[    0.348250] hub 1-0:1.0: USB hub found 
[    0.348260] hub 1-0:1.0: 6 ports detected 
[    0.348333] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
[    0.348353] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    0.348357] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    0.348399] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2 
[    0.348435] ehci_hcd 0000:00:1d.7: debug port 1 
[    0.352322] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[    0.352330] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd4705800 
[    0.376052] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    0.376163] usb usb2: configuration #1 chosen from 1 choice 
[    0.376192] hub 2-0:1.0: USB hub found 
[    0.376201] hub 2-0:1.0: 6 ports detected 
[    0.376273] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.376292] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.376333] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    0.376344] uhci_hcd 0000:00:1a.0: setting latency timer to 64 
[    0.376348] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
[    0.376384] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3 
[    0.376416] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000050e0 
[    0.376510] usb usb3: configuration #1 chosen from 1 choice 
[    0.376535] hub 3-0:1.0: USB hub found 
[    0.376542] hub 3-0:1.0: 2 ports detected 
[    0.376588]   alloc irq_desc for 19 on node -1 
[    0.376590]   alloc kstat_irqs on node -1 
[    0.376596] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[    0.376603] uhci_hcd 0000:00:1a.1: setting latency timer to 64 
[    0.376607] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
[    0.376642] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4 
[    0.376679] uhci_hcd 0000:00:1a.1: irq 19, io base 0x000050c0 
[    0.376773] usb usb4: configuration #1 chosen from 1 choice 
[    0.376797] hub 4-0:1.0: USB hub found 
[    0.376804] hub 4-0:1.0: 2 ports detected 
[    0.376848]   alloc irq_desc for 17 on node -1 
[    0.376850]   alloc kstat_irqs on node -1 
[    0.376855] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17 
[    0.376862] uhci_hcd 0000:00:1a.2: setting latency timer to 64 
[    0.376866] uhci_hcd 0000:00:1a.2: UHCI Host Controller 
[    0.376897] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5 
[    0.376934] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000050a0 
[    0.377021] usb usb5: configuration #1 chosen from 1 choice 
[    0.377046] hub 5-0:1.0: USB hub found 
[    0.377052] hub 5-0:1.0: 2 ports detected 
[    0.377097] uhci_hcd 0000:00:1d.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
[    0.377104] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    0.377108] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    0.377138] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6 
[    0.377166] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00005080 
[    0.377259] usb usb6: configuration #1 chosen from 1 choice 
[    0.377283] hub 6-0:1.0: USB hub found 
[    0.377289] hub 6-0:1.0: 2 ports detected 
[    0.377339] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 19 (level, low) -> IRQ 19 
[    0.377345] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    0.377349] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    0.377378] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7 
[    0.377405] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060 
[    0.377490] usb usb7: configuration #1 chosen from 1 choice 
[    0.377515] hub 7-0:1.0: USB hub found 
[    0.377522] hub 7-0:1.0: 2 ports detected 
[    0.377567] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 17 (level, low) -> IRQ 17 
[    0.377573] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    0.377577] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    0.377608] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8 
[    0.377636] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00005040 
[    0.377723] usb usb8: configuration #1 chosen from 1 choice 
[    0.377748] hub 8-0:1.0: USB hub found 
[    0.377754] hub 8-0:1.0: 2 ports detected 
[    0.377848] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    0.395115] i8042.c: Detected active multiplexing controller, rev 1.1. 
[    0.409473] Freeing initrd memory: 7736k freed 
[    0.421965] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.421979] serio: i8042 AUX0 port at 0x60,0x64 irq 12 
[    0.422026] serio: i8042 AUX1 port at 0x60,0x64 irq 12 
[    0.422048] serio: i8042 AUX2 port at 0x60,0x64 irq 12 
[    0.422070] serio: i8042 AUX3 port at 0x60,0x64 irq 12 
[    0.422227] mice: PS/2 mouse device common for all mice 
[    0.422954] rtc_cmos 00:03: RTC can wake from S4 
[    0.422997] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    0.423030] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs 
[    0.423151] device-mapper: uevent: version 1.0.3 
[    0.423272] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email] 
[    0.423338] device-mapper: multipath: version 1.1.0 loaded 
[    0.423340] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    0.423458] EISA: Probing bus 0 at eisa.0 
[    0.423470] Cannot allocate resource for EISA slot 2 
[    0.423472] Cannot allocate resource for EISA slot 3 
[    0.423474] Cannot allocate resource for EISA slot 4 
[    0.423476] Cannot allocate resource for EISA slot 5 
[    0.423492] EISA: Detected 0 cards. 
[    0.423616] cpuidle: using governor ladder 
[    0.423704] cpuidle: using governor menu 
[    0.424135] TCP cubic registered 
[    0.424296] NET: Registered protocol family 10 
[    0.424766] lo: Disabled Privacy Extensions 
[    0.425103] NET: Registered protocol family 17 
[    0.425615] Using IPI No-Shortcut mode 
[    0.425695] PM: Resume from disk failed. 
[    0.425706] registered taskstats version 1 
[    0.426208]   Magic number: 15:80:533 
[    0.426224] bdi 1:11: hash matches 
[    0.426293] rtc_cmos 00:03: setting system clock to 2011-06-03 13:30:32 UTC (1307107832) 
[    0.426295] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.426297] EDD information not available. 
[    0.451277] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    0.684559] isapnp: No Plug & Play device found 
[    0.684578] Freeing unused kernel memory: 684k freed 
[    0.711600] Write protecting the kernel text: 4828k 
[    0.711654] usb 1-3: new high speed USB device using ehci_hcd and address 2 
[    0.711682] Write protecting the kernel read-only data: 1884k 
[    0.730112] udev: starting version 151 
[    0.839366] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    0.839391]   alloc irq_desc for 16 on node -1 
[    0.839393]   alloc kstat_irqs on node -1 
[    0.839400] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.839490] r8169 0000:01:00.0: setting latency timer to 64 
[    0.839548]   alloc irq_desc for 26 on node -1 
[    0.839550]   alloc kstat_irqs on node -1 
[    0.839566] r8169 0000:01:00.0: irq 26 for MSI/MSI-X 
[    0.840321] eth0: RTL8102e at 0xf822e000, 00:1f:16:76:dc:4b, XID 14a00000 IRQ 26 
[    0.852850] ahci 0000:00:1f.2: version 3.0 
[    0.852870]   alloc irq_desc for 23 on node -1 
[    0.852872]   alloc kstat_irqs on node -1 
[    0.852879] ahci 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23 
[    0.852924]   alloc irq_desc for 27 on node -1 
[    0.852926]   alloc kstat_irqs on node -1 
[    0.852936] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X 
[    0.852994] ahci: SSS flag set, parallel bus scan disabled 
[    0.853036] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode 
[    0.853039] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems sxs 
[    0.853045] ahci 0000:00:1f.2: setting latency timer to 64 
[    0.855719] usb 1-3: configuration #1 chosen from 1 choice 
[    0.866836] Initializing USB Mass Storage driver... 
[    0.866963] scsi0 : SCSI emulation for USB Mass Storage devices 
[    0.867099] usbcore: registered new interface driver usb-storage 
[    0.867102] USB Mass Storage support registered. 
[    0.867248] usb-storage: device found at 2 
[    0.867250] usb-storage: waiting for device to settle before scanning 
[    0.876126] scsi1 : ahci 
[    0.876209] scsi2 : ahci 
[    0.876272] scsi3 : ahci 
[    0.876333] scsi4 : ahci 
[    0.876395] scsi5 : ahci 
[    0.876454] scsi6 : ahci 
[    0.876810] ata1: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705100 irq 27 
[    0.876816] ata2: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705180 irq 27 
[    0.876818] ata3: DUMMY 
[    0.876819] ata4: DUMMY 
[    0.876822] ata5: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705300 irq 27 
[    0.876826] ata6: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705380 irq 27 
[    0.909355] ACPI: Battery Slot [BAT0] (battery present) 
[    0.972062] usb 1-5: new high speed USB device using ehci_hcd and address 3 
[    1.141850] usb 1-5: configuration #1 chosen from 1 choice 
[    1.360071] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.361412] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
[    1.361493] ata1.00: ATA-8: WDC WD1600BEVT-60ZCT1, 13.01A13, max UDMA/100 
[    1.361497] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA 
[    1.362854] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
[    1.362963] ata1.00: configured for UDMA/100 
[    1.376235] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-6 13.0 PQ: 0 ANSI: 5 
[    1.376407] sd 1:0:0:0: Attached scsi generic sg0 type 0 
[    1.376431] sd 1:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB) 
[    1.376559] sd 1:0:0:0: [sda] Write Protect is off 
[    1.376562] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.376617] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.376854]  sda: sda1 sda2 < sda5 > 
[    1.434397] sd 1:0:0:0: [sda] Attached SCSI disk 
[    2.264063] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    2.277626] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
[    2.277630] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SH03, max UDMA/100 
[    2.291613] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) rejected by device (Stat=0x51 Err=0x04) 
[    2.291640] ata2.00: configured for UDMA/100 
[    2.309110] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SH03 PQ: 0 ANSI: 5 
[    2.314520] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray 
[    2.314524] Uniform CD-ROM driver Revision: 3.20 
[    2.314623] sr 2:0:0:0: Attached scsi CD-ROM sr0 
[    2.314684] sr 2:0:0:0: Attached scsi generic sg1 type 5 
[    2.632067] ata5: SATA link down (SStatus 0 SControl 300) 
[    2.968065] ata6: SATA link down (SStatus 0 SControl 300) 
[    3.305742] kjournald starting.  Commit interval 5 seconds 
[    3.305764] EXT3-fs: mounted filesystem with ordered data mode. 
[    5.864473] usb-storage: device scan complete 
[    5.866555] scsi 0:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS 
[    5.867090] sd 0:0:0:0: Attached scsi generic sg2 type 0 
[    5.870646] sd 0:0:0:0: [sdb] Attached SCSI removable disk 
[   21.061885] udev: starting version 151 
[   21.135010] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k 
[   21.151487] lp: driver loaded but no devices found 
[   21.231750] Linux agpgart interface v0.103 
[   21.321366] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset 
[   21.321890] agpgart-intel 0000:00:00.0: detected 65532K stolen memory 
[   21.367547] Linux video capture interface: v2.00 
[   21.370817] EXT3 FS on sda1, internal journal 
[   21.392328] uvcvideo: Found UVC 1.00 device CNF7047 (04f2:b091) 
[   21.392604] cfg80211: Calling CRDA to update world regulatory domain 
[   21.394486] [drm] Initialized drm 1.1.0 20060810 
[   21.409091] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000 
[   21.409425] input: CNF7047 as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input5 
[   21.409478] usbcore: registered new interface driver uvcvideo 
[   21.409481] USB Video Class driver (v0.1.0) 
[   21.441398] type=1505 audit(1307107853.513:2):  operation="profile_load" pid=613 name="/sbin/dhclient3" 
[   21.442116] type=1505 audit(1307107853.513:3):  operation="profile_load" pid=613 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   21.442513] type=1505 audit(1307107853.513:4):  operation="profile_load" pid=613 name="/usr/lib/connman/scripts/dhclient-script" 
[   21.444198] type=1505 audit(1307107853.517:5):  operation="profile_replace" pid=619 name="/sbin/dhclient3" 
[   21.445007] type=1505 audit(1307107853.517:6):  operation="profile_replace" pid=619 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   21.445412] type=1505 audit(1307107853.517:7):  operation="profile_replace" pid=619 name="/usr/lib/connman/scripts/dhclient-script" 
[   21.449421] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   21.449436] ath5k 0000:02:00.0: setting latency timer to 64 
[   21.449484] ath5k 0000:02:00.0: registered as 'phy0' 
[   21.517486] cfg80211: World regulatory domain updated: 
[   21.517489] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   21.517492] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   21.517495] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   21.517498] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   21.517500] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   21.517503] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   21.634656]   alloc irq_desc for 22 on node -1 
[   21.634660]   alloc kstat_irqs on node -1 
[   21.634667] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[   21.634727]   alloc irq_desc for 28 on node -1 
[   21.634728]   alloc kstat_irqs on node -1 
[   21.634740] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X 
[   21.634770] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   21.693921] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6 
[   21.694129] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7 
[   21.694319] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8 
[   21.695624] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   21.695631] i915 0000:00:02.0: setting latency timer to 64 
[   21.715110]   alloc irq_desc for 29 on node -1 
[   21.715114]   alloc kstat_irqs on node -1 
[   21.715124] i915 0000:00:02.0: irq 29 for MSI/MSI-X 
[   21.715132] [drm] set up 63M of stolen space 
[   21.955520] ath: EEPROM regdomain: 0x64 
[   21.955524] ath: EEPROM indicates we should expect a direct regpair map 
[   21.955527] ath: Country alpha2 being used: 00 
[   21.955529] ath: Regpair used: 0x64 
[   21.961990] phy0: Selected rate control algorithm 'minstrel' 
[   21.962742] Registered led device: ath5k-phy0::rx 
[   21.962759] Registered led device: ath5k-phy0::tx 
[   21.962762] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70) 
[   22.290043] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000 
[   22.352042] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9 
[   22.823809] type=1505 audit(1307107854.893:8):  operation="profile_replace" pid=786 name="/sbin/dhclient3" 
[   22.824559] type=1505 audit(1307107854.897:9):  operation="profile_replace" pid=786 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   22.824987] type=1505 audit(1307107854.897:10):  operation="profile_replace" pid=786 name="/usr/lib/connman/scripts/dhclient-script" 
[   22.827476] type=1505 audit(1307107854.897:11):  operation="profile_load" pid=785 name="/usr/share/gdm/guest-session/Xsession" 
[   22.983500] apm: BIOS not found. 
[   22.990761] fb0: inteldrmfb frame buffer device 
[   22.990765] registered panic notifier 
[   23.007939] acpi device:02: registered as cooling_device2 
[   23.008269] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10 
[   23.008330] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no) 
[   23.008371] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[   23.010273] vga16fb: initializing 
[   23.010277] vga16fb: mapped to 0xc00a0000 
[   23.010281] vga16fb: not registering due to another framebuffer present 
[   23.170662] ppdev: user-space parallel port driver 
[   23.388328] Console: switching to colour frame buffer device 170x48 
[   23.626438] CPU0 attaching NULL sched-domain. 
[   23.626444] CPU1 attaching NULL sched-domain. 
[   23.648101] CPU0 attaching sched-domain: 
[   23.648105]  domain 0: span 0-1 level MC 
[   23.648107]   groups: 0 1 
[   23.648113] CPU1 attaching sched-domain: 
[   23.648115]  domain 0: span 0-1 level MC 
[   23.648117]   groups: 1 0 
[   27.840305] CPU0 attaching NULL sched-domain. 
[   27.840312] CPU1 attaching NULL sched-domain. 
[   27.864102] CPU0 attaching sched-domain: 
[   27.864107]  domain 0: span 0-1 level MC 
[   27.864110]   groups: 0 1 
[   27.864116] CPU1 attaching sched-domain: 
[   27.864118]  domain 0: span 0-1 level MC 
[   27.864121]   groups: 1 0 
[  669.984077] usb 2-3: new high speed USB device using ehci_hcd and address 2 
[  670.119267] usb 2-3: configuration #1 chosen from 1 choice 
[  670.119713] scsi7 : SCSI emulation for USB Mass Storage devices 
[  670.120009] usb-storage: device found at 2 
[  670.120013] usb-storage: waiting for device to settle before scanning 
[  675.120789] usb-storage: device scan complete 
[  675.122054] scsi 7:0:0:0: Direct-Access     Flash    Drive SM_USB20   1000 PQ: 0 ANSI: 0 CCS 
[  675.122968] sd 7:0:0:0: Attached scsi generic sg3 type 0 
[  675.127129] sd 7:0:0:0: [sdc] 125952 512-byte logical blocks: (64.4 MB/61.5 MiB) 
[  675.128100] sd 7:0:0:0: [sdc] Write Protect is off 
[  675.128107] sd 7:0:0:0: [sdc] Mode Sense: 43 00 00 00 
[  675.128112] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[  675.132131] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[  675.132140]  sdc: sdc1 
[  675.171791] sd 7:0:0:0: [sdc] Assuming drive cache: write through 
[  675.171802] sd 7:0:0:0: [sdc] Attached SCSI removable disk 
gordon@gordon-laptop:~$

---

### Post by gordon33 on 2011-06-03
Its even worse now both my computers lap top and desk top will not connect to inter net.

I started another post: ( _[http://ubuntuforums.org/showthread.php?t=1774626](http://ubuntuforums.org/showthread.php?t=1774626)_ ) because of the urgency of having no intertnet. 

Need hep bad

Gordon33

---

