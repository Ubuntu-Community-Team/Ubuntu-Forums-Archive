---
title: "wireless on a netbook"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2009-04-18
Hi all. Firstly, I know this is a common topic and there are many, many articles out there explaining this topic, but none of them have helped me, so I'll try here. My situation: I've been running ubuntu-eee on my laptop since I got it (~ 6 months ago) with no problems. Two nights ago I fell asleep with the laptop on (which I believe put it in suspended mode, which may have messed with the driver). Now I can see the wireless networks in range, but can't connect to them.

lspci -v | less says:
01:00.0 Network controller: RaLink Unknown device 0781
        Subsystem: RaLink Unknown device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at f8000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

Any Help?

---

### Post by hesjnet on 2009-04-18
Have you tried Ubuntu-eee aka Easy Peasy? it is specially designed for Eee netbooks. Jaunty is also reported to be brilliant for at least Eee 900.

Have you tried to restart your router?

---

### Post by woodsonoversoul on 2009-04-18
I've restarted the router and I'm currently using ubuntu-eee, which has now become 'easy-peasy'. I suppose I could install another OS(or re-install the current), but I'm trying not to as I have a database set up on an xampp server (running on the laptop) and I'm concerned about copying everything correctly)

---

### Post by eeeandrew on 2009-04-18
how did you partition your hard drive? If you have seperate home and root partitions all your data will be safe if you reinstall the operating system.

---

### Post by alfplayer on 2009-04-18
What do you mean you can't connect? What happens when you try?

---

### Post by Crafty Kisses on 2009-04-18
Try scanning for networks through the Terminal, what are the results of this?
```
sudo iwlist wlan0 scan
```

---

### Post by Wusel on 2009-04-18
Hi, 

i also had his problem on my NC10. Sometimes it happens an i can't connect to my AP anymore. It is shown in the networkmanager but when i try to connect everything wich happens is, asking for the passkey of the ap and then yelling at me that the connection is disconnected.

There are two solutions that i figured out. First starting Windows and after that Ubuntu does the trick, but the it also helps if i shut down the netbook an removing the battery. After inserting it i start Ubuntu and everything runs smooth again. Ok until the next time it happens.

This is only a guess, maybe the driver messes something up in interface.
But i dont have so much time and patience to figure out a better solution :)

PS: Now running 9.04 RC and everything seems fine.

---

### Post by woodsonoversoul on 2009-04-19
Alright. Just got home from work. To answer your questions (and pose some of my own):

eeeandrew: I'm not esp. fluent in partitioning. I did the auto partition which gave me a dual-boot, but I think the individual os stuff is all lumped together. Also, all of my server files are in the opt folder; wouldn't this affect them?

alfplayer: When I click on a wifi network it doesn't connect. Not even one green light.

codename: sudo iwlist wlan0 scan gives me: 
wlan0     Interface doesn't support scanning.

Wusel: I've tried those. No luck :(

Thanks for all the replies! I'm still here, either stuck in Windows to connect wirelessly or tied with a cable to my router. Please, keep the questions coming!

---

### Post by woodsonoversoul on 2009-04-19
bump for today

---

### Post by woodsonoversoul on 2009-04-19
and bump again, 'cause I'd like to use my computer today...

---

### Post by woodsonoversoul on 2009-04-19
bump to stay on the front page...

---

### Post by woodsonoversoul on 2009-04-19
Anyone have any experience with this type of problem?

---

### Post by woodsonoversoul on 2009-04-20
Any ideas...?

---

### Post by woodsonoversoul on 2009-04-20
I followed the tutorials [here]("http://forums.remote-exploit.org/showthread.php?t=21707") and [here]("http://ubuntuforums.org/showthread.php?t=683085&page=3") and pretty much feel like I've smashed my wireless with a rock

---

### Post by aeiah on 2009-04-20
what does dmesg say when you try to scan / connect / do an ifdown wlan0 and ifup wlan0 commands?

i may have missed where you said this, but you have rebooted the eee pc havent you?

i have an acer aspire one which uses an atheros chipset and probably behaves differently so i dont have any direct experience im afraid.

---

### Post by woodsonoversoul on 2009-04-20
dmesg? I'm unfamiliar with that term, but I'll look it up. I have rebooted.

Also, from messing around, trying to get it to work, I've lost all wireless access points, I can't even see them. Please help if possible...

---

### Post by woodsonoversoul on 2009-04-20
when I typed 'dmesg' in terminal I get:

