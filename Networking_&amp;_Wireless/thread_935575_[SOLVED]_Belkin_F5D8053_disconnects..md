---
title: "[SOLVED] Belkin F5D8053 disconnects."
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by timstone on 2008-10-01
I got my OS up and running on my main pc finally...network is working, except it just randomly drops connection and I can't establish connection again until I reboot. 

Any ideas on what it could be or anything to fix it?

---

### Post by timstone on 2008-10-01
ok seriously...wtf?  is it possibly ndiswrapper?  is there a better tool to do the job it does?   ive tried everything from chainging my routers channel, to changing the security encryption type, last time i rebooted it was working for all of 2 minutes, if that.....

---

### Post by Crafty Kisses on 2008-10-01
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages
```

I also want to see the results of this command:
```
lshw -C network
```

I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

---

### Post by Jackie999 on 2008-10-01
I have the v3 version of the USB wireless (mines F5D8053 v3 - with rt2870 chip) the newest ralink driver (version 1.4.0.0) seems to be more stable than earlier ones.

Look here for how to set up the linux driver (if your chip is also the rt2870):
[http://ubuntuforums.org/showthread.php?t=919044](http://ubuntuforums.org/showthread.php?t=919044)
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473"]
[/URL]

---

### Post by timstone on 2008-10-01
Didn't know what parts you wanted to see so I copy/pasted all of it...

```

tim@tim-desktop:~$ sudo ifdown wlan0
[sudo] password for tim: 
ifdown: interface wlan0 not configured
tim@tim-desktop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
tim@tim-desktop:~$ 

```

```

