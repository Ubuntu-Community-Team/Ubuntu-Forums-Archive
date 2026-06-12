---
title: "low disk space"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by garage jack on 2009-12-03
sometimes my ubuntu gives me some kind of error, low disk space, something like,** you have 864,98 mb free space, try to empty trash or remove some programs** or something like that when i have lets say 8 gb of free space on my drive. and when i restart my computer, everything is normal again. why is this happening?

---

### Post by yeats on 2009-12-03
Could you open a terminal and do:

```
df -h
```

Then list the output here?

---

### Post by llamabr on 2009-12-03
You have a bunch of trash that gets deleted when you reboot, though that's not necessarily to the correct solution to emptying it (one need not be in the 'a reboot is the solution to a problem' mindset with linux).

Have a look in your ~/local/share/Trash/ folder.  Gnome, or more specifically, nautalus, sticks everything in there.  I guess in case you accidentally delete something you didn't want to delete.

Ubuntu is very hand-holding, and forgiving of mistakes, but causes these clogs as a consequense.

---

### Post by garage jack on 2009-12-03
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              19G   11G  7.3G  59% /
udev                  752M  276K  752M   1% /dev
none                  752M  496K  752M   1% /dev/shm
none                  752M  196K  752M   1% /var/run
none                  752M     0  752M   0% /var/lock
none                  752M     0  752M   0% /lib/init/rw
 here is a list

---

### Post by Chame_Wizard on 2009-12-03
> **garage jack said:**
> ```

Filesystem            Size  Used Avail Use% Mounted on
[B]
/dev/sdb6              19G   11G  7.3G  59% /[/B]
udev                  752M  276K  752M   1% /dev
none                  752M  496K  752M   1% /dev/shm
none                  752M  196K  752M   1% /var/run
none                  752M     0  752M   0% /var/lock
none                  752M     0  752M   0% /lib/init/rw
```
 here is a list

That's strange,seems like you have enough HDD free space left.So how's is it possible you have only 865 MiB left?

can you post the system log here?
```
dmesg
``` or /var/log/dmesg or /var/log/messages

---

### Post by kansasnoob on 2009-12-03
You might also post the output of:

```
sudo du -sh /*
```

That may or may not be helpful.

---

### Post by garage jack on 2009-12-03
> That's strange,seems like you have enough HDD free space left.So how's is it possible you have only 865 MiB left?


you didn't understand. when i watch movie or play chess or something else all of the sudden ubuntu starts giving those messages. also reports that disk space is shrinking, 900, 865 and one time 0! and when i check disk space it is really 900, 865 and 0. but, when i restart my computer, everything is normal, i have my 8 or so gb free. this thing happend twice.

---