```
[    5.390348] SELinux:  Disabled at boot.
[    5.390374] AppArmor: AppArmor initialized
[    5.390380] Failure registering capabilities with primary security module.
[    5.390394] Mount-cache hash table entries: 512
[    5.390574] Initializing cgroup subsys ns
[    5.390584] Initializing cgroup subsys cpuacct
[    5.390599] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    5.390611] monitor/mwait feature present.
[    5.390614] using mwait in idle threads.
[    5.390620] CPU: L1 I cache: 32K, L1 D cache: 24K
[    5.390624] CPU: L2 cache: 512K
[    5.390628] CPU: Physical Processor ID: 0
[    5.390632] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    5.390646] Compat vDSO mapped to ffffe000.
[    5.390662] Checking 'hlt' instruction... OK.
[    5.406634] SMP alternatives: switching to UP code
[    5.408467] Early unpacking initramfs... done
[    5.758577] ACPI: Core revision 20070126
[    5.758684] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    5.904322] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    5.904351] SMP alternatives: switching to SMP code
[    5.904878] Booting processor 1/1 eip 3000
[    5.914905] Initializing CPU#1
[    5.993721] Calibrating delay using timer specific routine.. 3191.99 BogoMIPS (lpj=6383991)
[    5.993735] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0040c39d 00000000 00000001 00000000
[    5.993748] monitor/mwait feature present.
[    5.993754] CPU: L1 I cache: 32K, L1 D cache: 24K
[    5.993758] CPU: L2 cache: 512K
[    5.993763] CPU: Physical Processor ID: 0
[    5.993767] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00043940 0040c39d 00000000 00000001 00000000
[    5.993967] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    5.993992] Total of 2 processors activated (6388.36 BogoMIPS).
[    5.994200] ENABLING IO-APIC IRQs
[    5.994413] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    6.141793] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    6.161795] Brought up 2 CPUs
[    6.161835] CPU0 attaching sched-domain:
[    6.161839]  domain 0: span 3
[    6.161842]   groups: 1 2
[    6.161849] CPU1 attaching sched-domain:
[    6.161852]  domain 0: span 3
[    6.161855]   groups: 2 1
[    6.162186] net_namespace: 64 bytes
[    6.162198] Booting paravirtualized kernel on bare hardware
[    6.163111] Time:  7:10:19  Date: 04/20/09
[    6.163149] NET: Registered protocol family 16
[    6.163500] ACPI: bus type pci registered
[    6.163965] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    6.163970] PCI: Using configuration type 1
[    6.163989] Setting up standard PCI resources
[    6.176040] ACPI: EC: Look up EC in DSDT
[    6.191405] ACPI: Interpreter enabled
[    6.191410] ACPI: (supports S0 S1 S3 S4 S5)
[    6.191443] ACPI: Using IOAPIC for interrupt routing
[    6.192000] Error attaching device data
[    6.192096] Error attaching device data
[    6.202478] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    6.202485] ACPI: EC: driver started in poll mode
[    6.202689] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    6.203620] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    6.203627] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    6.204425] PCI: Transparent bridge - 0000:00:1e.0
[    6.204482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    6.204774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    6.204918] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    6.224330] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    6.224562] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    6.224789] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    6.225016] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    6.225243] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    6.225473] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    6.225712] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    6.225946] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    6.226191] Linux Plug and Play Support v0.97 (c) Adam Belay
[    6.226259] pnp: PnP ACPI init
[    6.226274] ACPI: bus type pnp registered
[    6.229813] pnp: PnP ACPI: found 13 devices
[    6.229819] ACPI: ACPI bus type pnp unregistered
[    6.230294] PCI: Using ACPI for IRQ routing
[    6.230300] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    6.257497] NET: Registered protocol family 8
[    6.257502] NET: Registered protocol family 20
[    6.257569] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    6.257577] hpet0: 3 64-bit timers, 14318180 Hz
[    6.258638] AppArmor: AppArmor Filesystem Enabled
[    6.261476] Time: tsc clocksource has been installed.
[    6.261501] Switched to high resolution mode on CPU 0
[    6.261694] Switched to high resolution mode on CPU 1
[    6.269512] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    6.269529] system 00:08: ioport range 0x25c-0x25f has been reserved
[    6.269534] system 00:08: ioport range 0x380-0x383 has been reserved
[    6.269539] system 00:08: ioport range 0x400-0x41f has been reserved
[    6.269544] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    6.269549] system 00:08: ioport range 0x800-0x87f has been reserved
[    6.269554] system 00:08: ioport range 0x480-0x4bf has been reserved
[    6.269560] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
[    6.269566] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    6.269571] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    6.269577] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    6.269582] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    6.269588] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    6.269599] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    6.269605] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    6.269615] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[    6.269625] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    6.269630] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    6.269636] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    6.269641] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
[    6.269647] system 00:0c: iomem range 0x0-0x0 could not be reserved
[    6.300464] PCI: Bridge: 0000:00:1c.0
[    6.300468]   IO window: disabled.
[    6.300476]   MEM window: disabled.
[    6.300482]   PREFETCH window: disabled.
[    6.300490] PCI: Bridge: 0000:00:1c.1
[    6.300495]   IO window: e000-efff
[    6.300503]   MEM window: fbf00000-fbffffff
[    6.300509]   PREFETCH window: disabled.
[    6.300523] PCI: Bridge: 0000:00:1c.3
[    6.300526]   IO window: disabled.
[    6.300533]   MEM window: f8000000-fbefffff
[    6.300540]   PREFETCH window: f0000000-f6ffffff
[    6.300547] PCI: Bridge: 0000:00:1e.0
[    6.300550]   IO window: disabled.
[    6.300557]   MEM window: disabled.
[    6.300563]   PREFETCH window: disabled.
[    6.300607] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.300618] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    6.300648] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    6.300657] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    6.300687] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    6.300696] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    6.300713] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    6.300736] NET: Registered protocol family 2
[    6.337479] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.337926] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    6.338981] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    6.339536] TCP: Hash tables configured (established 131072 bind 65536)
[    6.339542] TCP reno registered
[    6.349623] Unpacking initramfs... done
[    6.704678] Freeing initrd memory: 4979k freed
[    6.706313] audit: initializing netlink socket (disabled)
[    6.706339] audit(1240211419.128:1): initialized
[    6.706651] highmem bounce pool size: 64 pages
[    6.710546] VFS: Disk quotas dquot_6.5.1
[    6.710690] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    6.710930] io scheduler noop registered
[    6.710935] io scheduler anticipatory registered
[    6.710939] io scheduler deadline registered
[    6.710961] io scheduler cfq registered (default)
[    6.710980] Boot video device is 0000:00:02.0
[    6.711276] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    6.711342] assign_interrupt_mode Found MSI capability
[    6.711347] Allocate Port Service[0000:00:1c.0:pcie00]
[    6.711424] Allocate Port Service[0000:00:1c.0:pcie02]
[    6.711571] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    6.711636] assign_interrupt_mode Found MSI capability
[    6.711640] Allocate Port Service[0000:00:1c.1:pcie00]
[    6.711715] Allocate Port Service[0000:00:1c.1:pcie02]
[    6.711863] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    6.711927] assign_interrupt_mode Found MSI capability
[    6.711932] Allocate Port Service[0000:00:1c.3:pcie00]
[    6.712004] Allocate Port Service[0000:00:1c.3:pcie02]
[    6.774930] Real Time Clock Driver v1.12ac
[    6.775247] hpet_resources: 0xfed00000 is busy
[    6.775299] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.776529] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.807571] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.807581] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.807855] mice: PS/2 mouse device common for all mice
[    6.807963] cpuidle: using governor ladder
[    6.807967] cpuidle: using governor menu
[    6.808112] NET: Registered protocol family 1
[    6.808163] Using IPI No-Shortcut mode
[    6.808208] registered taskstats version 1
[    6.808360]   Magic number: 5:845:167
[    6.808415]   hash matches device ttyq7
[    6.808510]   hash matches device PNP0000:00
[    6.808518] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.808522] EDD information not available.
[    6.808665] Freeing unused kernel memory: 264k freed
[    6.848986] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    8.147865] fuse init (API version 7.9)
[    8.167452] ACPI: SSDT 7F7AE180, 023C (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    8.167822] ACPI: SSDT 7F7AE450, 0724 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    8.168300] Monitor-Mwait will be used to enter C-1 state
[    8.168306] Monitor-Mwait will be used to enter C-2 state
[    8.168310] Monitor-Mwait will be used to enter C-3 state
[    8.168554] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    8.168564] ACPI: Processor [P001] (supports 8 throttling states)
[    8.169040] ACPI: SSDT 7F7AE0B0, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    8.169366] ACPI: SSDT 7F7AE3C0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    8.170081] Marking TSC unstable due to: TSC halts in idle.
[    8.170268] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    8.170279] ACPI: Processor [P002] (supports 8 throttling states)
[    8.171648] Time: hpet clocksource has been installed.
[    8.173733] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    8.182270] ACPI: Thermal Zone [TZ00] (55 C)
[    8.713258] usbcore: registered new interface driver usbfs
[    8.713309] usbcore: registered new interface driver hub
[    8.714653] usbcore: registered new device driver usb
[    8.729203] USB Universal Host Controller Interface driver v3.0
[    8.729307] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    8.729327] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.729335] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.729639] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    8.729695] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000d400
[    8.730008] usb usb1: configuration #1 chosen from 1 choice
[    8.730069] hub 1-0:1.0: USB hub found
[    8.730084] hub 1-0:1.0: 2 ports detected
[    8.795776] SCSI subsystem initialized
[    8.833172] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    8.833196] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    8.833205] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.833280] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    8.833332] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000d480
[    8.833612] usb usb2: configuration #1 chosen from 1 choice
[    8.833676] hub 2-0:1.0: USB hub found
[    8.833693] hub 2-0:1.0: 2 ports detected
[    8.881993] libata version 3.00 loaded.
[    8.937149] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    8.937172] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.937181] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.937237] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    8.937286] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d800
[    8.937572] usb usb3: configuration #1 chosen from 1 choice
[    8.937641] hub 3-0:1.0: USB hub found
[    8.937657] hub 3-0:1.0: 2 ports detected
[    9.040922] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    9.040945] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    9.040954] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    9.041003] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    9.041045] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    9.041250] usb usb4: configuration #1 chosen from 1 choice
[    9.041292] hub 4-0:1.0: USB hub found
[    9.041301] hub 4-0:1.0: 2 ports detected
[    9.144880] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    9.144907] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    9.144916] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    9.144974] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    9.148905] ehci_hcd 0000:00:1d.7: debug port 1
[    9.148920] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    9.148939] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7eb7c00
[    9.165688] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    9.165960] usb usb5: configuration #1 chosen from 1 choice
[    9.166028] hub 5-0:1.0: USB hub found
[    9.166044] hub 5-0:1.0: 8 ports detected
[    9.274776] ata_piix 0000:00:1f.2: version 2.12
[    9.274791] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    9.274843] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[    9.274906] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    9.275839] scsi0 : ata_piix
[    9.275966] scsi1 : ata_piix
[    9.279181] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    9.279191] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    9.440755] ata1.00: ATA-8: ST9160827AS, 3.AAA, max UDMA/133
[    9.440763] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    9.456758] ata1.00: configured for UDMA/133
[    9.625155] scsi 0:0:0:0: Direct-Access     ATA      ST9160827AS      3.AA PQ: 0 ANSI: 5
[    9.686819] Driver 'sd' needs updating - please use bus_type methods
[    9.686985] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    9.687020] sd 0:0:0:0: [sda] Write Protect is off
[    9.687028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.687082] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.687186] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    9.687218] sd 0:0:0:0: [sda] Write Protect is off
[    9.687225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.687278] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.687288]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    9.757212] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.766214] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    9.920040] usb 5-8: new high speed USB device using ehci_hcd and address 3
[   10.097138] usb 5-8: configuration #1 chosen from 1 choice
[   10.233154] Attempting manual resume
[   10.233160] swsusp: Resume From Partition 8:6
[   10.233164] PM: Checking swsusp image.
[   10.233380] PM: Resume from disk failed.
[   10.287598] kjournald starting.  Commit interval 5 seconds
[   10.287635] EXT3-fs: mounted filesystem with ordered data mode.
[   10.339586] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   10.509949] usb 4-1: configuration #1 chosen from 1 choice
[   16.164549] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.223834] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.508853] asus_eee module requires i2c-i801 module at load time if you like to access pll via proc too
[   16.508875] asus_eee version 0.3 init sucessfully
[   16.588978] Linux agpgart interface v0.102
[   16.708268] agpgart: Detected an Intel 945GME Chipset.
[   16.708487] agpgart: Detected 7932K stolen memory.
[   16.735367] agpgart: AGP aperture is 256M @ 0xd0000000
[   17.363041] input: Power Button (FF) as /devices/virtual/input/input1
[   17.388129] ACPI: Power Button (FF) [PWRF]
[   17.388387] input: Lid Switch as /devices/virtual/input/input2
[   17.407171] iTCO_vendor_support: vendor-support=0
[   17.416420] ACPI: Lid Switch [LID]
[   17.416630] input: Sleep Button (CM) as /devices/virtual/input/input3
[   17.432063] ACPI: Sleep Button (CM) [SLPB]
[   17.432261] input: Power Button (CM) as /devices/virtual/input/input4
[   17.448042] ACPI: Power Button (CM) [PWRB]
[   17.460444] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.460612] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   17.460679] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.536399] Asus EeePC Hotkey Driver
[   17.537353] [eeepc hotk] Hotkey init flags 0x41.
[   17.537497] [eeepc hotk] Get control methods supported: 0x101713
[   18.183847] ACPI: AC Adapter [AC0] (off-line)
[   18.350435] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   18.370139] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.698241] ACPI: Battery Slot [BAT0] (battery present)
[   18.879230] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[   18.879245] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   18.879722] 
[   18.879725] 
[   18.879727] === pAd = f8aa6000, size = 580788 ===
[   18.879730] 
[   18.879736] <-- RTMPAllocAdapterBlock, Status=0
[   18.879769] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   18.998562] Atheros(R) AR8121/AR8113 PCI-E Ethernet Network Driver - version 1.0.0.4
[   18.998571] Copyright (c) 2007 Atheros Corporation.
[   18.998677] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.998703] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.601054] Bluetooth: Core ver 2.11
[   19.676964] NET: Registered protocol family 31
[   19.676972] Bluetooth: HCI device and connection manager initialized
[   19.676982] Bluetooth: HCI socket layer initialized
[   19.737029] Bluetooth: HCI USB driver ver 2.9
[   19.739207] usbcore: registered new interface driver hci_usb
[   19.944961] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   20.184077] Linux video capture interface: v2.00
[   20.257668] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   20.273401] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0/input/input7
[   20.284357] usbcore: registered new interface driver uvcvideo
[   20.284369] USB Video Class driver (SVN r249)
[   20.503028] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.503071] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.990974] repeat_elantech == 1
[   21.990982] repeat_elantech == 2
[   22.167621] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[   22.884062] lp: driver loaded but no devices found
[   23.120598] Adding 2963952k swap on /dev/sda6.  Priority:-1 extents:1 across:2963952k
[   23.156241] EXT3 FS on sda5, internal journal
[   24.239559] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.904333] No dock devices found.
[   26.826088] pciehp: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[   26.826576] pciehp: Cannot get control of hotplug hardware for pci 0000:00:1c.0
[   26.826629] pciehp: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[   26.827051] pciehp: Cannot get control of hotplug hardware for pci 0000:00:1c.1
[   26.827097] pciehp: HPC vendor_id 8086 device_id 27d6 ss_vid 0 ss_did 0
[   26.827496] pciehp: Cannot get control of hotplug hardware for pci 0000:00:1c.3
[   26.827525] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   27.095304] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   27.095316] apm: disabled - APM is not SMP safe.
[   27.311159] ppdev: user-space parallel port driver
[   27.477381] audit(1240229439.784:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4838 profile="/usr/sbin/cupsd" namespace="default"
[   30.213004] RX DESC dfdab000  size = 2048
[   30.213547] <-- RTMPAllocTxRxRingMemory, Status=0
[   30.309532] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   30.309653] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   30.309825] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   30.309949] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   30.311801] 1. Phy Mode = 9
[   30.311815] 2. Phy Mode = 9
[   30.333792] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   30.341457] 3. Phy Mode = 9
[   30.347196] MCS Set = ff ff 00 00 01
[   30.348846] <==== RTMPInitialize, Status=0
[   30.348935] 0x1300 = 00064300
[   30.392957] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   30.405876] Bluetooth: L2CAP ver 2.9
[   30.405894] Bluetooth: L2CAP socket layer initialized
[   30.518535] Bluetooth: RFCOMM socket layer initialized
[   30.518573] Bluetooth: RFCOMM TTY layer initialized
[   30.518581] Bluetooth: RFCOMM ver 1.8
[   32.700003] NET: Registered protocol family 17
[   34.861191] [drm] Initialized drm 1.1.0 20060810
[   34.871321] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.871354] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   34.871586] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.448296] NET: Registered protocol family 10
[   36.449695] lo: Disabled Privacy Extensions
[   40.956736] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[   47.113449] eth0: no IPv6 routers present
[   47.270272] ra0: no IPv6 routers present
[   70.946757] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[   89.985500] ATL1e: eth0 NIC Link is Down
[  104.279762] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  104.282984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  119.836938] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  126.949677] eth0: no IPv6 routers present
[  132.343285] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  149.819843] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  162.322453] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  179.804988] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  192.304467] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  209.794986] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  222.294472] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  239.785016] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  252.280495] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  369.667199] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[  382.158740] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  499.545384] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 376
[  512.040898] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  629.427567] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[  641.923076] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[  703.254745] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  703.254808] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  703.256598] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  712.638696] RX DESC dfbd4000  size = 2048
[  712.639260] <-- RTMPAllocTxRxRingMemory, Status=0
[  712.643898] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[  712.643982] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[  712.644042] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[  712.644103] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[  712.645046] 1. Phy Mode = 9
[  712.645055] 2. Phy Mode = 9
[  712.666667] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  712.674194] 3. Phy Mode = 9
[  712.679905] MCS Set = ff ff 00 00 01
[  712.681559] <==== RTMPInitialize, Status=0
[  712.681639] 0x1300 = 00064300
[  712.765485] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  712.765560] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  712.768000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  713.622219] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[  723.289767] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  724.400508] ra0: no IPv6 routers present
[  729.592302] eth0: no IPv6 routers present
[  785.583567] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 493
[  789.091854] eth0: no IPv6 routers present
[  798.647429] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 493
[  815.569534] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  828.628519] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  845.555562] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  858.606541] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[  875.537623] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  888.584562] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  905.519658] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  918.562618] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[ 1035.401794] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[ 1048.440771] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[ 1165.285007] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[ 1178.318990] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[ 1295.163188] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[ 1308.197147] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[ 1404.514257] RX DESC dfbd4000  size = 2048
[ 1404.515205] <-- RTMPAllocTxRxRingMemory, Status=0
[ 1404.522099] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 1404.522241] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 1404.522366] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 1404.522494] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 1404.527031] 1. Phy Mode = 9
[ 1404.527050] 2. Phy Mode = 9
[ 1404.549335] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 1404.557225] 3. Phy Mode = 9
[ 1404.562959] MCS Set = ff ff 00 00 01
[ 1404.564619] <==== RTMPInitialize, Status=0
[ 1404.564709] 0x1300 = 00064300
[ 1415.465814] ra0: no IPv6 routers present
[ 4723.927605] RX DESC f340f000  size = 2048
[ 4723.928460] <-- RTMPAllocTxRxRingMemory, Status=0
[ 4723.934813] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 4723.934931] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 4723.935037] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 4723.935149] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 4723.940221] 1. Phy Mode = 9
[ 4723.940240] 2. Phy Mode = 9
[ 4723.962581] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 4723.970357] 3. Phy Mode = 9
[ 4723.976078] MCS Set = ff ff 00 00 01
[ 4723.977731] <==== RTMPInitialize, Status=0
[ 4723.977821] 0x1300 = 00064300
[ 4734.433602] ra0: no IPv6 routers present
[ 4794.862702] RX DESC f3732000  size = 2048
[ 4794.863123] <-- RTMPAllocTxRxRingMemory, Status=0
[ 4794.867323] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 4794.867363] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 4794.867402] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 4794.867442] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 4794.868033] 1. Phy Mode = 9
[ 4794.868036] 2. Phy Mode = 9
[ 4794.888795] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 4794.896079] 3. Phy Mode = 9
[ 4794.901808] MCS Set = ff ff 00 00 01
[ 4794.903455] <==== RTMPInitialize, Status=0
[ 4794.903538] 0x1300 = 00064300
[ 4805.617484] ra0: no IPv6 routers present
[ 4889.980036] RX DESC dfee8000  size = 2048
[ 4889.980925] <-- RTMPAllocTxRxRingMemory, Status=0
[ 4889.986295] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[ 4889.986423] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[ 4889.986546] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[ 4889.986669] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[ 4889.988436] 1. Phy Mode = 9
[ 4889.988450] 2. Phy Mode = 9
[ 4890.010803] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 4890.018555] 3. Phy Mode = 9
[ 4890.024294] MCS Set = ff ff 00 00 01
[ 4890.025939] <==== RTMPInitialize, Status=0
[ 4890.026021] 0x1300 = 00064300
[ 4900.958189] ra0: no IPv6 routers present
dan@dan-netbook:~/wireless/2008_0325_RT2860_Linux_STA_v1.6.1.0/os/linux$ 


```