tim@tim-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:44:28:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55900 (54.5 KB)  TX bytes:55900 (54.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:c4:89:29  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fec4:8929/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:775780 (757.5 KB)  TX bytes:125454 (122.5 KB)

```

```

tim@tim-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"TS_2282"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:20:73:1D   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

mode... Ok.
[   13.867364] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.867462] hpet clockevent registered
[   13.947329] Calibrating delay using timer specific routine.. 5591.32 BogoMIPS (lpj=11182649)
[   13.947353] Security Framework initialized
[   13.947359] SELinux:  Disabled at boot.
[   13.947374] AppArmor: AppArmor initialized
[   13.947378] Failure registering capabilities with primary security module.
[   13.947387] Mount-cache hash table entries: 512
[   13.947515] Initializing cgroup subsys ns
[   13.947520] Initializing cgroup subsys cpuacct
[   13.947533] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000 00000000
[   13.947543] monitor/mwait feature present.
[   13.947545] using mwait in idle threads.
[   13.947550] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   13.947553] CPU: L2 cache: 1024K
[   13.947555] CPU: Physical Processor ID: 0
[   13.947558] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   13.947569] Compat vDSO mapped to ffffe000.
[   13.947585] Checking 'hlt' instruction... OK.
[   13.963756] SMP alternatives: switching to UP code
[   13.965580] Freeing SMP alternatives: 11k freed
[   13.965703] Early unpacking initramfs... done
[   14.279645] ACPI: Core revision 20070126
[   14.295783] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.326613] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[   14.326654] Total of 1 processors activated (5591.32 BogoMIPS).
[   14.326810] ENABLING IO-APIC IRQs
[   14.326983] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.474466] Brought up 1 CPUs
[   14.474490] CPU0 attaching sched-domain:
[   14.474493]  domain 0: span 01
[   14.474496]   groups: 01
[   14.474678] net_namespace: 64 bytes
[   14.474691] Booting paravirtualized kernel on bare hardware
[   14.475324] Time:  1:37:18  Date: 10/02/08
[   14.475348] NET: Registered protocol family 16
[   14.475612] EISA bus registered
[   14.475619] ACPI: bus type pci registered
[   14.475771] PCI: PCI BIOS revision 2.10 entry at 0xfb2c2, last bus=3
[   14.475773] PCI: Using configuration type 1
[   14.475797] Setting up standard PCI resources
[   14.477527] ACPI: EC: Look up EC in DSDT
[   14.501509] ACPI: Interpreter enabled
[   14.501513] ACPI: (supports S0 S1 S3 S4 S5)
[   14.501532] ACPI: Using IOAPIC for interrupt routing
[   14.535250] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.535828] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   14.535832] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[   14.536348] PCI: Transparent bridge - 0000:00:1e.0
[   14.536378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.536848] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   14.537406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   14.537690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[   14.803041] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   14.803376] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   14.803709] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   14.804040] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   14.804373] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   14.804706] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   14.805041] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   14.805372] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[   14.805619] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.805659] pnp: PnP ACPI init
[   14.805667] ACPI: bus type pnp registered
[   14.827997] pnpacpi: exceeded the max number of IO resources: 40 
[   14.828202] pnp: PnP ACPI: found 11 devices
[   14.828204] ACPI: ACPI bus type pnp unregistered
[   14.828209] PnPBIOS: Disabled by ACPI PNP
[   14.828494] PCI: Using ACPI for IRQ routing
[   14.828497] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.849774] NET: Registered protocol family 8
[   14.849777] NET: Registered protocol family 20
[   14.849817] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.849822] hpet0: 3 64-bit timers, 14318180 Hz
[   14.850859] AppArmor: AppArmor Filesystem Enabled
[   14.853759] Time: tsc clocksource has been installed.
[   14.853774] Switched to high resolution mode on CPU 0
[   14.861742] system 00:01: ioport range 0x800-0x85f has been reserved
[   14.861746] system 00:01: ioport range 0xc00-0xc7f has been reserved
[   14.861748] system 00:01: ioport range 0x860-0x8ff could not be reserved
[   14.861760] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[   14.861763] system 00:08: iomem range 0x100000-0xffffff could not be reserved
[   14.861766] system 00:08: iomem range 0x1000000-0x3fe88bff could not be reserved
[   14.861769] system 00:08: iomem range 0xc0000-0xfffff could not be reserved
[   14.861772] system 00:08: iomem range 0xfec00000-0xfecfffff could not be reserved
[   14.861775] system 00:08: iomem range 0xfee00000-0xfeefffff could not be reserved
[   14.861777] system 00:08: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   14.861780] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   14.861783] system 00:08: iomem range 0xffc00000-0xffffffff could not be reserved
[   14.861789] system 00:09: ioport range 0x100-0x1fe could not be reserved
[   14.861791] system 00:09: ioport range 0x200-0x277 has been reserved
[   14.861794] system 00:09: ioport range 0x280-0x2e7 has been reserved
[   14.861796] system 00:09: ioport range 0x2e8-0x2ef has been reserved
[   14.861799] system 00:09: ioport range 0x2f0-0x2f7 has been reserved
[   14.861801] system 00:09: ioport range 0x2f8-0x2ff has been reserved
[   14.861804] system 00:09: ioport range 0x300-0x377 could not be reserved
[   14.861806] system 00:09: ioport range 0x380-0x3bb has been reserved
[   14.861809] system 00:09: ioport range 0x3c0-0x3e7 could not be reserved
[   14.861812] system 00:09: ioport range 0x3f6-0x3f7 could not be reserved
[   14.861814] system 00:09: ioport range 0x400-0x4cf has been reserved
[   14.861817] system 00:09: ioport range 0x4d2-0x57f has been reserved
[   14.861819] system 00:09: ioport range 0x580-0x677 has been reserved
[   14.861822] system 00:09: ioport range 0x680-0x777 has been reserved
[   14.861824] system 00:09: ioport range 0x780-0x7bb has been reserved
[   14.861827] system 00:09: ioport range 0x7c0-0x7ff has been reserved
[   14.861829] system 00:09: ioport range 0x8e0-0x8ff has been reserved
[   14.861833] system 00:09: ioport range 0x900-0x9fe has been reserved
[   14.861836] system 00:09: ioport range 0xa00-0xafe has been reserved
[   14.861838] system 00:09: ioport range 0xb00-0xbfe has been reserved
[   14.861841] system 00:09: ioport range 0xc80-0xcaf has been reserved
[   14.861843] system 00:09: ioport range 0xcb0-0xcbf has been reserved
[   14.861845] system 00:09: ioport range 0xcc0-0xcf7 has been reserved
[   14.861848] system 00:09: ioport range 0xd00-0xdfe has been reserved
[   14.861850] system 00:09: ioport range 0xe00-0xefe has been reserved
[   14.861853] system 00:09: ioport range 0xf00-0xffe has been reserved
[   14.861855] system 00:09: ioport range 0x2000-0x20fe has been reserved
[   14.861858] system 00:09: ioport range 0x2100-0x21fe has been reserved
[   14.861860] system 00:09: ioport range 0x2200-0x22fe has been reserved
[   14.861863] system 00:09: ioport range 0x2300-0x23fe has been reserved
[   14.861865] system 00:09: ioport range 0x2400-0x24fe has been reserved
[   14.861868] system 00:09: ioport range 0x2500-0x25fe has been reserved
[   14.861870] system 00:09: ioport range 0x2600-0x26fe has been reserved
[   14.861873] system 00:09: ioport range 0x2700-0x27fe has been reserved
[   14.861875] system 00:09: ioport range 0x2800-0x28fe has been reserved
[   14.861878] system 00:09: ioport range 0x2900-0x29fe has been reserved
[   14.861880] system 00:09: ioport range 0x2a00-0x2afe has been reserved
[   14.861883] system 00:09: ioport range 0x2b00-0x2bfe has been reserved
[   14.861885] system 00:09: ioport range 0x2c00-0x2cfe has been reserved
[   14.861888] system 00:09: ioport range 0x2d00-0x2dfe has been reserved
[   14.861891] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[   14.861893] system 00:09: iomem range 0xfeda0000-0xfedacfff has been reserved
[   14.892370] PCI: Bridge: 0000:00:01.0
[   14.892373]   IO window: d000-dfff
[   14.892378]   MEM window: dd000000-dfefffff
[   14.892381]   PREFETCH window: c0000000-cfffffff
[   14.892385] PCI: Bridge: 0000:00:1c.0
[   14.892386]   IO window: disabled.
[   14.892391]   MEM window: dcf00000-dcffffff
[   14.892395]   PREFETCH window: disabled.
[   14.892400] PCI: Bridge: 0000:00:1e.0
[   14.892402]   IO window: c000-cfff
[   14.892407]   MEM window: dce00000-dcefffff
[   14.892411]   PREFETCH window: disabled.
[   14.892431] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.892437] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.892455] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.892461] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.892472] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.892483] NET: Registered protocol family 2
[   14.929655] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.929967] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.930589] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.930896] TCP: Hash tables configured (established 131072 bind 65536)
[   14.930898] TCP reno registered
[   14.941728] checking if image is initramfs... it is
[   15.555242] Freeing initrd memory: 7314k freed
[   15.555396] Simple Boot Flag at 0x7a set to 0x1
[   15.555871] audit: initializing netlink socket (disabled)
[   15.555885] audit(1222911438.580:1): initialized
[   15.556059] highmem bounce pool size: 64 pages
[   15.558321] VFS: Disk quotas dquot_6.5.1
[   15.558405] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.558549] io scheduler noop registered
[   15.558552] io scheduler anticipatory registered
[   15.558553] io scheduler deadline registered
[   15.558566] io scheduler cfq registered (default)
[   15.558661] Boot video device is 0000:01:00.0
[   15.558667] PCI: Firmware left 0000:03:08.0 e100 interrupts enabled, disabling
[   15.558782] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.558823] assign_interrupt_mode Found MSI capability
[   15.558858] Allocate Port Service[0000:00:01.0:pcie00]
[   15.558949] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.558993] assign_interrupt_mode Found MSI capability
[   15.559028] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.559075] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.559360] isapnp: Scanning for PnP cards...
[   15.910760] isapnp: No Plug & Play device found
[   15.947644] Real Time Clock Driver v1.12ac
[   15.947877] hpet_resources: 0xfed00000 is busy
[   15.947893] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.949321] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.949401] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.949516] PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[   15.949519] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   15.949911] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.952064] mice: PS/2 mouse device common for all mice
[   15.952207] EISA: Probing bus 0 at eisa.0
[   15.952211] EISA: Cannot allocate resource for mainboard
[   15.952218] Cannot allocate resource for EISA slot 2
[   15.952239] EISA: Detected 0 cards.
[   15.952242] cpuidle: using governor ladder
[   15.952244] cpuidle: using governor menu
[   15.952323] NET: Registered protocol family 1
[   15.952353] Using IPI No-Shortcut mode
[   15.952382] registered taskstats version 1
[   15.952473]   Magic number: 12:855:608
[   15.952529]   hash matches device ptyaf
[   15.952588] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.952590] EDD information not available.
[   15.952782] Freeing unused kernel memory: 368k freed
[   15.991775] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.181904] fuse init (API version 7.9)
[   17.203632] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.688877] usbcore: registered new interface driver usbfs
[   17.688905] usbcore: registered new interface driver hub
[   17.701124] usbcore: registered new device driver usb
[   17.716785] USB Universal Host Controller Interface driver v3.0
[   17.716850] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 17
[   17.716864] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.716868] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.717071] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.717101] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
[   17.717240] usb usb1: configuration #1 chosen from 1 choice
[   17.717267] hub 1-0:1.0: USB hub found
[   17.717275] hub 1-0:1.0: 2 ports detected
[   17.796624] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   17.796629] e100: Copyright(c) 1999-2006 Intel Corporation
[   17.820667] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 18
[   17.820682] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.820687] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.820713] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.820742] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   17.820859] usb usb2: configuration #1 chosen from 1 choice
[   17.820887] hub 2-0:1.0: USB hub found
[   17.820894] hub 2-0:1.0: 2 ports detected
[   17.834676] SCSI subsystem initialized
[   17.875726] libata version 3.00 loaded.
[   17.924480] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   17.924496] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.924500] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.924530] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.924559] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
[   17.924677] usb usb3: configuration #1 chosen from 1 choice
[   17.924706] hub 3-0:1.0: USB hub found
[   17.924713] hub 3-0:1.0: 2 ports detected
[   18.028380] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 20
[   18.028395] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   18.028399] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   18.028427] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   18.028456] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000ff20
[   18.028574] usb usb4: configuration #1 chosen from 1 choice
[   18.028601] hub 4-0:1.0: USB hub found
[   18.028608] hub 4-0:1.0: 2 ports detected
[   18.060143] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   18.132216] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 17
[   18.132232] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.132237] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.132264] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   18.136160] ehci_hcd 0000:00:1d.7: debug port 1
[   18.136166] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   18.136173] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xffa80800
[   18.187990] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.188116] usb usb5: configuration #1 chosen from 1 choice
[   18.188146] hub 5-0:1.0: USB hub found
[   18.188154] hub 5-0:1.0: 8 ports detected
[   18.291933] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   18.313741] e100: eth0: e100_probe: addr 0xdceff000, irq 21, MAC addr 00:13:20:44:28:97
[   18.318545] ata_piix 0000:00:1f.1: version 2.12
[   18.318563] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   18.318601] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.321526] scsi0 : ata_piix
[   18.322550] scsi1 : ata_piix
[   18.322593] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   18.322596] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   18.583248] usb 1-1: device not accepting address 2, error -71
[   18.648317] ata1.00: ATA-5: WDC WD300BB-32CLB0, 05.04E05, max UDMA/100
[   18.648321] ata1.00: 58633344 sectors, multi 8: LBA 
[   18.648350] ata1.01: ATAPI: HL-DT-STDVD-ROM GDR8163B, 0D20, max UDMA/33
[   18.664253] ata1.00: configured for UDMA/100
[   18.835042] ata1.01: configured for UDMA/33
[   18.835087] ata2: port disabled. ignoring.
[   18.835220] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300BB-32CL 05.0 PQ: 0 ANSI: 5
[   18.839195] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8163B 0D20 PQ: 0 ANSI: 5
[   18.839262] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   18.994512] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 21
[   18.994553] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.994598] scsi2 : ata_piix
[   18.994812] scsi3 : ata_piix
[   18.994845] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 21
[   18.994848] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 21
[   19.158512] ata3.00: ATA-6: WDC WD800JD-75JNC0, 06.01C06, max UDMA/100
[   19.158516] ata3.00: 156250000 sectors, multi 8: LBA 
[   19.166508] ata3.00: configured for UDMA/100
[   19.190154] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   19.341480] usb 5-5: configuration #1 chosen from 1 choice
[   19.581469] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   19.763712] usb 1-1: configuration #1 chosen from 1 choice
[   19.781529] usbcore: registered new interface driver hiddev
[   19.795777] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   19.805113] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-1
[   19.805130] usbcore: registered new interface driver usbhid
[   19.805134] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.992908] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800JD-75JN 06.0 PQ: 0 ANSI: 5
[   20.008282] Driver 'sd' needs updating - please use bus_type methods
[   20.008377] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
[   20.008394] sd 0:0:0:0: [sda] Write Protect is off
[   20.008397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.008422] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.008475] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
[   20.008489] sd 0:0:0:0: [sda] Write Protect is off
[   20.008491] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.008514] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.008519]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   20.166287]  sda1 sda2 < sda5 >
[   20.185151] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.185939] sd 2:0:0:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   20.185956] sd 2:0:0:0: [sdb] Write Protect is off
[   20.185960] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   20.185984] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.186034] sd 2:0:0:0: [sdb] 156250000 512-byte hardware sectors (80000 MB)
[   20.186204] sd 2:0:0:0: [sdb] Write Protect is off
[   20.186208] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   20.186236] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.186240]  sdb:sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   20.196288] Uniform CD-ROM driver Revision: 3.20
[   20.196340] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   20.214969]  sdb1 sdb2 < sdb5 >
[   20.241947] sd 2:0:0:0: [sdb] Attached SCSI disk
[   20.250441] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.250466] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   20.250487] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   20.616812] Attempting manual resume
[   20.616817] swsusp: Resume From Partition 8:21
[   20.616819] PM: Checking swsusp image.
[   20.616991] PM: Resume from disk failed.
[   20.661079] kjournald starting.  Commit interval 5 seconds
[   20.661093] EXT3-fs: mounted filesystem with ordered data mode.
[   27.998836] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   28.158474] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   28.242666] Linux agpgart interface v0.102
[   28.282274] intel_rng: Firmware space is locked read-only. If you can't or
[   28.282277] intel_rng: don't want to disable this in firmware setup, and if
[   28.282279] intel_rng: you are certain that your system has a functional
[   28.282280] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   28.390100] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.442434] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.573831] parport_pc 00:07: reported by Plug and Play ACPI
[   28.573890] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   28.733483] iTCO_vendor_support: vendor-support=0
[   28.785594] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.785686] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   28.785720] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.822569] input: Power Button (FF) as /devices/virtual/input/input4
[   28.849630] ACPI: Power Button (FF) [PWRF]
[   28.849692] input: Power Button (CM) as /devices/virtual/input/input5
[   28.877233] ACPI: Power Button (CM) [VBTN]
[   29.667907] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 23 (level, low) -> IRQ 20
[   29.667933] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   30.087084] intel8x0_measure_ac97_clock: measured 52422 usecs
[   30.087089] intel8x0: clocking to 48000
[   30.191847] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   30.446475] usb 5-5: reset high speed USB device using ehci_hcd and address 3
[   30.634600] ndiswrapper: driver rt2870 (Ralink Technology, Corp.,04/12/2007, 1.00.01.0000) loaded
[   30.969895] wlan0: ethernet device 00:17:3f:c4:89:29 using NDIS driver: rt2870, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 050D:8053.F.conf
[   30.970764] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.970799] usbcore: registered new interface driver ndiswrapper
[   31.772960] lp0: using parport0 (interrupt-driven).
[   31.824300] Adding 3028212k swap on /dev/sdb5.  Priority:-1 extents:1 across:3028212k
[   32.372744] EXT3 FS on sdb1, internal journal
[   33.557308] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.933324] No dock devices found.
[   35.376637] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   35.376643] apm: overridden by ACPI.
[   35.508198] ppdev: user-space parallel port driver
[   35.713648] audit(1222911459.063:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4861 profile="/usr/sbin/cupsd" namespace="default"
[   39.094615] Bluetooth: Core ver 2.11
[   39.095194] NET: Registered protocol family 31
[   39.095199] Bluetooth: HCI device and connection manager initialized
[   39.095203] Bluetooth: HCI socket layer initialized
[   39.129327] Bluetooth: L2CAP ver 2.9
[   39.129333] Bluetooth: L2CAP socket layer initialized
[   39.220272] Bluetooth: RFCOMM socket layer initialized
[   39.220286] Bluetooth: RFCOMM TTY layer initialized
[   39.220289] Bluetooth: RFCOMM ver 1.8
[   52.634330] NET: Registered protocol family 10
[   52.634807] lo: Disabled Privacy Extensions
[   52.635584] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.636116] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.744385] NET: Registered protocol family 17
[   63.272259] UDF-fs: No VRS found
[   63.282006] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.408140] ISO 9660 Extensions: RRIP_1991A
[   65.806147] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   83.349824] wlan0: no IPv6 routers present
[  328.103187] BUG: unable to handle kernel paging request at virtual address f8cb2004
[  328.103195] printing eip: f8b112e1 *pde = 1fa35067 *pte = 00000000 
[  328.103202] Oops: 0000 [#1] SMP 
[  328.103206] Modules linked in: af_packet isofs udf ipv6 rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_userspace cpufreq_stats cpufreq_conservative cpufreq_ondemand freq_table video output sbs sbshc container dock battery iptable_filter ip_tables x_tables ac lp ndiswrapper i2c_core snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button iTCO_wdt iTCO_vendor_support intel_agp parport_pc parport shpchp pci_hotplug evdev agpgart snd dcdbas soundcore snd_page_alloc pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi usbhid hid ata_piix ata_generic libata scsi_mod e100 mii ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  328.103260] 
[  328.103263] Pid: 3136, comm: ntos_wq Tainted: P        (2.6.24-19-generic #1)
[  328.103266] EIP: 0060:[<f8b112e1>] EFLAGS: 00010246 CPU: 0
[  328.103272] EIP is at 0xf8b112e1
[  328.103275] EAX: f8cb1ff4 EBX: f1632780 ECX: 00000000 EDX: f8cb1ff4
[  328.103277] ESI: f1632838 EDI: f8b44b90 EBP: dfb5bf10 ESP: dfb5be28
[  328.103280]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  328.103283] Process ntos_wq (pid: 3136, ti=dfb5a000 task=dfba9700 task.ti=dfb5a000)
[  328.103285] Stack: f8b44b90 f1632838 df838bb0 00000000 00006000 00000003 00006000 f7c8bc4c 
[  328.103292]        00000000 c01091d3 00000000 dfb04c40 f7c8bc4c dfb04c00 dfb6f0c0 dfa91bc0 
[  328.103298]        f1632780 f8ae22b1 00000000 c1808b9c 00000002 f1632780 c0408380 dfb04c00 
[  328.103305] Call Trace:
[  328.103325]  [<c01091d3>] dma_alloc_coherent+0xc3/0x110
[  328.103349]  [<f8ae22b1>] wrap_alloc_urb+0x1d1/0x2d0 [ndiswrapper]
[  328.103386]  [<f8ae241a>] wrap_submit_urb+0x6a/0xa0 [ndiswrapper]
[  328.103415]  [<f8ae282d>] wrap_submit_irp+0x2cd/0xb40 [ndiswrapper]
[  328.103476]  [<f8ade815>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[  328.103532]  [<f8adefbe>] IofCompleteRequest+0x3e/0x180 [ndiswrapper]
[  328.103570]  [<f8ae30f0>] wrap_urb_complete_worker+0x50/0x130 [ndiswrapper]
[  328.103598]  [<f8ae30a0>] wrap_urb_complete_worker+0x0/0x130 [ndiswrapper]
[  328.103617]  [<c013ce8f>] run_workqueue+0xbf/0x160
[  328.103636]  [<c013d930>] worker_thread+0x0/0xe0
[  328.103644]  [<c013d9b4>] worker_thread+0x84/0xe0
[  328.103653]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[  328.103665]  [<c013d930>] worker_thread+0x0/0xe0
[  328.103672]  [<c0140982>] kthread+0x42/0x70
[  328.103676]  [<c0140940>] kthread+0x0/0x70
[  328.103683]  [<c0105677>] kernel_thread_helper+0x7/0x10
[  328.103700]  =======================
[  328.103701] Code: dc 8b 4d d0 8b 11 c1 ea 10 81 e2 ff 0f 00 00 66 89 55 d8 8b 45 d0 8b 48 04 c1 e9 1e 83 e1 03 83 e1 02 74 04 c6 45 bf 01 8b 55 e0 <0f> b6 42 10 83 f8 40 74 58 8b 4d e0 0f b6 51 10 83 fa 50 74 4c 
[  328.103737] EIP: [<f8b112e1>] 0xf8b112e1 SS:ESP 0068:dfb5be28
[  328.103744] ---[ end trace 48b0afbc9ab89c82 ]---
tim@tim-desktop:~$ 

```

```

tim@tim-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:44:28:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:c4:89:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Ralink Technology, Corp.,04 ip=192.168.2.3 multicast=yes wireless=IEEE 802.11g

```

---