### Post by garage jack on 2009-12-03
5.9M    /bin
15M    /boot
0    /cdrom
936K    /dev
17M    /etc
du: cannot access `/home/miroslav/.gvfs': Permission denied
2.1G    /home
0    /initrd.img
158M    /lib
13M    /lib32
0    /lib64
16K    /lost+found
8.0K    /media
4.0K    /mnt
77M    /opt
du: cannot access `/proc/3743/task/3743/fd/3': No such file or directory
du: cannot access `/proc/3743/task/3743/fdinfo/3': No such file or directory
du: cannot access `/proc/3743/fd/3': No such file or directory
du: cannot access `/proc/3743/fdinfo/3': No such file or directory
0    /proc
6.4M    /root
8.7M    /sbin
4.0K    /selinux
200K    /srv
0    /sys
76K    /tmp
4.6G    /usr
3.2G    /var
0    /vmlinuz
4.0K    /windows

---

### Post by garage jack on 2009-12-03
[    0.014438] Initializing cgroup subsys freezer
[    0.014441] Initializing cgroup subsys net_cls
[    0.014466] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.014470] CPU: L2 cache: 512K
[    0.014475] CPU 0/0x0 -> Node 0
[    0.014477] CPU: Hyper-Threading is disabled
[    0.014482] mce: CPU supports 4 MCE banks
[    0.014497] CPU0: Thermal monitoring enabled (TM1)
[    0.014504] using mwait in idle threads.
[    0.014506] Performance Counters: no PMU driver, software counters only.
[    0.014522] SMP alternatives: switching to UP code
[    0.026505] ACPI: Core revision 20090521
[    0.035740] Setting APIC routing to flat
[    0.036043] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136083] CPU0: Intel(R) Celeron(R) D CPU 3.20GHz stepping 05
[    0.140000] Brought up 1 CPUs
[    0.140000] Total of 1 processors activated (6431.56 BogoMIPS).
[    0.140000] CPU0 attaching NULL sched-domain.
[    0.140000] Booting paravirtualized kernel on bare hardware
[    0.140000] regulator: core version 0.5
[    0.140000] Time: 13:29:14  Date: 12/03/09
[    0.140000] NET: Registered protocol family 16
[    0.140000] ACPI: bus type pci registered
[    0.140000] PCI: Using configuration type 1 for base access
[    0.140000] bio: create slab <bio-0> at 0
[    0.140000] ACPI: EC: Look up EC in DSDT
[    0.140000] ACPI: Interpreter enabled
[    0.140000] ACPI: (supports S0 S1 S4 S5)
[    0.140000] ACPI: Using IOAPIC for interrupt routing
[    0.141779] ACPI: No dock devices found.
[    0.141944] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.142003] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.142015] pci 0000:00:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.142124] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    0.142233] pci 0000:00:1d.0: reg 20 io port: [0xac00-0xac1f]
[    0.142292] pci 0000:00:1d.1: reg 20 io port: [0xa000-0xa01f]
[    0.142349] pci 0000:00:1d.2: reg 20 io port: [0xa400-0xa41f]
[    0.142405] pci 0000:00:1d.3: reg 20 io port: [0xa800-0xa81f]
[    0.142461] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfa100000-0xfa1003ff]
[    0.142516] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.142522] pci 0000:00:1d.7: PME# disabled
[    0.142612] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.142620] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.142625] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH4 GPIO
[    0.142651] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.142658] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.142665] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.142672] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.142679] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.142687] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.142742] pci 0000:00:1f.3: reg 20 io port: [0x1400-0x141f]
[    0.142791] pci 0000:00:1f.5: reg 10 io port: [0xb400-0xb4ff]
[    0.142799] pci 0000:00:1f.5: reg 14 io port: [0xb800-0xb83f]
[    0.142805] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfa101000-0xfa1011ff]
[    0.142812] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfa102000-0xfa1020ff]
[    0.142843] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.142848] pci 0000:00:1f.5: PME# disabled
[    0.142892] pci 0000:01:00.0: reg 10 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.142899] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.142919] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.142980] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.142985] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.143031] pci 0000:02:08.0: reg 10 32bit mmio: [0xfa000000-0xfa000fff]
[    0.143038] pci 0000:02:08.0: reg 14 io port: [0x9000-0x903f]
[    0.143077] pci 0000:02:08.0: supports D1 D2
[    0.143080] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.143084] pci 0000:02:08.0: PME# disabled
[    0.143119] pci 0000:00:1e.0: transparent bridge
[    0.143124] pci 0000:00:1e.0: bridge io port: [0x9000-0x9fff]
[    0.143129] pci 0000:00:1e.0: bridge 32bit mmio: [0xfa000000-0xfa0fffff]
[    0.143148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.143279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.150497] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.150621] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.150742] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.150862] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.150982] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.151102] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.151223] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.151348] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.151617] SCSI subsystem initialized
[    0.151722] libata version 3.00 loaded.
[    0.151833] usbcore: registered new interface driver usbfs
[    0.151860] usbcore: registered new interface driver hub
[    0.151892] usbcore: registered new device driver usb
[    0.152068] ACPI: WMI: Mapper loaded
[    0.152071] PCI: Using ACPI for IRQ routing
[    0.152259] Bluetooth: Core ver 2.15
[    0.152311] NET: Registered protocol family 31
[    0.152313] Bluetooth: HCI device and connection manager initialized
[    0.152317] Bluetooth: HCI socket layer initialized
[    0.152319] NetLabel: Initializing
[    0.152321] NetLabel:  domain hash size = 128
[    0.152323] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.152340] NetLabel:  unlabeled traffic allowed by default
[    0.152472] hpet clockevent registered
[    0.152476] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.152482] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.152488] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.162504] pnp: PnP ACPI init
[    0.162548] ACPI: bus type pnp registered
[    0.165524] pnp: PnP ACPI: found 11 devices
[    0.165527] ACPI: ACPI bus type pnp unregistered
[    0.165543] system 00:00: iomem range 0xcf400-0xcffff has been reserved
[    0.165547] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.165550] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.165553] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.165556] system 00:00: iomem range 0x5fff0000-0x5fffffff could not be reserved
[    0.165559] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.165562] system 00:00: iomem range 0x100000-0x5ffeffff could not be reserved
[    0.165566] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.165569] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.165572] system 00:00: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.165575] system 00:00: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.165578] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.165581] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.165592] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.165596] system 00:03: ioport range 0x290-0x29f has been reserved
[    0.165599] system 00:03: ioport range 0x800-0x805 has been reserved
[    0.165602] system 00:03: ioport range 0x880-0x88f has been reserved
[    0.170346] AppArmor: AppArmor Filesystem Enabled
[    0.170388] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.170391] pci 0000:00:01.0:   IO window: disabled
[    0.170397] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf9ffffff
[    0.170402] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf7ffffff
[    0.170407] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.170411] pci 0000:00:1e.0:   IO window: 0x9000-0x9fff
[    0.170416] pci 0000:00:1e.0:   MEM window: 0xfa000000-0xfa0fffff
[    0.170421] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.170438] pci 0000:00:1e.0: setting latency timer to 64
[    0.170444] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.170447] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.170450] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.170452] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.170455] pci_bus 0000:02: resource 0 io:  [0x9000-0x9fff]
[    0.170458] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfa0fffff]
[    0.170460] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.170463] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.170512] NET: Registered protocol family 2
[    0.170673] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.171913] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.176594] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.177777] TCP: Hash tables configured (established 262144 bind 65536)
[    0.177784] TCP reno registered
[    0.178007] NET: Registered protocol family 1
[    0.178131] Trying to unpack rootfs image as initramfs...
[    0.403931] Freeing initrd memory: 7927k freed
[    0.414601] Scanning for low memory corruption every 60 seconds
[    0.414806] audit: initializing netlink socket (disabled)
[    0.414832] type=2000 audit(1259846954.409:1): initialized
[    0.422798] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.424295] VFS: Disk quotas dquot_6.5.2
[    0.424376] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.425225] fuse init (API version 7.12)
[    0.425330] msgmni has been set to 3006
[    0.425632] alg: No test for stdrng (krng)
[    0.425651] io scheduler noop registered
[    0.425655] io scheduler anticipatory registered
[    0.425657] io scheduler deadline registered
[    0.425737] io scheduler cfq registered (default)
[    0.425855] pci 0000:01:00.0: Boot video device
[    0.425867] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.426049] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.426078] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.426230] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.426235] ACPI: Power Button [PWRF]
[    0.426288] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.426292] ACPI: Power Button [PWRB]
[    0.426353] fan PNP0C0B:00: registered as cooling_device0
[    0.426361] ACPI: Fan [FAN] (on)
[    0.426616] processor LNXCPU:00: registered as cooling_device1
[    0.428459] thermal LNXTHERM:01: registered as thermal_zone0
[    0.428469] ACPI: Thermal Zone [THRM] (22 C)
[    0.430068] Linux agpgart interface v0.103
[    0.430075] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.430181] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.430530] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.431740] brd: module loaded
[    0.432307] loop: module loaded
[    0.432438] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.432686] ata_piix 0000:00:1f.1: version 2.13
[    0.432712]   alloc irq_desc for 18 on node 0
[    0.432715]   alloc kstat_irqs on node 0
[    0.432726] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.432788] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.432882] scsi0 : ata_piix
[    0.433026] scsi1 : ata_piix
[    0.434020] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.434024] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.434902] Fixed MDIO Bus: probed
[    0.434954] PPP generic driver version 2.4.2
[    0.435104] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.435336]   alloc irq_desc for 23 on node 0
[    0.435339]   alloc kstat_irqs on node 0
[    0.435349] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.435374] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.435379] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.435462] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.439392] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.439413] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa100000
[    0.460000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.460140] usb usb1: configuration #1 chosen from 1 choice
[    0.460177] hub 1-0:1.0: USB hub found
[    0.460187] hub 1-0:1.0: 8 ports detected
[    0.460310] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.460342] uhci_hcd: USB Universal Host Controller Interface driver
[    0.460705]   alloc irq_desc for 16 on node 0
[    0.460710]   alloc kstat_irqs on node 0
[    0.460720] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.460731] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.460735] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.460823] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.460864] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ac00
[    0.460968] usb usb2: configuration #1 chosen from 1 choice
[    0.461001] hub 2-0:1.0: USB hub found
[    0.461011] hub 2-0:1.0: 2 ports detected
[    0.461128]   alloc irq_desc for 19 on node 0
[    0.461131]   alloc kstat_irqs on node 0
[    0.461138] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.461146] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.461150] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.461208] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.461250] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a000
[    0.461347] usb usb3: configuration #1 chosen from 1 choice
[    0.461377] hub 3-0:1.0: USB hub found
[    0.461386] hub 3-0:1.0: 2 ports detected
[    0.461489] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.461497] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.461501] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.461551] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.461588] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a400
[    0.461683] usb usb4: configuration #1 chosen from 1 choice
[    0.461717] hub 4-0:1.0: USB hub found
[    0.461727] hub 4-0:1.0: 2 ports detected
[    0.461827] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.461836] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.461839] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.461886] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.461916] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a800
[    0.462019] usb usb5: configuration #1 chosen from 1 choice
[    0.462054] hub 5-0:1.0: USB hub found
[    0.462064] hub 5-0:1.0: 2 ports detected
[    0.462195] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.462199] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.462284] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.462370] mice: PS/2 mouse device common for all mice
[    0.462482] rtc_cmos 00:05: RTC can wake from S4
[    0.462528] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.462556] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.462720] device-mapper: uevent: version 1.0.3
[    0.462898] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.462969] device-mapper: multipath: version 1.1.0 loaded
[    0.462974] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.463137] cpuidle: using governor ladder
[    0.463140] cpuidle: using governor menu
[    0.463668] TCP cubic registered
[    0.463819] NET: Registered protocol family 10
[    0.464334] lo: Disabled Privacy Extensions
[    0.464640] NET: Registered protocol family 17
[    0.464685] Bluetooth: L2CAP ver 2.13
[    0.464687] Bluetooth: L2CAP socket layer initialized
[    0.464690] Bluetooth: SCO (Voice Link) ver 0.6
[    0.464692] Bluetooth: SCO socket layer initialized
[    0.464771] Bluetooth: RFCOMM TTY layer initialized
[    0.464774] Bluetooth: RFCOMM socket layer initialized
[    0.464776] Bluetooth: RFCOMM ver 1.11
[    0.464952] PM: Resume from disk failed.
[    0.464970] registered taskstats version 1
[    0.465083]   Magic number: 5:565:482
[    0.465211] rtc_cmos 00:05: setting system clock to 2009-12-03 13:29:14 UTC (1259846954)
[    0.465216] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.465218] EDD information not available.
[    0.480875] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.610538] ata2.00: ATAPI: PIONEER DVD-RW  DVR-110D, 1.17, max UDMA/33
[    0.650286] ata2.00: configured for UDMA/33
[    0.659954] Switched to high resolution mode on CPU 0
[    0.670295] ata1.00: HPA unlocked: 160084415 -> 160086528, native 160086528
[    0.670301] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    0.670304] ata1.00: 160086528 sectors, multi 16: LBA 
[    0.700270] ata1.01: HPA unlocked: 312579695 -> 312581808, native 312581808
[    0.700274] ata1.01: ATA-7: WDC WD1600AAJB-00PVA0, 00.07H00, max UDMA/100
[    0.700277] ata1.01: 312581808 sectors, multi 16: LBA48 
[    0.740333] ata1.00: configured for UDMA/100
[    0.781367] ata1.01: configured for UDMA/100
[    0.781517] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    0.781698] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.781781] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1600AAJB-0 00.0 PQ: 0 ANSI: 5
[    0.781896] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.781948] sd 0:0:0:0: [sda] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    0.782018] sd 0:0:0:0: [sda] Write Protect is off
[    0.782022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.782056] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.782248]  sda:
[    0.788838] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.17 PQ: 0 ANSI: 5
[    0.806464]  sda1 sda2 <sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    0.807201] Uniform CD-ROM driver Revision: 3.20
[    0.807334] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.807414] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    0.823357]  sda5 >
[    0.823699] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.823713] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.823775] sd 0:0:1:0: [sdb] Write Protect is off
[    0.823778] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    0.823809] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.823973]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[    0.858866] sd 0:0:1:0: [sdb] Attached SCSI disk
[    0.858894] Freeing unused kernel memory: 660k freed
[    0.859585] Write protecting the kernel read-only data: 7580k
[    1.039722] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    1.046570] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    1.111069] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.111074] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.111208]   alloc irq_desc for 20 on node 0
[    1.111212]   alloc kstat_irqs on node 0
[    1.111223] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.134934] e100 0000:02:08.0: PME# disabled
[    1.140062] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.214206] e100: eth0: e100_probe: addr 0xfa000000, irq 20, MAC addr 00:1a:4d:89:a4:74
[    1.320192] usb 3-1: configuration #1 chosen from 1 choice
[    1.329282] usbcore: registered new interface driver hiddev
[    1.342343] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[    1.342458] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[    1.342485] usbcore: registered new interface driver usbhid
[    1.342490] usbhid: v2.6:USB HID core driver
[    1.600029] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.840517] usb 4-2: configuration #1 chosen from 1 choice
[    2.355595] xor: automatically using best checksumming function: generic_sse
[    2.400008]    generic_sse:  4908.000 MB/sec
[    2.400011] xor: using function: generic_sse (4908.000 MB/sec)
[    2.431462] device-mapper: dm-raid45: initialized v0.2594b
[    2.629928] PM: Starting manual resume from disk
[    2.629935] PM: Resume from partition 8:21
[    2.629937] PM: Checking hibernation image.
[    2.630227] PM: Resume from disk failed.
[    2.662365] kjournald starting.  Commit interval 5 seconds
[    2.662391] EXT3-fs: mounted filesystem with writeback data mode.
[    3.373682] type=1505 audit(1259846957.404:2): operation="profile_load" pid=384 name=/usr/share/gdm/guest-session/Xsession
[    3.397568] type=1505 audit(1259846957.424:3): operation="profile_load" pid=385 name=/sbin/dhclient3
[    3.398241] type=1505 audit(1259846957.424:4): operation="profile_load" pid=385 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.398608] type=1505 audit(1259846957.424:5): operation="profile_load" pid=385 name=/usr/lib/connman/scripts/dhclient-script
[    3.420546] type=1505 audit(1259846957.454:6): operation="profile_load" pid=386 name=/usr/bin/evince
[    3.432050] type=1505 audit(1259846957.464:7): operation="profile_load" pid=386 name=/usr/bin/evince-previewer
[    3.438612] type=1505 audit(1259846957.464:8): operation="profile_load" pid=386 name=/usr/bin/evince-thumbnailer
[    3.457817] type=1505 audit(1259846957.484:9): operation="profile_load" pid=388 name=/usr/lib/cups/backend/cups-pdf
[    3.458605] type=1505 audit(1259846957.484:10): operation="profile_load" pid=388 name=/usr/sbin/cupsd
[    4.829704] Adding 979924k swap on /dev/sdb5.  Priority:-1 extents:1 across:979924k 
[    5.407032] udev: starting version 147
[    6.189812] EXT3 FS on sdb6, internal journal
[    6.336011] lp: driver loaded but no devices found
[    6.413985] parport_pc 00:09: reported by Plug and Play ACPI
[    6.414045] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    6.423547] ppdev: user-space parallel port driver
[    6.490251] lp0: using parport0 (interrupt-driven).
[    7.334009] intel_rng: FWH not detected
[    7.529317] Linux video capture interface: v2.00
[    7.606916] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.622126] gspca: main v2.6.0 registered
[    7.650053] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.785058] gspca: probing 093a:2468
[    7.787667] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[    7.787672] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[    7.790136] gspca: probe ok
[    7.790166] usbcore: registered new interface driver pac207
[    7.790170] pac207: registered
[    8.607310] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    8.607624] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    8.607628] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[    8.607630] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   10.048968] nvidia: module license 'NVIDIA' taints kernel.
[   10.048975] Disabling lock debugging due to kernel taint
[   10.319704] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.319977] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.20  Thu Jun 25 18:15:32 PDT 2009
[   11.109742] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   11.569815]   alloc irq_desc for 17 on node 0
[   11.569820]   alloc kstat_irqs on node 0
[   11.569830] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.569908] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   11.900029] intel8x0_measure_ac97_clock: measured 50525 usecs (2436 samples)
[   11.900034] intel8x0: clocking to 48000
[   11.982620] __ratelimit: 12 callbacks suppressed
[   11.982624] type=1505 audit(1259843366.014:15): operation="profile_replace" pid=1014 name=/usr/share/gdm/guest-session/Xsession
[   11.985703] type=1505 audit(1259843366.014:16): operation="profile_replace" pid=1015 name=/sbin/dhclient3
[   11.986393] type=1505 audit(1259843366.014:17): operation="profile_replace" pid=1015 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   11.986773] type=1505 audit(1259843366.014:18): operation="profile_replace" pid=1015 name=/usr/lib/connman/scripts/dhclient-script
[   11.992962] type=1505 audit(1259843366.024:19): operation="profile_replace" pid=1016 name=/usr/bin/evince
[   12.004766] type=1505 audit(1259843366.034:20): operation="profile_replace" pid=1016 name=/usr/bin/evince-previewer
[   12.011719] type=1505 audit(1259843366.044:21): operation="profile_replace" pid=1016 name=/usr/bin/evince-thumbnailer
[   12.023019] type=1505 audit(1259843366.054:22): operation="profile_replace" pid=1018 name=/usr/lib/cups/backend/cups-pdf
[   12.023856] type=1505 audit(1259843366.054:23): operation="profile_replace" pid=1018 name=/usr/sbin/cupsd
[   12.027202] type=1505 audit(1259843366.054:24): operation="profile_replace" pid=1019 name=/usr/sbin/mysqld
[   13.505090] usplash:313 freeing invalid memtype fffffffff0000000-fffffffff8000000
[   15.042024] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.040141] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   17.040622] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.369046] __ratelimit: 12 callbacks suppressed
[   17.369051] type=1503 audit(1259843371.394:29): operation="open" pid=1229 parent=1228 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   18.448696] type=1503 audit(1259843372.474:30): operation="open" pid=1314 parent=1313 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.476661] type=1503 audit(1259843373.504:31): operation="open" pid=1328 parent=1327 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.640790] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   19.640810] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   19.640846] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   20.605513] type=1503 audit(1259843374.634:32): operation="open" pid=1348 parent=1347 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.643363] type=1503 audit(1259843375.674:33): operation="open" pid=1549 parent=1548 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.694741] type=1503 audit(1259843376.724:34): operation="open" pid=1601 parent=1600 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   23.747137] type=1503 audit(1259843377.774:35): operation="open" pid=1686 parent=1685 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   24.799106] type=1503 audit(1259843378.824:36): operation="open" pid=1718 parent=1717 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.825162] type=1503 audit(1259843382.802:37): operation="open" pid=1795 parent=1794 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.866932] type=1503 audit(1259843383.842:38): operation="open" pid=1814 parent=1813 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.897539] type=1503 audit(1259843384.872:39): operation="open" pid=1838 parent=1837 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   28.010019] eth0: no IPv6 routers present
[   28.926226] type=1503 audit(1259843385.902:40): operation="open" pid=1892 parent=1891 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   29.959031] type=1503 audit(1259843386.932:41): operation="open" pid=1904 parent=1903 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   30.993449] type=1503 audit(1259843387.972:42): operation="open" pid=1915 parent=1914 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.063058] type=1503 audit(1259843389.042:43): operation="open" pid=1925 parent=1924 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.086758] type=1503 audit(1259843389.062:44): operation="open" pid=1934 parent=1933 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

---

### Post by yeats on 2009-12-03
Could this be a swap problem?  Can you post the output of

```
sudo fdisk -l
```

?

---

### Post by garage jack on 2009-12-03
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00bb00bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3682    29575633+   7  HPFS/NTFS
/dev/sda2            3683        9963    50452132+   f  W95 Ext'd (LBA)
/dev/sda5            3683        9963    50452101    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x608e9b20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       19457   125572072+   f  W95 Ext'd (LBA)
/dev/sdb5            3825        3946      979933+  82  Linux swap / Solaris
/dev/sdb6            3947        6378    19535008+  83  Linux
/dev/sdb7            6379       19457   105057036    7  HPFS/NTFS

---

### Post by yeats on 2009-12-03
```
/dev/sdb5 3825 3946 979933+ 82 Linux swap / Solaris
```

According to this converter: [http://www.unitconversion.org/data-storage/blocks-to-gigabytes-conversion.html](http://www.unitconversion.org/data-storage/blocks-to-gigabytes-conversion.html) , 979933 blocks amounts to less than half of 1 GB.  The recommended amount for swap is 2X RAM.  This *could* be the issue.

Could you do one of the activities that tends to cause this problem for you and run top in a terminal while it's happening?:

```
top
```

---

### Post by garage jack on 2009-12-03
miroslav@garagejack:~$ top

top - 18:57:12 up  5:27,  3 users,  load average: 2.02, 0.83, 0.44
Tasks: 128 total,   3 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s): 47.2%us,  8.3%sy,  0.0%ni, 33.2%id,  0.0%wa,  0.7%hi, 10.6%si,  0.0%st
Mem:   1539748k total,  1521524k used,    18224k free,   181048k buffers
Swap:   979924k total,     4508k used,   975416k free,   243092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3052 miroslav  20   0  362m 160m  18m R 19.3 10.7  33:01.46 npviewer.bin       
 3973 miroslav  20   0  660m  61m  22m S 16.0  4.1   0:18.99 totem              
 1310 root      20   0  225m  80m  18m R 10.0  5.4  13:45.78 Xorg               
 1899 miroslav  20   0  376m 119m  16m S  6.3  7.9   7:59.80 compiz.real        
 1808 miroslav  20   0  329m 6968 5228 S  6.0  0.5   6:38.28 pulseaudio         
 2984 miroslav  20   0  747m 221m  28m S  6.0 14.7  18:30.53 firefox            
 3943 miroslav  20   0  218m  15m  10m S  2.7  1.0   0:01.11 gnome-terminal     
 1714 root      20   0 22180 1240 1040 S  0.3  0.1   0:05.61 hald-addon-stor    
 4031 miroslav  20   0 19132 1324  980 R  0.3  0.1   0:00.05 top                
    1 root      20   0 19456 1556 1188 S  0.0  0.1   0:00.65 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            

oh, man, don't tell me the only solution is to reinstall ubuntu? :-D

---

### Post by yeats on 2009-12-03
> oh, man, don't tell me the only solution is to reinstall ubuntu? 

Nah, but you might consider disabling compiz (System -> Preferences -> Appearance -> Visual Effects), which may be fighting with your other programs for memory...  Also, I see that you're running totem and a flash program (npviewer.bin) at the same time.  Since you only have 1.5 G of memory and it's nearly full, that's probably explaining your problem.  Try doing fewer things at once.

---

### Post by garage jack on 2009-12-03
don't worry, i don't usually run two programs at the same time, i was just trying to provoke that problem too show you, but, you are right, i should cut on effects. and thanks for your time and advises.

---

### Post by kansasnoob on 2009-12-03
To me /usr looks heavy compared to /home so I'd first run:

```
sudo apt-get autoclean && sudo apt-get clean
```

And:

```
sudo apt-get -f install
```

Which may ask you to run autoremove, etc.

---

### Post by garage jack on 2009-12-04
> To me /usr looks heavy compared to /home so I'd first run:
sudo apt-get autoclean && sudo apt-get clean gave me 2 gb free space, how is this possible? stupid question, i know. still trying to figure out how ubuntu works.

---