plus some more stuff above that. Does that contain what you were looking for?

---

### Post by woodsonoversoul on 2009-04-20
Alright, headed to school. Thanks for all the help so far! Keep it coming!

---

### Post by woodsonoversoul on 2009-04-21
bump for today

---

### Post by Saghaulor on 2009-04-21
I'm no expert, but I'll try to help as much as I can.

From your dmesg output, I can see two network interfaces.

An Atheros chipset, which is probably your eth0.
> [   18.998562] Atheros(R) AR8121/AR8113 PCI-E Ethernet Network Driver - version 1.0.0.4
[   18.998571] Copyright (c) 2007 Atheros Corporation.
[   30.392957] ATL1e: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   47.113449] eth0: no IPv6 routers present

And then ra0, which is probably your Ralink chipset (wireless).
> [   30.309532] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!
[   30.309653] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!
[   30.309825] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!
[   30.309949] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!
[   30.311801] 1. Phy Mode = 9
[   30.311815] 2. Phy Mode = 9
[   30.333792] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   30.341457] 3. Phy Mode = 9
[   30.347196] MCS Set = ff ff 00 00 01
[   30.348846] <==== RTMPInitialize, Status=0
[   47.270272] ra0: no IPv6 routers present

These may be related to the ra0 interface.
> [  132.343285] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  149.819843] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  162.322453] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  179.804988] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  192.304467] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  209.794986] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  222.294472] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 368
[  239.785016] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  252.280495] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  369.667199] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[  382.158740] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 485
[  499.545384] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 376
[  512.040898] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 286
[  629.427567] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403
[  641.923076] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 403


Try this, first, see what interfaces are listed.
```
sudo ifconfig
```
Hopefully it will report ra0 as an interface.

Also, try ```
sudo iwlist ra0 scan
```

Hopefully that scans for access points.

I'm trying to find a thread that was very helpful to me when I was having wireless issues. I'll post it when I find it.

---

### Post by Saghaulor on 2009-04-21
If your chipset was like mine, you could try
```
lsusb
```
It will list all the usb interfaces, and my wifi card was part of the usb system. From there we may be able to determine more about your chipset.

---

### Post by woodsonoversoul on 2009-04-21
Thanks. I'll try it as soon as I get home

---

### Post by Saghaulor on 2009-04-21
You might have to try ```
lspci
``` if your wifi isn't actually a usb chipset.
Also, you can pipe your output into Grep, to narrow the results down to what you're looking for. That is, if you know what you're looking for.

Something like this. ```
lsusb | grep .ireless
```
The period functions as a wildcard. But grep is only as effective as what you tell it to search for. So it might not be helpful in this instance unless you really wildcard/variable it out. Lsusb and lspci shouldn't report too much, so it should be fairly easy to read.

---

### Post by woodsonoversoul on 2009-04-21
lsusb:
Bus 005 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: RaLink Unknown device 0781
03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

so it's a RaLink, which I thought but wasn't sure of since I've been installing so many drivers and editing so many system files (I thought the 'RaLink' might have been something I did)

---

### Post by woodsonoversoul on 2009-04-21
and thanks for the info on grep

---

### Post by Saghaulor on 2009-04-21
Now we just need to figure out which driver to use, and then get it working.

Any luck with scanning with ra0 instead of wlan0?

---

### Post by woodsonoversoul on 2009-04-21
can you explain 'scanning'?

---

### Post by Saghaulor on 2009-04-21
Scanning for an access point. 

Remember, ```
sudo iwlist ra0 scan
```

If if returns something like the following, then the wifi drivers are working, at least, in part.

> \wlan0     Scan completed :
          Cell 01 - Address: 00:21:7C:EE:FE:89
                    ESSID:"2WIRE920"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/100  Signal level:-81 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000156988f3181
                    Extra: Last beacon: 1576ms ago


---

### Post by woodsonoversoul on 2009-04-21
sudo iwlist ra0 scan:
ra0       Scan completed :
          Cell 01 - Address: 00:1C:DF:8B:7E:C5
                    ESSID:"Trutle"
                    Mode:Managed
                    Channel:11
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s

          Cell 02 - Address: 00:12:0E:0B:89:EA
                    ESSID:"WEST8955"
                    Mode:Managed
                    Channel:6
                    Quality:24/100  Signal level:-80 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s

          Cell 03 - Address: 00:24:56:60:D0:19
                    ESSID:"2WIRE341"
                    Mode:Managed
                    Channel:6
                    Quality:34/100  Signal level:-76 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s

          Cell 04 - Address: 00:18:F3:71:17:E1
                    ESSID:"HARTMAN"
                    Mode:Managed
                    Channel:11
                    Quality:10/100  Signal level:-86 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

          Cell 05 - Address: 00:22:3F:7C:3D:F2
                    ESSID:"ourhouse"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-33 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


 sudo iwlist wlan0 scan:
wlan0     Interface doesn't support scanning.



So does this mean my driver IS working?

---

### Post by Saghaulor on 2009-04-21
It would appear so.

Try this ```
sudo ifconfig ra0
```

---

### Post by Saghaulor on 2009-04-21
It seems the driver is working, as it's scanning access points.

The above command will tell us more about your wireless interface. 

Is one of the above listed access points yours? Is it encrypted with WEP or WPA?

---

### Post by woodsonoversoul on 2009-04-21
I don't see an above command, and the last network on the list is my local network  but I'm not sure of it's encryption (I finally broke down after a year and bought internet from Comcast, 2 days later my laptop wifi goes out :( ), but I'll look around for the info the installer left. I should be able to detect this on a windows system, yes?

---

### Post by Saghaulor on 2009-04-21
"The above command" referred to a command on the previous page of this thread.

In regards to your internet/wifi. Okay, so you subscribe to Comcast. Good, that's a start. Do you have a wireless router connected to your Comcast modem?

If you do not, then this would explain why you are not connecting to your internet wirelessly.

Also, notice how there are several entries listed as results from your "iwlist ra0 scan" command?

Each one has a field called "Essid" That's the broadcast name of a wifi access point. If you have a wireless router you should have named the connection, or if you left it as its default, it might be something like, Belkin, or Linksys, etc.

If you don't have a wireless router then all of this is irrelevant as you should be connecting via a wire, that is, until you get a wifi router.

Also, can you disable smiles when you post, some of your posts are screwed up.

---

### Post by woodsonoversoul on 2009-04-21
Thanks so much for taking your time with me. Yes I do have a wireless router (however, I've been using a cable to connect through it since I can't via wireless, and I've been running these commands. Don't know if that might have screwed up the results...) And yes my network is called 'ourhouse', the last network on the list.

I can see the available networks via clicking the icon at the top right of the screen, I just can't connect (this may be different from what I said earlier, but as I've said, I've tried many different approaches. I've stopped experimenting now, and am just moving along with this thread)

And yeah, I guess my previous post looked a little silly. Smilies are off now...

---

### Post by Saghaulor on 2009-04-21
Not a problem, it's good to give back when I can.

Okay, so we're making good headway. You've got a wifi router, and you have what appears to be working wifi drivers on your netbook.

We can see your router, called 'ourhouse', good.

I believe that now the issue is an encrypted wifi signal. Not a problem, let's see if we can fix this once and for all.

First, I would try to log into your router, and turn off wifi encryption. Then try to connect to your router without the encryption. If it connects, then we know it's not fritz drivers, or at least, they're working enough to actually connect. I would turn your encryption back on when you're done testing.

I believe you may be using WPA encryption. I know that back in the day some drivers were having issues with WPA authentication.

What version of Ubuntu are you using?

---

### Post by woodsonoversoul on 2009-04-21
I'm using 8.04 with an eee-pc system.

I'm googling it right now, but how do I log on to my router?

---

### Post by woodsonoversoul on 2009-04-21
Alright, figured out how to get to the login screen. Now I'm trying to remember my login info. Windows logs in normally w/o prompting for a password. Can I get my login info from windows?

---

### Post by Saghaulor on 2009-04-21
Depends on the brand of router or if the default ip address has been changed. In any event you type the routers ip address into your browser and then it will prompt youb for credentials.then obviously you need the account info. Try 192.168.1.1 or 192.168.2.2, as those are popular default ips of most routers.

---

### Post by Saghaulor on 2009-04-21
Your Windows password and your router password are two separate passwords, unless you use the same password for everything, in which case they would be the same.Windows will only have your router password if you use the same password for everything or if you saved the router password in a text file or password keychain.

If you used the default password you can find the password in the router's instruction documentation.

---

### Post by woodsonoversoul on 2009-04-21
I know my password, but can't locate my username. Do you think comcast might store it/be able to retrieve it? I'm working on it...

---

### Post by woodsonoversoul on 2009-04-21
What I mean about Windows is; since windows can log into my wireless network, surely it has those credentials stored somewhere...

---

### Post by woodsonoversoul on 2009-04-21
Alright. Called Comcast and reset my credentials

---

### Post by woodsonoversoul on 2009-04-21
OOOOHHHHHH and turning off the encryption worked!!! Thanks so much!! Now to go back through and build up my security again. any suggestions?

---

### Post by Saghaulor on 2009-04-21
Your Internet Service Provider, ISP (Comcast) will not have this information.

Generally, the username is 'admin', unless you have changed it.

If worse comes to worst, you can always reset your router. I would only recommend this as a last resort because all settings will be erased.

But in the event that you do reset the router, everything will revert back to the manufacturer defaults, which means you should be able to find the info in the router documentation or via google.

---

### Post by Saghaulor on 2009-04-21
Just to be sure, you connected to your router wirelessly, and made sure that you didn't have the wire plugged in?

---

### Post by woodsonoversoul on 2009-04-21
yeah comcast instructed me to reset the router, but everything works great now

---

### Post by woodsonoversoul on 2009-04-21
and yes, totally wireless. Thanks so much man. Is there anyway I can mark this solved, or give you rep points or something?

---

### Post by Saghaulor on 2009-04-21
I think that they disabled the 'thanks' feature. Oh well.

I would recommend reconfiguring the security of your router. Make sure to document all change that you made, so that you can backtrack if things don't work out.

WPA2 is the best form of wireless encryption out. Not all hardware supports it. You may need to use WPA. 

I recommend encrypting your wireless for a few reasons. Without encryption, it's a way for bad guys to listen/watch what you're doing as you surf the net. It's also a free pipeline for people to do bad stuff on your internet that will inevitably trace back to you. 

WEP encryption is almost useless. It can be hacked in two minutes or less under the right circumstances. But even WEP is better than nothing.

---

### Post by woodsonoversoul on 2009-04-21
Well thanks again

---

