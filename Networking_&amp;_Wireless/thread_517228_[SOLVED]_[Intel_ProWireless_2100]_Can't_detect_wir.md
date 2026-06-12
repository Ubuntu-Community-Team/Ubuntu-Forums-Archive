---
title: "[SOLVED] [Intel Pro/Wireless 2100] Can't detect wireless network"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by dpro on 2007-08-04
The topic pretty much explains the problem. My wireless network card can't detect the wireless network.

I'm running Feisty, and here are some info:
lshw:
```

*-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 6
                bus info: pci@02:06.0
                logical name: eth1
                version: 04
                serial: 00:04:23:51:cd:11
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
                resources: iomemory:e0203000-e0203fff irq:10
```

lspci
```
02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:04:23:51:CD:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x6000 Memory:e0203000-e0203fff 

```

iwconfig
```
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```
eth1      No scan results
```

sudo dhclient eth1
```
There is already a pid file /var/run/dhclient.pid with pid 5439
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:04:23:51:cd:11
Sending on   LPF/eth1/00:04:23:51:cd:11
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


I've seen people referring to ipw2100.sourceforge.net, but before I'm being sent over there too, I've got two comments:
1: It already says I've got the ipw2100 1.2.2 driver installed (?)
2: As the newbie that I am, I wouldn't know how to install everything that the site suggests that I install.

Also, I don't know if this has got anything to do with anything, but when I run:
"sudo iwconfig eth1 channel 11" (my router is set to run at 11) I get this:
```
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.
```

Any suggestions anyone?

Let me know if I need to provide further information to enable you to help me :P

Thanks,

-d

---

### Post by TBerben on 2007-08-04
Open the network manager, select "connect to other wireless network". Then enter the ESSID (the "name") of your network and if necessary the encryption type and key. ESSID broadcast might be disabled in your router settings, hence ubuntu doesn't detect the network.

---

### Post by dpro on 2007-08-04
Thanks for your reply, but SSID broadcast is enabled, and the procedure you mentioned doesn't help.

---

### Post by dpro on 2007-08-06
Also; I've tried ndiswrapper, but that didn't do much good either.

I don't know if I need to update the firmware? Can you see out of the info I've posted if the firmware is out of date, cause I can't :P (I have downloaded it, but I don't know how to install it)

Again, thanks for any help:)

-d

---

### Post by noob12 on 2007-08-06
This is the first time I've seen the 2100.

Your radio sure looks off.  If there's a hardware switch can you make sure it is on.  Also, if there are BIOS settings, can you make sure they are enabled by default?

Also can you post **cat /sys/class/net/*/device/rf_kill** (which may not match anything but if it does is interesting).

Post **cat /etc/network/interfaces** and your entire **dmesg** while you're at it.

---

### Post by noob12 on 2007-08-07
Firmware and driver version that is shown in your lshw is the most recent stable for the 2100 from [http://ipw2100.sourceforge.net/index.php](http://ipw2100.sourceforge.net/index.php).

Let me know if you want more diagnostic help.

---

### Post by dpro on 2007-08-07
I'd like all the help I can get :P

The wireless settings is enabled by default in the BIOS.
Might very well be that the radio is off. I do have a hardware swith, although it's not one of
those Fn+F2 thingies, it's a launchpad which really doesn't seem to be enabled. At least, when I press the buttons on the launchpad nothing happens. I've heard about some launchpad bug, but I haven't really come across any info wether that is my case or not.

Anyway, here's the info you requested:

cat /sys/class/net/*/device/rf_kill:
```
2
```

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
```

Hmm.. eth1 (my wireless network card) isn't in here. Is that weird? :P

dmesg:
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ce000 size: 0000000000002000 end: 00000000000d0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f5e0000 end: 000000001f6e0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f6e0000 size: 000000000000b000 end: 000000001f6eb000 type: 3
[    0.000000] copy_e820_map() start: 000000001f6eb000 size: 0000000000015000 end: 000000001f700000 type: 4
[    0.000000] copy_e820_map() start: 000000001f700000 size: 0000000000900000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec10000 size: 0000000000010000 end: 00000000fec20000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffffc00 size: 0000000000000400 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6130
[    0.000000] ACPI: RSDT (v001 PTLTD  Montara  0x06040000  LTP 0x00000000) @ 0x1f6e658e
[    0.000000] ACPI: FADT (v001 INTEL  MONTARAG 0x06040000 PTL  0x00000050) @ 0x1f6eaed2
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f6eafd8
[    0.000000] ACPI: SSDT (v001 INTEL    GV3Ref 0x00001001 MSFT 0x0100000e) @ 0x1f6e65be
[    0.000000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Detected 1399.846 MHz processor.
[    5.742433] Built 1 zonelists.  Total pages: 127731
[    5.742438] Kernel command line: root=UUID=f0875865-5370-4e0f-b32b-b314640a6dd3 ro quiet splash
[    5.742653] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    5.742662] mapped APIC to ffffd000 (013fa000)
[    5.742666] Enabling fast FPU save and restore... done.
[    5.742669] Enabling unmasked SIMD FPU exception support... done.
[    5.742679] Initializing CPU#0
[    5.742756] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    5.744383] Console: colour VGA+ 80x25
[    5.744593] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    5.744858] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    5.761604] Memory: 499512k/514944k available (1992k kernel code, 14912k reserved, 900k data, 328k init, 0k highmem)
[    5.761618] virtual kernel memory layout:
[    5.761620]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    5.761622]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    5.761623]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    5.761625]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    5.761627]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    5.761628]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    5.761630]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    5.761634] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    5.838700] Calibrating delay using timer specific routine.. 2801.69 BogoMIPS (lpj=5603396)
[    5.838755] Security Framework v1.0.0 initialized
[    5.838763] SELinux:  Disabled at boot.
[    5.838786] Mount-cache hash table entries: 512
[    5.838954] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    5.838968] CPU: L1 I cache: 32K, L1 D cache: 32K
[    5.838971] CPU: L2 cache: 1024K
[    5.838974] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    5.838986] Compat vDSO mapped to ffffe000.
[    5.838991] Remapping vsyscall page to ffffe000
[    5.839003] Checking 'hlt' instruction... OK.
[    5.854789] SMP alternatives: switching to UP code
[    5.854973] Freeing SMP alternatives: 11k freed
[    5.855182] Early unpacking initramfs... done
[    6.258270] ACPI: Core revision 20060707
[    6.259120] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    6.261409] ACPI: setting ELCR to 0200 (from 0c00)
[    6.270496] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
[    6.270503] SMP motherboard not detected.
[    6.270506] Local APIC not detected. Using dummy APIC emulation.
[    6.270547] Brought up 1 CPUs
[    6.270839] Booting paravirtualized kernel on bare hardware
[    6.270913] Time: 10:14:20  Date: 07/07/107
[    6.270952] NET: Registered protocol family 16
[    6.271054] EISA bus registered
[    6.271059] ACPI: bus type pci registered
[    6.272287] PCI: PCI BIOS revision 2.10 entry at 0xfd6c4, last bus=3
[    6.272290] PCI: Using configuration type 1
[    6.272292] Setting up standard PCI resources
[    6.284100] ACPI: Interpreter enabled
[    6.284103] ACPI: Using PIC for interrupt routing
[    6.284806] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    6.284814] PCI: Probing PCI hardware (bus 00)
[    6.285817] Boot video device is 0000:00:02.0
[    6.286120] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    6.286125] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    6.286518] PCI: Transparent bridge - 0000:00:1e.0
[    6.286577] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    6.286581] Please report the result to linux-kernel to fix this permanently
[    6.286597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    6.292111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    6.292944] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    6.293188] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    6.293426] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    6.293668] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    6.293907] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    6.294147] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    6.294387] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[    6.294654] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    6.297590] Linux Plug and Play Support v0.97 (c) Adam Belay
[    6.297602] pnp: PnP ACPI init
[    6.498308] pnp: PnP ACPI: found 12 devices
[    6.498314] PnPBIOS: Disabled by ACPI PNP
[    6.498370] PCI: Using ACPI for IRQ routing
[    6.498373] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    6.504788] NET: Registered protocol family 8
[    6.504790] NET: Registered protocol family 20
[    6.504878] pnp: 00:04: ioport range 0x600-0x60f has been reserved
[    6.505178] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    6.505195] PCI: Bus 3, cardbus bridge: 0000:02:09.0
[    6.505199]   IO window: 00003000-000030ff
[    6.505203]   IO window: 00003400-000034ff
[    6.505208]   PREFETCH window: 30000000-33ffffff
[    6.505213]   MEM window: 38000000-3bffffff
[    6.505218] PCI: Bridge: 0000:00:1e.0
[    6.505221]   IO window: 3000-3fff
[    6.505227]   MEM window: e0200000-e02fffff
[    6.505232]   PREFETCH window: 30000000-35ffffff
[    6.505242] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    6.505251] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    6.505454] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    6.505458] PCI: setting IRQ 10 as level-triggered
[    6.505462] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[    6.505501] NET: Registered protocol family 2
[    6.538324] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    6.538422] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    6.538555] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    6.538628] TCP: Hash tables configured (established 16384 bind 8192)
[    6.538631] TCP reno registered
[    6.550388] checking if image is initramfs... it is
[    7.338414] Freeing initrd memory: 6778k freed
[    7.338702] Simple Boot Flag at 0x36 set to 0x1
[    7.338924] audit: initializing netlink socket (disabled)
[    7.338942] audit(1186481660.776:1): initialized
[    7.339107] VFS: Disk quotas dquot_6.5.1
[    7.339131] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.339197] io scheduler noop registered
[    7.339200] io scheduler anticipatory registered
[    7.339203] io scheduler deadline registered
[    7.339219] io scheduler cfq registered (default)
[    7.339689] isapnp: Scanning for PnP cards...
[    7.693300] isapnp: No Plug & Play device found
[    7.728459] Real Time Clock Driver v1.12ac
[    7.728530] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    7.728790] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    7.729833] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    7.729838] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    7.729849] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    7.729941] mice: PS/2 mouse device common for all mice
[    7.730564] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    7.730861] input: Macintosh mouse button emulation as /class/input/input0
[    7.730899] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    7.730904] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    7.731151] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    7.734406] i8042.c: Detected active multiplexing controller, rev 1.1.
[    7.735568] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.735574] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    7.735577] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    7.735580] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    7.735583] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    7.735731] EISA: Probing bus 0 at eisa.0
[    7.735740] Cannot allocate resource for EISA slot 1
[    7.735744] Cannot allocate resource for EISA slot 2
[    7.735747] Cannot allocate resource for EISA slot 3
[    7.735769] EISA: Detected 0 cards.
[    7.765868] TCP cubic registered
[    7.765878] NET: Registered protocol family 1
[    7.765906] Using IPI No-Shortcut mode
[    7.765979] ACPI: (supports S0 S3 S4 S5)
[    7.766031]   Magic number: 3:763:223
[    7.766076]   hash matches device ttyu7
[    7.766091]   hash matches device ttyra
[    7.766390] Freeing unused kernel memory: 328k freed
[    7.769461] Time: tsc clocksource has been installed.
[    7.781157] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.011905] Capability LSM initialized
[    9.052229] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    9.052237] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.324000] Time: acpi_pm clocksource has been installed.
[    3.524000] ACPI: Thermal Zone [THRS] (31 C)
[    3.740000] ACPI: Thermal Zone [THRC] (36 C)
[    4.152000] usbcore: registered new interface driver usbfs
[    4.152000] usbcore: registered new interface driver hub
[    4.152000] usbcore: registered new device driver usb
[    4.156000] USB Universal Host Controller Interface driver v3.0
[    4.156000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.156000] PCI: setting IRQ 11 as level-triggered
[    4.156000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.156000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.156000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.156000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.156000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    4.156000] usb usb1: configuration #1 chosen from 1 choice
[    4.156000] hub 1-0:1.0: USB hub found
[    4.156000] hub 1-0:1.0: 2 ports detected
[    4.260000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.260000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.260000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.260000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.260000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.260000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    4.260000] usb usb2: configuration #1 chosen from 1 choice
[    4.260000] hub 2-0:1.0: USB hub found
[    4.260000] hub 2-0:1.0: 2 ports detected
[    4.260000] ieee1394: Initialized config rom entry `ip1394'
[    4.364000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.364000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.364000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.364000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.364000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.364000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    4.364000] usb usb3: configuration #1 chosen from 1 choice
[    4.364000] hub 3-0:1.0: USB hub found
[    4.364000] hub 3-0:1.0: 2 ports detected
[    4.468000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    4.468000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    4.468000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.468000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.468000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.468000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.468000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.468000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    4.472000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.472000] usb usb4: configuration #1 chosen from 1 choice
[    4.472000] hub 4-0:1.0: USB hub found
[    4.472000] hub 4-0:1.0: 6 ports detected
[    4.588000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[    4.640000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.648000] b44.c:v1.01 (Jun 16, 2006)
[    4.648000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    4.648000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    4.652000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0a:e4:20:33:2b
[    4.664000] SCSI subsystem initialized
[    4.680000] libata version 2.20 loaded.
[    4.684000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.684000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.684000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.684000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.684000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.684000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.684000] scsi0 : ata_piix
[    5.240000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[    5.240000] ata1.00: ATA-7: SAMSUNG MP0804H, UE100-14, max UDMA/100
[    5.240000] ata1.00: 156368016 sectors, multi 16: LBA48 
[    5.248000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[    5.248000] ata1.00: configured for UDMA/100
[    5.248000] scsi1 : ata_piix
[    5.568000] ata2.00: ATAPI, max UDMA/33
[    5.732000] ata2.00: configured for UDMA/33
[    5.732000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0804H  UE10 PQ: 0 ANSI: 5
[    5.732000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UX10 PQ: 0 ANSI: 5
[    5.752000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[    5.752000] sda: Write Protect is off
[    5.752000] sda: Mode Sense: 00 3a 00 00
[    5.752000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.752000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[    5.752000] sda: Write Protect is off
[    5.752000] sda: Mode Sense: 00 3a 00 00
[    5.752000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.752000]  sda: sda1 sda2 sda3
[    5.788000] sd 0:0:0:0: Attached scsi disk sda
[    5.792000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.792000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.796000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.796000] Uniform CD-ROM driver Revision: 3.20
[    5.796000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.920000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[03e40a00b7002022]
[    6.068000] Attempting manual resume
[    6.068000] swsusp: Resume From Partition 8:2
[    6.068000] PM: Checking swsusp image.
[    6.068000] PM: Resume from disk failed.
[    6.120000] kjournald starting.  Commit interval 5 seconds
[    6.120000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.380000] NET: Registered protocol family 17
[   20.672000] iTCO_vendor_support: vendor-support=0
[   20.676000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.676000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.676000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.708000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.720000] agpgart: Detected an Intel 855 Chipset.
[   20.720000] agpgart: Detected 8060K stolen memory.
[   20.728000] agpgart: AGP aperture is 128M @ 0xe8000000
[   20.732000] intel_rng: FWH not detected
[   20.908000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.912000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.972000] ieee80211_crypt: registered algorithm 'NULL'
[   22.012000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   22.012000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.060000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   22.072000] Yenta: CardBus bridge found at 0000:02:09.0 [17c0:3003]
[   22.072000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   22.072000] Yenta: Routing CardBus interrupts to PCI
[   22.072000] Yenta TI: socket 0000:02:09.0, mfunc 0x01001002, devctl 0x64
[   22.104000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   22.116000] parport: PnPBIOS parport detected.
[   22.116000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   22.132000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   22.132000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   22.144000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   22.144000] b44: eth0: Flow control is off for TX and off for RX.
[   22.184000] irda_init()
[   22.184000] NET: Registered protocol family 23
[   22.200000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   22.200000] wbsd: Copyright(c) Pierre Ossman
[   22.216000] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   22.228000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   22.228000] nsc-ircc, chip->init
[   22.228000] nsc-ircc, Found chip at base=0x02e
[   22.228000] nsc-ircc, driver loaded (Dag Brattli)
[   22.228000] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.228000] nsc-ircc, Found chip at base=0x02e
[   22.228000] nsc-ircc, driver loaded (Dag Brattli)
[   22.228000] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.228000] pnp: Device 00:09 disabled.
[   22.304000] Yenta: ISA IRQ mask 0x0010, PCI irq 10
[   22.304000] Socket status: 30000007
[   22.304000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   22.304000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   22.304000] cs: IO port probe 0x3000-0x3fff: clean.
[   22.304000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   22.304000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   22.316000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   22.316000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   22.316000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   22.624000] eth1: Radio is disabled by RF switch.
[   22.768000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   22.768000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.888000] cs: IO port probe 0x100-0x3af: clean.
[   22.888000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.888000] cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   22.888000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.888000] cs: IO port probe 0xa00-0xaff: clean.
[   24.016000] intel8x0_measure_ac97_clock: measured 55391 usecs
[   24.016000] intel8x0: clocking to 48000
[   24.136000] fuse init (API version 7.8)
[   24.168000] lp0: using parport0 (interrupt-driven).
[   24.232000] Adding 498004k swap on /dev/disk/by-uuid/d1f8b227-c475-4973-b2df-17aec4022824.  Priority:-1 extents:1 across:498004k
[   24.396000] EXT3 FS on sda3, internal journal
[   24.600000] NET: Registered protocol family 10
[   24.600000] lo: Disabled Privacy Extensions
[   24.704000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.784000] NTFS volume version 3.1.
[   28.920000] ACPI: AC Adapter [AC] (on-line)
[   28.940000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.012000] No dock devices found.
[   29.032000] Using specific hotkey driver
[   29.192000] input: Power Button (FF) as /class/input/input3
[   29.196000] ACPI: Power Button (FF) [PWRF]
[   29.236000] input: Lid Switch as /class/input/input4
[   29.240000] ACPI: Lid Switch [LID]
[   29.284000] input: Sleep Button (CM) as /class/input/input5
[   29.288000] ACPI: Sleep Button (CM) [SLP2]
[   29.924000] ACPI: Battery Slot [BAT0] (battery present)
[   29.940000] ibm_acpi: ec object not found
[   29.980000] pcc_acpi: loading...
[   32.824000] ttyS1: LSR safety check engaged!
[   34.832000] eth0: no IPv6 routers present
[   35.648000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.796000] [drm] Initialized drm 1.1.0 20060810
[   36.804000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   36.804000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.808000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   37.616000] ppdev: user-space parallel port driver
[   38.560000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.560000] apm: overridden by ACPI.
[   38.728000] Bluetooth: Core ver 2.11
[   38.728000] NET: Registered protocol family 31
[   38.728000] Bluetooth: HCI device and connection manager initialized
[   38.728000] Bluetooth: HCI socket layer initialized
[   38.776000] Bluetooth: L2CAP ver 2.8
[   38.776000] Bluetooth: L2CAP socket layer initialized
[   39.008000] Bluetooth: RFCOMM socket layer initialized
[   39.008000] Bluetooth: RFCOMM TTY layer initialized
[   39.008000] Bluetooth: RFCOMM ver 1.8
```

Thanks for your help! :)

---

### Post by noob12 on 2007-08-07
You don't want your wireless card listed in /etc/network/interfaces.  You want eth1 left out as it is now. This will allow NetworkManager to manage it.

Your radio is off.

These two things both say the hardware kill switch is indeed enabled on the device.
> 
cat /sys/class/net/*/device/rf_kill
2


From your dmesg:
> 
[   22.624000] eth1: Radio is disabled by RF switch.


If we want to get wireless working you need to turn this switch on.  I am not sure what you mean by a launchpad.  Normally it is a slider on the side of the laptop or a FN key.

I don't think we can turn it on by software in this state, but I'll investigate.

---

### Post by noob12 on 2007-08-07
Can you let me know the make and model number of your laptop; include any version that is indicated on the label on the bottom.

---

### Post by dpro on 2007-08-07
If you look at the picture below, the five buttons on the left of the keyboard is what I referred to as the launchpad. Seems like those need to be installed somehow. I'll look around for some info on this.

[IMG]http://www.dinside.no/km_bilde/3/96503.jpg[/IMG]

---

### Post by noob12 on 2007-08-07
While we're here, I notice something weird about your eth0 set up in /etc/network/interfaces.  This is unrelated but may cause you different problems.  If you want eth0 configured dynamically, remove the address, netmask, and gateway lines.  If you did intend to configure it statically with these values, you need to change the word **dhcp** in the iface line to the word **static**.  This is nothing to do with your wireless, but you should fix it as well.

---

### Post by noob12 on 2007-08-07
Send me the make and model.  While you are booted in windows can you try turning on the wireless on the launchpad.  That state may persist across a reboot.

---

### Post by dpro on 2007-08-07
yeah. the eth0 thing you mentioned, was just me trying everything to get the wireless network to work:P hehe. Removed the input now, I want it dynamically.

Make and model might be a problem for you, as it is a Norwegian make (I think).
Anyhow, it's called Tundra 1555.

By the way, what I called launchpad earlier is actually a Launch Manager. I'm googling for installation info for this now.

---

### Post by noob12 on 2007-08-07
If you know what key or combination of keys works to turn on and off wireless in Windows, try using the same on Linux.  It might work but not really show any indication.  If you press the key(s) and the state shown by **cat /sys/class/net/*/device/rf_kill** changes to **0**, you successfully turned it on.

I'll look for info on the Tundra 1555 on the ipw2100 site.

---

### Post by noob12 on 2007-08-07
I believe you have a rebranded version of the AOpen 1555G: [http://solution.aopen.com.tw/products/nb/1555G.htm](http://solution.aopen.com.tw/products/nb/1555G.htm)

If we can confirm this, installing the acerhk module should allow you to turn on the device.

Followed this chain of refs

[http://ipw2100.sourceforge.net/index.php](http://ipw2100.sourceforge.net/index.php)
[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)
[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

Aopen 	1555G 	Software 	The acerhk module has support since version 0.5.13. Use module parameter poll=1 to support the RF switch key.
[http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/)

Signing off for the night.

[COLOR="Red"]UPDATE:[/COLOR]  Users with similar laptops should jump straight to [the solution posting #58 in this thread]("http://ubuntuforums.org/showpost.php?p=3217515&postcount=58").  Everything else is diagnostics, trial, and error.  That posting will get you the solution quickly and concisely.  I will be posting a separate HOWTO with essentially equivalent info.

---

### Post by dpro on 2007-08-07
I think you're right about the aOpen..
When I looked around for info regarding tundra 1555, this link ([ftp://ftp.aopen.com/pub/nb/1555/](ftp://ftp.aopen.com/pub/nb/1555/)) was posted in a forum. In only contains windows drivers though.

I'll see what I can do with your last post! Thanks heeps for all your help! :)

---

### Post by dpro on 2007-08-07
I extracted the files from "#  Acer Hotkey driver for Linux - acerhk-0.5.34.tgz. " 
(from [http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/)),

then I got some errors:

make
```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/pat/downloads/acer modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/pat/downloads/acer/acerhk.o
/home/pat/downloads/acer/acerhk.c:38:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/pat/downloads/acer/acerhk.o] Error 1
make[1]: *** [_module_/home/pat/downloads/acer] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [acerhk.ko] Error 2
```

It said that I might need to change KERNELSRC in the makefile, but that is well above my head.

---

### Post by noob12 on 2007-08-07
The docs say that this laptop has a fully SW based RF-kill switch and ipw2100 docs indicate the driver can't directly toggle this type of RF-kill switch;  so yes, you must install the additional module to control that.

You'll need to install the build-essential and appropriate header package before building.
```

sudo aptitude install build-essential linux-headers-`uname -r` 

```
Note that those characters around the uname are both backquotes not apostrophe/single-quote.  Cut and paste from the code box above should work.

---

### Post by dpro on 2007-08-07
Hey, you're back! :)

So I ran the line you suggested, and it seemed like everything went well.
However, I still get the same errors like before, when running the "make" 
```

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/pat/downloads/acer modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/pat/downloads/acer/acerhk.o
/home/pat/downloads/acer/acerhk.c:38:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/pat/downloads/acer/acerhk.o] Error 1
make[1]: *** [_module_/home/pat/downloads/acer] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [acerhk.ko] Error 2

```

---

### Post by noob12 on 2007-08-07
OK.  I haven't tried building that module before, so I'm a bit blind.  Also, I'm only back for a few minutes.

My guess is that you have to run or re-run the configure step before make.  If there is a file named README, INSTALL, BUILD, or CONFIGURE in the tarball, it may provide instructions on setting up and running the configure step.  I may get a chance to try a build later today.  If I'm successful, I can provide step-by-step instructions.  Never built this package before.

---

### Post by dpro on 2007-08-07
Okay. 
There is an INSTALL file and, as far as I know, I've followed its instruction exactly, but still the above mentioned errors occur :S


I can't thank  you enough for all your help. Absolutely awsome :)

---

### Post by noob12 on 2007-08-08
OK.  I was able to build the module on my box also 2.6.20-16 Feisty.   To build the module you just have to make a slight change to the C code.  They have an old name for one header file.  If you change this, it should build fine.

In the acerhk sources, open acerhk.c in a text editor such as gedit.  Find the line that says
```

#include <linux/config.h>

```
Change it to read
```

#include <linux/autoconf.h>

```
Save and exit.

Then
```
make clean all
```

Provided your build succeeded, you can then run
```

sudo make install

```
Note:  If you want to see what this does before running it as root type **make -n install**.

Now you should be able to insert the module and try starting it.  The instructions say you must use the poll option.
The verbose flag here will give us more debugging info in dmesg if we have problems.
```

sudo modprobe -v acerhk poll=1 verbose=1

```

Now the test.  Toggle your wifi hotkey and check the value of
```

cat /sys/class/net/*/device/rf_kill

```
which should become 0.

If this works, we can proceed with your wifi setup.

---

### Post by dpro on 2007-08-08
Progress!

Everything went well (no error messages) until the "sudo insmod acerhk" where I got a no such file or directory message.
```
insmod: can't read 'acerhk': No such file or directory
```

---

### Post by noob12 on 2007-08-08
That's because there was a noobish mistake in my commands.  You don't need to both insmod and modprobe.  Just leave out the insmod.  I've gone back and edited the previous post to leave this out.

Note:  On my machine I get an error when I run the modprobe, but I'm hoping it is because I don't have the appropriate hardware.  If you get an error during the modprobe, we need to look for someone who has built it successfully for this kernel.

UPDATE:  I also added a verbose=1 flag to the modprobe.  This will put out more kernel logging in dmesg where we can look at it if it fails.

---

### Post by dpro on 2007-08-08
That worked without any errors, but cat /sys/class/net/*/device/rf_kill still says 2 :/

So.. here's the dmesg:

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ce000 size: 0000000000002000 end: 00000000000d0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f5e0000 end: 000000001f6e0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f6e0000 size: 000000000000b000 end: 000000001f6eb000 type: 3
[    0.000000] copy_e820_map() start: 000000001f6eb000 size: 0000000000015000 end: 000000001f700000 type: 4
[    0.000000] copy_e820_map() start: 000000001f700000 size: 0000000000900000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec10000 size: 0000000000010000 end: 00000000fec20000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffffc00 size: 0000000000000400 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6130
[    0.000000] ACPI: RSDT (v001 PTLTD  Montara  0x06040000  LTP 0x00000000) @ 0x1f6e658e
[    0.000000] ACPI: FADT (v001 INTEL  MONTARAG 0x06040000 PTL  0x00000050) @ 0x1f6eaed2
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f6eafd8
[    0.000000] ACPI: SSDT (v001 INTEL    GV3Ref 0x00001001 MSFT 0x0100000e) @ 0x1f6e65be
[    0.000000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Detected 1399.892 MHz processor.
[    6.237050] Built 1 zonelists.  Total pages: 127731
[    6.237056] Kernel command line: root=UUID=f0875865-5370-4e0f-b32b-b314640a6dd3 ro quiet splash
[    6.237271] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    6.237278] mapped APIC to ffffd000 (013fa000)
[    6.237282] Enabling fast FPU save and restore... done.
[    6.237286] Enabling unmasked SIMD FPU exception support... done.
[    6.237296] Initializing CPU#0
[    6.237373] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    6.238975] Console: colour VGA+ 80x25
[    6.239194] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    6.239462] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.258483] Memory: 499512k/514944k available (1992k kernel code, 14912k reserved, 900k data, 328k init, 0k highmem)
[    6.258497] virtual kernel memory layout:
[    6.258498]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    6.258500]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    6.258502]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    6.258503]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    6.258505]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    6.258507]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    6.258508]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    6.258513] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    6.337314] Calibrating delay using timer specific routine.. 2801.65 BogoMIPS (lpj=5603306)
[    6.337367] Security Framework v1.0.0 initialized
[    6.337377] SELinux:  Disabled at boot.
[    6.337399] Mount-cache hash table entries: 512
[    6.337566] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    6.337582] CPU: L1 I cache: 32K, L1 D cache: 32K
[    6.337585] CPU: L2 cache: 1024K
[    6.337589] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    6.337600] Compat vDSO mapped to ffffe000.
[    6.337605] Remapping vsyscall page to ffffe000
[    6.337618] Checking 'hlt' instruction... OK.
[    6.353405] SMP alternatives: switching to UP code
[    6.353589] Freeing SMP alternatives: 11k freed
[    6.353798] Early unpacking initramfs... done
[    6.757033] ACPI: Core revision 20060707
[    6.757906] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    6.760196] ACPI: setting ELCR to 0200 (from 0c00)
[    6.769722] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
[    6.769728] SMP motherboard not detected.
[    6.769731] Local APIC not detected. Using dummy APIC emulation.
[    6.769771] Brought up 1 CPUs
[    6.770066] Booting paravirtualized kernel on bare hardware
[    6.770140] Time: 18:58:33  Date: 07/08/107
[    6.770178] NET: Registered protocol family 16
[    6.770281] EISA bus registered
[    6.770286] ACPI: bus type pci registered
[    6.771514] PCI: PCI BIOS revision 2.10 entry at 0xfd6c4, last bus=3
[    6.771517] PCI: Using configuration type 1
[    6.771520] Setting up standard PCI resources
[    6.782910] ACPI: Interpreter enabled
[    6.782913] ACPI: Using PIC for interrupt routing
[    6.783617] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    6.783625] PCI: Probing PCI hardware (bus 00)
[    6.784629] Boot video device is 0000:00:02.0
[    6.784933] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    6.784938] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    6.785326] PCI: Transparent bridge - 0000:00:1e.0
[    6.785387] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    6.785391] Please report the result to linux-kernel to fix this permanently
[    6.785407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    6.790918] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    6.791751] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    6.791994] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    6.792233] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    6.792475] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    6.792713] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    6.792952] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    6.793218] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[    6.793455] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    6.796396] Linux Plug and Play Support v0.97 (c) Adam Belay
[    6.796408] pnp: PnP ACPI init
[    7.000953] pnp: PnP ACPI: found 12 devices
[    7.000959] PnPBIOS: Disabled by ACPI PNP
[    7.001014] PCI: Using ACPI for IRQ routing
[    7.001017] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.007430] NET: Registered protocol family 8
[    7.007432] NET: Registered protocol family 20
[    7.007519] pnp: 00:04: ioport range 0x600-0x60f has been reserved
[    7.007819] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    7.007837] PCI: Bus 3, cardbus bridge: 0000:02:09.0
[    7.007840]   IO window: 00003000-000030ff
[    7.007845]   IO window: 00003400-000034ff
[    7.007850]   PREFETCH window: 30000000-33ffffff
[    7.007855]   MEM window: 38000000-3bffffff
[    7.007859] PCI: Bridge: 0000:00:1e.0
[    7.007862]   IO window: 3000-3fff
[    7.007868]   MEM window: e0200000-e02fffff
[    7.007873]   PREFETCH window: 30000000-35ffffff
[    7.007882] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    7.007890] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.008094] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    7.008099] PCI: setting IRQ 10 as level-triggered
[    7.008103] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[    7.008142] NET: Registered protocol family 2
[    7.040934] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    7.041033] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    7.041166] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    7.041237] TCP: Hash tables configured (established 16384 bind 8192)
[    7.041241] TCP reno registered
[    7.052998] checking if image is initramfs... it is
[    7.840976] Freeing initrd memory: 6778k freed
[    7.841267] Simple Boot Flag at 0x36 set to 0x1
[    7.841491] audit: initializing netlink socket (disabled)
[    7.841509] audit(1186599513.780:1): initialized
[    7.841675] VFS: Disk quotas dquot_6.5.1
[    7.841700] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.841765] io scheduler noop registered
[    7.841769] io scheduler anticipatory registered
[    7.841772] io scheduler deadline registered
[    7.841789] io scheduler cfq registered (default)
[    7.842260] isapnp: Scanning for PnP cards...
[    8.195871] isapnp: No Plug & Play device found
[    8.230448] Real Time Clock Driver v1.12ac
[    8.230519] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.230775] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    8.231758] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    8.231763] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    8.231773] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    8.231865] mice: PS/2 mouse device common for all mice
[    8.232551] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.232843] input: Macintosh mouse button emulation as /class/input/input0
[    8.232881] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    8.232886] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    8.233136] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    8.236697] i8042.c: Detected active multiplexing controller, rev 1.1.
[    8.237911] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.237917] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    8.237920] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    8.237924] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    8.237927] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    8.238076] EISA: Probing bus 0 at eisa.0
[    8.238084] Cannot allocate resource for EISA slot 1
[    8.238088] Cannot allocate resource for EISA slot 2
[    8.238091] Cannot allocate resource for EISA slot 3
[    8.238113] EISA: Detected 0 cards.
[    8.268209] TCP cubic registered
[    8.268220] NET: Registered protocol family 1
[    8.268249] Using IPI No-Shortcut mode
[    8.268324] ACPI: (supports S0 S3 S4 S5)
[    8.268375]   Magic number: 3:963:998
[    8.268392]   hash matches device ttyae
[    8.268541]   hash matches device 00:00
[    8.268730] Freeing unused kernel memory: 328k freed
[    8.272073] Time: tsc clocksource has been installed.
[    8.283412] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.510546] Capability LSM initialized
[    9.550801] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    9.550809] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.324000] Time: acpi_pm clocksource has been installed.
[    3.524000] ACPI: Thermal Zone [THRS] (53 C)
[    3.744000] ACPI: Thermal Zone [THRC] (48 C)
[    4.168000] usbcore: registered new interface driver usbfs
[    4.168000] usbcore: registered new interface driver hub
[    4.168000] usbcore: registered new device driver usb
[    4.168000] USB Universal Host Controller Interface driver v3.0
[    4.168000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.168000] PCI: setting IRQ 11 as level-triggered
[    4.168000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.168000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.168000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.168000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.168000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    4.168000] usb usb1: configuration #1 chosen from 1 choice
[    4.168000] hub 1-0:1.0: USB hub found
[    4.168000] hub 1-0:1.0: 2 ports detected
[    4.272000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.272000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.272000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.272000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.272000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.272000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    4.272000] usb usb2: configuration #1 chosen from 1 choice
[    4.272000] hub 2-0:1.0: USB hub found
[    4.272000] hub 2-0:1.0: 2 ports detected
[    4.280000] ieee1394: Initialized config rom entry `ip1394'
[    4.376000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.376000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.376000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.376000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.376000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.376000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    4.376000] usb usb3: configuration #1 chosen from 1 choice
[    4.376000] hub 3-0:1.0: USB hub found
[    4.376000] hub 3-0:1.0: 2 ports detected
[    4.480000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    4.480000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    4.480000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.480000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.480000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.480000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.480000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.480000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    4.484000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.488000] usb usb4: configuration #1 chosen from 1 choice
[    4.488000] hub 4-0:1.0: USB hub found
[    4.488000] hub 4-0:1.0: 6 ports detected
[    4.592000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[    4.644000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.652000] b44.c:v1.01 (Jun 16, 2006)
[    4.652000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    4.652000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    4.656000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0a:e4:20:33:2b
[    4.668000] SCSI subsystem initialized
[    4.680000] libata version 2.20 loaded.
[    4.688000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.688000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.688000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.688000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.688000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.688000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.688000] scsi0 : ata_piix
[    4.852000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[    4.852000] ata1.00: ATA-7: SAMSUNG MP0804H, UE100-14, max UDMA/100
[    4.852000] ata1.00: 156368016 sectors, multi 16: LBA48 
[    4.860000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[    4.860000] ata1.00: configured for UDMA/100
[    4.860000] scsi1 : ata_piix
[    5.180000] ata2.00: ATAPI, max UDMA/33
[    5.344000] ata2.00: configured for UDMA/33
[    5.344000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0804H  UE10 PQ: 0 ANSI: 5
[    5.344000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UX10 PQ: 0 ANSI: 5
[    5.360000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[    5.364000] sda: Write Protect is off
[    5.364000] sda: Mode Sense: 00 3a 00 00
[    5.364000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.364000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[    5.364000] sda: Write Protect is off
[    5.364000] sda: Mode Sense: 00 3a 00 00
[    5.364000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.364000]  sda: sda1 sda2 sda3
[    5.396000] sd 0:0:0:0: Attached scsi disk sda
[    5.400000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.400000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.408000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.408000] Uniform CD-ROM driver Revision: 3.20
[    5.408000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.676000] Attempting manual resume
[    5.676000] swsusp: Resume From Partition 8:2
[    5.676000] PM: Checking swsusp image.
[    5.676000] PM: Resume from disk failed.
[    5.732000] kjournald starting.  Commit interval 5 seconds
[    5.732000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.924000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[03e40a00b7002022]
[   20.040000] NET: Registered protocol family 17
[   20.168000] iTCO_vendor_support: vendor-support=0
[   20.168000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.168000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.168000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.272000] intel_rng: FWH not detected
[   20.476000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.604000] agpgart: Detected an Intel 855 Chipset.
[   20.604000] agpgart: Detected 8060K stolen memory.
[   20.612000] agpgart: AGP aperture is 128M @ 0xe8000000
[   20.624000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.628000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.496000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   21.540000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   21.664000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   21.664000] b44: eth0: Flow control is off for TX and off for RX.
[   21.668000] parport: PnPBIOS parport detected.
[   21.668000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.680000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   21.680000] wbsd: Copyright(c) Pierre Ossman
[   21.756000] ieee80211_crypt: registered algorithm 'NULL'
[   21.776000] Yenta: CardBus bridge found at 0000:02:09.0 [17c0:3003]
[   21.776000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.776000] Yenta: Routing CardBus interrupts to PCI
[   21.776000] Yenta TI: socket 0000:02:09.0, mfunc 0x01001002, devctl 0x64
[   21.784000] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   21.932000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.932000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.968000] irda_init()
[   21.968000] NET: Registered protocol family 23
[   22.012000] Yenta: ISA IRQ mask 0x0018, PCI irq 10
[   22.012000] Socket status: 30000007
[   22.012000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   22.012000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   22.012000] cs: IO port probe 0x3000-0x3fff: clean.
[   22.012000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   22.012000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   22.012000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   22.012000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.028000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   22.028000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   22.048000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   22.048000] nsc-ircc, chip->init
[   22.048000] nsc-ircc, Found chip at base=0x02e
[   22.048000] nsc-ircc, driver loaded (Dag Brattli)
[   22.048000] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.048000] nsc-ircc, Found chip at base=0x02e
[   22.048000] nsc-ircc, driver loaded (Dag Brattli)
[   22.048000] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.048000] pnp: Device 00:09 disabled.
[   22.404000] cs: IO port probe 0x100-0x3af: clean.
[   22.404000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.404000] cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   22.404000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.408000] cs: IO port probe 0xa00-0xaff: clean.
[   23.272000] intel8x0_measure_ac97_clock: measured 55482 usecs
[   23.272000] intel8x0: clocking to 48000
[   23.276000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   23.276000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   23.276000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   23.532000] eth1: Radio is disabled by RF switch.
[   23.796000] fuse init (API version 7.8)
[   23.832000] lp0: using parport0 (interrupt-driven).
[   23.892000] Adding 498004k swap on /dev/disk/by-uuid/d1f8b227-c475-4973-b2df-17aec4022824.  Priority:-1 extents:1 across:498004k
[   24.056000] EXT3 FS on sda3, internal journal
[   24.276000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.316000] NET: Registered protocol family 10
[   24.316000] lo: Disabled Privacy Extensions
[   24.380000] NTFS volume version 3.1.
[   28.592000] ACPI: AC Adapter [AC] (on-line)
[   28.608000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.692000] No dock devices found.
[   28.712000] Using specific hotkey driver
[   28.872000] input: Power Button (FF) as /class/input/input3
[   28.876000] ACPI: Power Button (FF) [PWRF]
[   28.920000] input: Lid Switch as /class/input/input4
[   28.924000] ACPI: Lid Switch [LID]
[   28.964000] input: Sleep Button (CM) as /class/input/input5
[   28.968000] ACPI: Sleep Button (CM) [SLP2]
[   29.628000] ACPI: Battery Slot [BAT0] (battery present)
[   29.644000] ibm_acpi: ec object not found
[   29.688000] pcc_acpi: loading...
[   32.504000] ttyS1: LSR safety check engaged!
[   34.660000] eth0: no IPv6 routers present
[   35.340000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.512000] [drm] Initialized drm 1.1.0 20060810
[   36.520000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   36.520000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.524000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   37.168000] ppdev: user-space parallel port driver
[   38.276000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.276000] apm: overridden by ACPI.
[   38.444000] Bluetooth: Core ver 2.11
[   38.444000] NET: Registered protocol family 31
[   38.444000] Bluetooth: HCI device and connection manager initialized
[   38.444000] Bluetooth: HCI socket layer initialized
[   38.492000] Bluetooth: L2CAP ver 2.8
[   38.492000] Bluetooth: L2CAP socket layer initialized
[   38.640000] Bluetooth: RFCOMM socket layer initialized
[   38.640000] Bluetooth: RFCOMM TTY layer initialized
[   38.640000] Bluetooth: RFCOMM ver 1.8
[   49.728000] eth0: no IPv6 routers present
[   95.664000] b44: eth0: Link is down.
[  136.828000] acerhk: registered input device
[  136.828000] input: Acer hotkey driver as /class/input/input6
[  136.828000] acerhk: start search for model string at c00f0000
[  136.836000] acerhk: found model string 'AOpen' at c00f25cc
[  136.836000] acerhk: Model type 2, calling launch_connect(1)
[  136.836000] acerhk: cmos index set to 0x60
[  136.836000] acerhk: bios routine found at 0xc00fdd00
[  136.836000] Acer Travelmate hotkey driver v0.5.34
[  136.836000] acerhk: starting key polling, every 50 ms
[  272.664000] b44: eth0: Link is up at 100 Mbps, full duplex.
[  272.664000] b44: eth0: Flow control is off for TX and off for RX.
[  272.664000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  288.936000] eth0: no IPv6 routers present
```

---

### Post by noob12 on 2007-08-08
Rebooting unloaded the module because we hadn't set it up in your /etc/modules list.  Let's do that so it loads each time.

```

echo "acerhk poll=1 verbose=1" | sudo tee -a /etc/modules

```

---

### Post by noob12 on 2007-08-08
If you haven't rebooted, try this
```

sudo /sbin/ifdown eth1
sudo modprobe -r ipw2100
# now toggle the switch
sudo modprobe ipw2100
sudo /sbin/ifup eth1

```

---

### Post by noob12 on 2007-08-09
dpro:  What happened?  The dmesg looked healthy.  DId you give up?

---

### Post by dpro on 2007-08-10
Sorry, I've been working a lot lately. I'll get back to it tonight (8 hours or so).

---

### Post by dpro on 2007-08-10
I'm back! :D
Okay,so I added

```
echo "acerhk poll=1 verbose=1" | sudo tee -a /etc/modules
```

looked ok (no errors). However I hadn't rebooted yet, so I also tried 

```
sudo /sbin/ifdown eth1
```
and got: "/sbin/ifdown: interface eth1 not configured."

```
sudo modprobe -r ipw2100
```
no errors. Did not actually know what you meant by
"# now toggle the switch", so I ran the

```
sudo modprobe -v acerhk poll=1 verbose=1
```
hoping that's what you meant (this is what happens when I start thinking! :P)

```
sudo modprobe ipw2100
```
no errors

```
sudo /sbin/ifup eth1
```
"Ignoring unknown interface eth1=eth1."

Then I just tried 
```
cat /sys/class/net/*/device/rf_kill
```

just for fun, but still got "2".

---

### Post by noob12 on 2007-08-10
The unknown eth1 is happening because you don't have that in your /etc/network/interfaces apparently.

Language barrier or my lack of clarity.  By "toggle the switch" I meant push the wireless control switch/button on the launchpad, and you had to do it at that point in the sequence.  With the acerhk module loaded (as your modprobe did), please try to repeat that sequence, but where it says to toggle the switch, you need to push the launchpad button.

After that we're interested in seeing the trailing lines of dmesg
```

dmesg | tail -200

```

---

### Post by dpro on 2007-08-10
Alright, repeated the steps. 
The commands gave same responses as before, and pressing the switch still doesn't seem to do anything at all.

"dmesg | tail -200" gives:
```
[    4.168000] hub 1-0:1.0: USB hub found
[    4.168000] hub 1-0:1.0: 2 ports detected
[    4.240000] ieee1394: Initialized config rom entry `ip1394'
[    4.272000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.272000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.272000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.272000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.272000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.272000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    4.272000] usb usb2: configuration #1 chosen from 1 choice
[    4.272000] hub 2-0:1.0: USB hub found
[    4.272000] hub 2-0:1.0: 2 ports detected
[    4.376000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.376000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.376000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.376000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.376000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.376000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    4.376000] usb usb3: configuration #1 chosen from 1 choice
[    4.376000] hub 3-0:1.0: USB hub found
[    4.376000] hub 3-0:1.0: 2 ports detected
[    4.480000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    4.480000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    4.480000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.480000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.480000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.480000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.480000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.480000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    4.484000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.484000] usb usb4: configuration #1 chosen from 1 choice
[    4.484000] hub 4-0:1.0: USB hub found
[    4.484000] hub 4-0:1.0: 6 ports detected
[    4.600000] SCSI subsystem initialized
[    4.612000] libata version 2.20 loaded.
[    4.620000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.620000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.620000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.620000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.620000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.620000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.620000] scsi0 : ata_piix
[    5.176000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[    5.176000] ata1.00: ATA-7: SAMSUNG MP0804H, UE100-14, max UDMA/100
[    5.176000] ata1.00: 156368016 sectors, multi 16: LBA48 
[    5.184000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
[    5.184000] ata1.00: configured for UDMA/100
[    5.184000] scsi1 : ata_piix
[    5.504000] ata2.00: ATAPI, max UDMA/33
[    5.668000] ata2.00: configured for UDMA/33
[    5.668000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0804H  UE10 PQ: 0 ANSI: 5
[    5.668000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UX10 PQ: 0 ANSI: 5
[    5.668000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[    5.720000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.732000] b44.c:v1.01 (Jun 16, 2006)
[    5.732000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    5.732000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    5.732000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0a:e4:20:33:2b
[    5.752000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[    5.752000] sda: Write Protect is off
[    5.752000] sda: Mode Sense: 00 3a 00 00
[    5.752000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.752000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[    5.752000] sda: Write Protect is off
[    5.752000] sda: Mode Sense: 00 3a 00 00
[    5.752000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.752000]  sda: sda1 sda2 sda3
[    5.788000] sd 0:0:0:0: Attached scsi disk sda
[    5.792000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.792000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.796000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.796000] Uniform CD-ROM driver Revision: 3.20
[    5.796000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.008000] Attempting manual resume
[    6.008000] swsusp: Resume From Partition 8:2
[    6.008000] PM: Checking swsusp image.
[    6.008000] PM: Resume from disk failed.
[    6.068000] kjournald starting.  Commit interval 5 seconds
[    6.068000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.004000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[03e40a00b7002022]
[   18.976000] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[   20.212000] NET: Registered protocol family 17
[   20.460000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.468000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.712000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.712000] iTCO_vendor_support: vendor-support=0
[   20.744000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.744000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.744000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.224000] agpgart: Detected an Intel 855 Chipset.
[   21.224000] agpgart: Detected 8060K stolen memory.
[   21.232000] agpgart: AGP aperture is 128M @ 0xe8000000
[   21.632000] intel_rng: FWH not detected
[   21.640000] ieee80211_crypt: registered algorithm 'NULL'
[   21.644000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.644000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.840000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   21.840000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   21.840000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   21.840000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   21.840000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   22.044000] parport: PnPBIOS parport detected.
[   22.044000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   22.072000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   22.072000] wbsd: Copyright(c) Pierre Ossman
[   22.116000] eth1: Radio is disabled by RF switch.
[   22.148000] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   22.168000] irda_init()
[   22.168000] NET: Registered protocol family 23
[   22.264000] Yenta: CardBus bridge found at 0000:02:09.0 [17c0:3003]
[   22.264000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   22.264000] Yenta: Routing CardBus interrupts to PCI
[   22.264000] Yenta TI: socket 0000:02:09.0, mfunc 0x01001002, devctl 0x64
[   22.344000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   22.396000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   22.400000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   22.400000] nsc-ircc, chip->init
[   22.400000] nsc-ircc, Found chip at base=0x02e
[   22.400000] nsc-ircc, driver loaded (Dag Brattli)
[   22.400000] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.400000] nsc-ircc, Found chip at base=0x02e
[   22.400000] nsc-ircc, driver loaded (Dag Brattli)
[   22.400000] nsc_ircc_open(), can't get iobase of 0x2f8
[   22.400000] pnp: Device 00:09 disabled.
[   22.500000] Yenta: ISA IRQ mask 0x0010, PCI irq 10
[   22.500000] Socket status: 30000007
[   22.500000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   22.500000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   22.500000] cs: IO port probe 0x3000-0x3fff: clean.
[   22.500000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   22.500000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   22.500000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   22.500000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.828000] cs: IO port probe 0x100-0x3af: clean.
[   22.828000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.828000] cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   22.828000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.832000] cs: IO port probe 0xa00-0xaff: clean.
[   23.764000] intel8x0_measure_ac97_clock: measured 55373 usecs
[   23.764000] intel8x0: clocking to 48000
[   23.888000] fuse init (API version 7.8)
[   23.920000] lp0: using parport0 (interrupt-driven).
[   23.988000] acerhk: registered input device
[   24.036000] input: Acer hotkey driver as /class/input/input3
[   24.040000] acerhk: start search for model string at c00f0000
[   24.040000] acerhk: found model string 'AOpen' at c00f25cc
[   24.040000] acerhk: Model type 2, calling launch_connect(1)
[   24.044000] acerhk: cmos index set to 0x60
[   24.044000] acerhk: bios routine found at 0xc00fdd00
[   24.044000] Acer Travelmate hotkey driver v0.5.34
[   24.044000] acerhk: starting key polling, every 50 ms
[   24.068000] Adding 498004k swap on /dev/disk/by-uuid/d1f8b227-c475-4973-b2df-17aec4022824.  Priority:-1 extents:1 across:498004k
[   24.228000] EXT3 FS on sda3, internal journal
[   24.408000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.492000] NTFS volume version 3.1.
[   28.776000] ACPI: AC Adapter [AC] (on-line)
[   28.800000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.884000] No dock devices found.
[   28.904000] Using specific hotkey driver
[   29.064000] input: Power Button (FF) as /class/input/input4
[   29.068000] ACPI: Power Button (FF) [PWRF]
[   29.108000] input: Lid Switch as /class/input/input5
[   29.112000] ACPI: Lid Switch [LID]
[   29.156000] input: Sleep Button (CM) as /class/input/input6
[   29.160000] ACPI: Sleep Button (CM) [SLP2]
[   29.828000] ACPI: Battery Slot [BAT0] (battery present)
[   29.844000] ibm_acpi: ec object not found
[   29.884000] pcc_acpi: loading...
[   32.752000] ttyS1: LSR safety check engaged!
[   36.704000] [drm] Initialized drm 1.1.0 20060810
[   36.708000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   36.712000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.716000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   37.468000] ppdev: user-space parallel port driver
[   38.400000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.400000] apm: overridden by ACPI.
[   38.568000] Bluetooth: Core ver 2.11
[   38.568000] NET: Registered protocol family 31
[   38.568000] Bluetooth: HCI device and connection manager initialized
[   38.568000] Bluetooth: HCI socket layer initialized
[   38.616000] Bluetooth: L2CAP ver 2.8
[   38.616000] Bluetooth: L2CAP socket layer initialized
[   38.744000] Bluetooth: RFCOMM socket layer initialized
[   38.744000] Bluetooth: RFCOMM TTY layer initialized
[   38.744000] Bluetooth: RFCOMM ver 1.8
[   48.028000] NET: Registered protocol family 10
[   48.028000] lo: Disabled Privacy Extensions
[   48.028000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.028000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  150.924000] ACPI: PCI interrupt for device 0000:02:06.0 disabled
[  150.928000] ieee80211_crypt: unregistered algorithm 'NULL'
[  167.300000] ieee80211_crypt: registered algorithm 'NULL'
[  167.304000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  167.304000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  167.308000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[  167.308000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[  167.308000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[  167.308000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  167.440000] eth1: Radio is disabled by RF switch.
[  167.656000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by noob12 on 2007-08-11
OK.  So at this point, I think we may be very close or we may not be.  It's really hard to do this blind.

In particular, I'm not sure if the acerhk module is going to actually tweak the right bits on the machine to turn on the RF switch or if it is just going to make the value available to software.

I'm going to be away from the forums for a couple of days, but here are some suggestions to try.

See if  /proc/driver/acerhk/wirelessled exists.
```

cat  /proc/driver/acerhk/wirelessled

```

If it says "No such file or directory", then just send me the output of the command
```
ls /proc/driver/acerhk
```
and I'll have to look at that before giving you any further suggestions, and in this case you should skip the remainder of this message.


If that file does exist (doesn't give a No such file or directory error), then you will probably see the number 0 or 1 written out.  *In this case,* please try the following.  
```

sudo /sbin/ifdown eth1
sudo modprobe -r ipw2100
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe ipw2100 debug=15
sudo /sbin/ifup eth1

```

Now
```

cat /sys/class/net/eth1/device/rf_kill

```
We hope this is showing 0.  Let me know what it shows in any case.
Regardless of whether this shows 0 or not, show me the output of

```

iwconfig

```

We're looking for any signs that the radio is actually on.

If things all look like the radio is still off, please send me this
```

dmesg | tail -100

```

If this works, we are very close, and just have to set up some of this to run at boot. Otherwise, it may also show us some signs that we are close to a solution.  I'm still hopeful, but I am also  getting close to the end of my ideas. The final sad option is to get a USB wireless or to seek more knowledgeable help from someone who has got the Tundra or AOpen 1555 working before.

---

### Post by timohnani on 2007-08-11
Hi,

Have a look here:

[http://ubuntuforums.org/showthread.php?t=189540](http://ubuntuforums.org/showthread.php?t=189540)

From the photo of your laptop it seems to be the same one as mine. At that post it tells you how to arrange your laptop to work.

Timo

---

### Post by sdancisin on 2007-08-12
I had the same exact problem. Tried all of the steps listed, but still comes back that the rfkill is 2.

So I updated the BIOS - and seems there was an issue with the Wake on Boot for the Wireless.    It is a acer Travelmate C110


All is working fine now

---

### Post by rikkeb on 2007-08-12
Thank you so much for your help noob12, especially my boyfriend is greatful, since your explanation worked great for him. Unfortunately my computer is a little different. It is an Acer TravelMate 292 LMi and doesn't have the wireless button on top, but the slider on the side mentioned ealier. I have gone through all the steps up till and including #33, although I also tried with

```
sudo /sbin/ifdown eth1
sudo modprobe -r ipw2200
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe ipw2200 debug=15
sudo /sbin/ifup eth1
```

instead of 

```
sudo /sbin/ifdown eth1
sudo modprobe -r ipw2100
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe ipw2100 debug=15
sudo /sbin/ifup eth1
```

since my network card is Intel Pro Wireless 2200BG

Unfortunately

```
cat /sys/class/net/eth1/device/rf_kill
```

still gives me a 2.

If you have any more suggestions, I would be very greatful :KS

/ Rikke

---

### Post by noob12 on 2007-08-12
rikkeb: I would be happy to help you if you start a new thread.  Your situation is similar but sufficiently different from the one on this thread.  When you say "my boyfriend" are you referring to the original poster "dpro" or someone else?

dpro:  Did you get yours working?  If so, we can set up the commands to run automatically.
If not, can continue if you want.  In either case would like to understand what happened.

---

### Post by dpro on 2007-08-13
Hey!

Been away for a few days again. Back now.

I tried the "cat  /proc/driver/acerhk/wirelessled" and I didn't get a no such file..-error, but I got this one:
```
cat: /proc/driver/acerhk/wirelessled: Permission denied
```

ls /proc/driver/acerhk gave this:
```
blueled  info  key  led  wirelessled
```


Well, since I didn't actually get a no such file..-error, and the WIRELESSLED is in the ls..-command, I continued with the steps you mentioned.

```
sudo /sbin/ifdown eth1
sudo modprobe -r ipw2100
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe ipw2100 debug=15
sudo /sbin/ifup eth1
```

and WOHO! The cat /sys/class/net/eth1/device/rf_kill now says 0! Progress right? :P
(By the way, will it still say "0" after rebooting?)

iwconfig:
```
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:16 dBm   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

dmesg | tail -100:
```
[   21.636000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   21.636000] b44: eth0: Flow control is off for TX and off for RX.
[   21.640000] Yenta: ISA IRQ mask 0x0018, PCI irq 10
[   21.640000] Socket status: 30000007
[   21.640000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   21.640000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   21.640000] cs: IO port probe 0x3000-0x3fff: clean.
[   21.640000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   21.640000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   21.640000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   21.640000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   21.640000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   21.640000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   21.644000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   21.656000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   21.656000] wbsd: Copyright(c) Pierre Ossman
[   21.660000] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   21.736000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   21.736000] nsc-ircc, chip->init
[   21.736000] nsc-ircc, Found chip at base=0x02e
[   21.736000] nsc-ircc, driver loaded (Dag Brattli)
[   21.736000] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.736000] nsc-ircc, Found chip at base=0x02e
[   21.736000] nsc-ircc, driver loaded (Dag Brattli)
[   21.736000] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.736000] pnp: Device 00:09 disabled.
[   21.940000] eth1: Radio is disabled by RF switch.
[   22.120000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   22.120000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.348000] cs: IO port probe 0x100-0x3af: clean.
[   22.352000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.352000] cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   22.352000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.352000] cs: IO port probe 0xa00-0xaff: clean.
[   23.376000] intel8x0_measure_ac97_clock: measured 55385 usecs
[   23.376000] intel8x0: clocking to 48000
[   23.512000] fuse init (API version 7.8)
[   23.544000] lp0: using parport0 (interrupt-driven).
[   23.612000] acerhk: registered input device
[   23.660000] input: Acer hotkey driver as /class/input/input3
[   23.664000] acerhk: start search for model string at c00f0000
[   23.664000] acerhk: found model string 'AOpen' at c00f25cc
[   23.664000] acerhk: Model type 2, calling launch_connect(1)
[   23.664000] acerhk: cmos index set to 0x60
[   23.664000] acerhk: bios routine found at 0xc00fdd00
[   23.664000] Acer Travelmate hotkey driver v0.5.34
[   23.664000] acerhk: starting key polling, every 50 ms
[   23.688000] Adding 498004k swap on /dev/disk/by-uuid/d1f8b227-c475-4973-b2df-17aec4022824.  Priority:-1 extents:1 across:498004k
[   23.848000] EXT3 FS on sda3, internal journal
[   23.984000] NET: Registered protocol family 10
[   23.984000] lo: Disabled Privacy Extensions
[   24.076000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.148000] NTFS volume version 3.1.
[   28.388000] ACPI: AC Adapter [AC] (on-line)
[   28.412000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.484000] No dock devices found.
[   28.504000] Using specific hotkey driver
[   28.664000] input: Power Button (FF) as /class/input/input4
[   28.668000] ACPI: Power Button (FF) [PWRF]
[   28.716000] input: Lid Switch as /class/input/input5
[   28.720000] ACPI: Lid Switch [LID]
[   28.760000] input: Sleep Button (CM) as /class/input/input6
[   28.764000] ACPI: Sleep Button (CM) [SLP2]
[   29.396000] ACPI: Battery Slot [BAT0] (battery present)
[   29.412000] ibm_acpi: ec object not found
[   29.452000] pcc_acpi: loading...
[   32.312000] ttyS1: LSR safety check engaged!
[   34.736000] eth0: no IPv6 routers present
[   35.156000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.304000] [drm] Initialized drm 1.1.0 20060810
[   36.312000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   36.312000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.316000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   37.092000] ppdev: user-space parallel port driver
[   38.036000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.036000] apm: overridden by ACPI.
[   38.200000] Bluetooth: Core ver 2.11
[   38.200000] NET: Registered protocol family 31
[   38.200000] Bluetooth: HCI device and connection manager initialized
[   38.200000] Bluetooth: HCI socket layer initialized
[   38.252000] Bluetooth: L2CAP ver 2.8
[   38.252000] Bluetooth: L2CAP socket layer initialized
[   38.384000] Bluetooth: RFCOMM socket layer initialized
[   38.384000] Bluetooth: RFCOMM TTY layer initialized
[   38.384000] Bluetooth: RFCOMM ver 1.8
[   49.988000] eth0: no IPv6 routers present
[  461.024000] ACPI: PCI interrupt for device 0000:02:06.0 disabled
[  461.028000] ieee80211_crypt: unregistered algorithm 'NULL'
[  501.060000] ieee80211_crypt: registered algorithm 'NULL'
[  501.072000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  501.072000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  501.080000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[  501.080000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[  501.080000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[  501.080000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  501.460000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  602.636000] b44: eth0: Link is down.
[  634.016000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  634.032000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  706.552000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by dpro on 2007-08-13
Okay, so I rebooted and the cat /sys/class/net/eth1/device/rf_kill say 2 again (You probably knew it would, right?) 

I repeated the five steps as before and then it says 0.
My point is, I'm now writing this post through the wireless network, using Ubuntu! :D

The only thing left would be making it so that cat /sys/class/net/eth1/device/rf_kil says 0 on startup. Is this possible?

This is so awsome. I cannot thank you enough for all your trouble :)

---

### Post by rikkeb on 2007-08-13
I have posted a new thread here:

[http://ubuntuforums.org/showthread.php?p=3181090](http://ubuntuforums.org/showthread.php?p=3181090)

Thank you so much. My boyfriend isn't dpro, he just stumbled upon the thread having the same problem, he uses a Travlemate C110.

/ Rikke

---

### Post by noob12 on 2007-08-15
dpro asked:
> 
The only thing left would be making it so that cat /sys/class/net/eth1/device/rf_kil says 0 on startup. Is this possible?


Yes, but please bear with me.  I need you to try one more experiment to determine the right flags to use with acerhk to make this work most cleanly.

Please try this
```

sudo modprobe -r acerhk
sudo modprobe acerhk poll=1 autowlan=1 verbose=1

```

Now please try using the launchpad wireless button and seeing if it changes the state shown by
```

cat /sys/class/net/eth1/device/rf_kill

```
from 2 to 0 and back.

If this does get your launchpad key working, then you just need to edit your /etc/modules file as follows so that your launchpad button will control the wireless normally.  Only do this change if your launchpad button starts to work.
```

xhost +
sudo gedit /etc/modules

```
Find and edit the line that has **acerhk** in it and edit it to look like
```
acerhk poll=1 autowlan=1 verbose=1
```
Save and exit.
You can later remove the verbose=1.  This is just for our diagnostics.

If the above steps worked both to enable and disable the wireless, I think you are done.  

If the steps above don't make the launchpad key work, or if you decide you want to force it to 0 independent of the button, then I can provide you instructions to setup the necessary commands (your 5 steps) to run automatically at boot-time before networking starts up.

Let me know.

---

### Post by berget on 2007-08-15
I have been watching this thread eagerly as I have the same type of computer (and problem) as mr. dpro. 

:popcorn:

Would you be willing to make a small step-by-step guide to fixing this problem, or an automated script that could be applied to fix this? I'm sure there must be at least a couple dozen acer/tundra users who have the same problem when switching to Ubuntu.

Thanks for all the help so far!

---

### Post by noob12 on 2007-08-15
Yes.  So far dpro and rikkeb (see her posting and reference to her thread) have been the test subjects.  I will try to put a HOWTO out there.  One impediment is that I will be gone and away from any computers next week, so I'm reluctant to put anything out there and not be around to help edit/correct it.

The common part is building and installing acerhk.    After that the details depend on your laptop and the exact switching mechanism.  The rfswitch link [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix) referenced in a couple of my postings has terse but very useful tips if you mostly know what to do or are good at drawing analogies from what's here.

All of the useful instructions in this thread (excluding the very useful feedback from dpro) are in the following posts:  #18, #22, #33, and #41.  If you have exactly the same laptop as dpro and are impatient, then following those will probably get you where you need to be, and at least to the point of 41, where I'm still waiting for feedback.  Perhaps you could test that for me and let me know how the story ends.  Once I have that feedback from you or dpro, I can finish a HOWTO.

If you don't have the exact same laptop, I'd suggest you start a different thread, and PM me to help you there.

---

### Post by mandeepkaur on 2007-08-17
Hi,

My case is same as above and my laptop is also same
The wireless of my is on 
I went through all these instructions. I got the following output.
what happens is that when I tried to scan network through wireless assistant a pop up window comes that says

Radio of your wireless card is off
Would you like to turn it on
yes No

I clicked on yes
It say no networks found
and still I am not able to get into network.

Please advise.

I look forward to hearing from you.

With Regards

Mandeep Kaur

---

### Post by noob12 on 2007-08-17
I use the default NetworkManager.  I don't know much about Wireless Assistant and I don't know what it's doing when it says it is turning the radio on.

From the perspective of the hard RF switch the definitive check is looking at the rf_kill file (this cat command comes up in several postings on the thread):  **cat /sys/class/net/*/device/rf_kill** (you can use the * if you have just one wireless device or you can substitute the interface name for a specific wireless device).  If that shows 0, it means the rf-kill-switch is off and the radio is on.  If that's still 2, then something you applied isn't working.  If it is 1, it is turned off by software.   

Another indication that the radio is on would be that **iwconfig** will show nonzero signal and transmit power or **iwlist scan** is showing access point stations.

You may have a different or additional problem from the one in this thread.  My suggestion is that if you have the same laptop as the one in this thread and the rf_kill value still shows 2, then it's still on-topic, so stay on this thread.  Otherwise, start another, and PM me if necessary. I'll help you there.  I'll be off the forum next week; when I return I'll write a HOWTO on this topic.

---

### Post by mandeepkaur on 2007-08-17
Thanks for your reply
I have checked with /sys/class/net/*/device/rf_kill the vale is 2 and I am not able to turn it to 0. Please help me to rectify this problem

Thanks once again
Mandeep Kaur

---

### Post by noob12 on 2007-08-17
OK.  Can you let me know the following.

What is the make and model number of the laptop you are using?

Post the output of the following commands.  They'll let me know where you are.
```

uname -r

find /lib/modules -name "acerhk.ko"

lsmod | grep -e '(acerhk|ipw2100)'

cat /etc/modules

ls -l /proc/driver/acerhk/wirelessled

ifconfig -a

iwconfig

```
No excerpts please.

---

### Post by mandeep kaur on 2007-08-18
Thanks for your reply 

Following is the outputs of above commands
[B][U]
uname -r[/U][/B] **Output**: 2.6.15-26-386

**_find /lib/modules -name “acerhk.ko”_**
**Output: **/lib/modules/2.6.15-26-386/kernel/drivers/input/misc/acerhk.ko
**_cat /etc/modules_**
**Output: **
# /etc/modules: kernel modules to load at boot time
#
#This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with “#” are ignored.
lp
psmouse
sbp2
sr_mod
[B][U]
ls-l/proc/driver/acerhk/wirelessled[/U][/B]
**Output:** bash: ls-l/proc/driver/acerhk/wirelessled: No such file or directory

**_iwconfig_**
**Output: **
lo no wireless extensions.
eth1  unassociated ESSID:off/any Nickname:”ipw2100”
         Mode: Managed  Channel=0 Access Point: Not-Associated
         Bit Rate=0 kb/s Tx-Power:off
         Retry min limit:7  RTS thr:off Fragment thr:off
         Encryption key:off
         Power Management:off
         Link Quality:0 Signal level:0 Noise level:0
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0
etho no wireless extensions

[B][U]
ifconfig -a[/U][/B]
[B]
Output: [/B]
eth0   Link encap:Ethernet  HWaddr 00:0A:E4:20:29:00
          inet addr:192.168.2.245 Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fe4a:d5be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10

eth1     Link encap:Ethernet  HWaddr 00:05:5D:4B:15:CF
            BROADCAST MULTICAST MTU:1500 Metric:1
            RX Packets :0 errors:0 dropped:0 overruns:0 frame:0
            TX  Packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytex:0 (0.0 b) TX bytes :0 (0.0 b)
             Interrupt:10 Base address: 0*a000 Memory : e0203000-e0203fff
lo          Link encap: Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
             UP LOOPBACK RUNNING MTU: 16436 Metric:1
             RX packets: 19 errors:0 dropped:0 overruns:0 frame:0
             TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:1444 (1.4 KiB)  TX bytes:1444 (1.4 KiB)

Please see above detail help you to rectify the problem

Thanks
Mandeep kaur

---

### Post by dpro on 2007-08-18
Alright!
Sorry for not replying earlier, but I've been gone for some days now, but here it goes:

I ran
```
sudo modprobe -r acerhk
sudo modprobe acerhk poll=1 autowlan=1 verbose=1
```
and pressed the launchpad wireless button, and
```
cat /sys/class/net/eth1/device/rf_kill
```
turn to 0.

Then I edited /etc/modules like you mentioned, rebooted and now the wireless button
works on startup!

So it seems my problem is now Solved (capital S!)!
This is absolutely fantastic! You must be bored with all of my "thank you"s but guess what;
here comes another one!

Thanks heeps for all your trouble:)
If you ever come to Norway, I'll buy you a beer! ;)

---

### Post by mandeep kaur on 2007-08-18
Your problem is solved but not mine. Please help me to rectify it.

When I have tried to change the value in rf_kill 
I got the below output
Warning: The file has been changed since reading it.
Do you really want to write to it (y/n)
I said 'y'
rf_kill "E667: fsync failed
Hit enter or type command

And I am not able to change the value

Please help me.

thanks

Mandeep Kaur

---

### Post by noob12 on 2007-08-18
dpro:  Hah. I might take you up on that beer sometime!   Thanks for your help and very useful feedback.  Based on this I'll be writing a HOWTO for users of the same laptop.

---

### Post by noob12 on 2007-08-18
mandeep:  Here are some first steps.  Let me know if these work.  I will be away from the forum for about a week.  After my return, I will write a step-by-step HOWTO based on my instructions in this thread and dpro's feedback.

Your outputs suggest that you have built the module and installed it, apparently by hand (because it is not in the normal place that the Makefile puts it).  However you never loaded it.  If you installed it by hand-copying, make sure you ran depmod.  The makefile will install it with the proper commands.  If you did not run depmod after copying the driver into place, run it now as follows.

```

sudo depmod -a

```

I asked earlier whether you had the exact same laptop as dpro (Tundra or AOpen 1555), but you haven't explicitly told me that you do, or I may have missed it.  If you don't have the same laptop, different steps may be needed; so start a different thread in that case.  **These instructions assume that you do have the same model laptop as dpro.**

```

sudo modprobe -r acerhk
sudo modprobe acerhk poll=1 autowlan=1

```
Now pressing the wireless control button on the launchpad should toggle the wireless between ON and OFF.  The led should go on and off by pushing the button.  Put it in the ON state.

If the LED doesn't work, you can look at 
```

cat /proc/driver/acerhk/wirelessled

```
instead.  Toggling the button on the launchpad will turn this between 0 and 1.  You want it at 1.

Your wireless may be working now, but you may need to do this.  You can do it regardless.
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2100
sudo modprobe ipw2100
sudo /etc/init.d/networking start

```

Now
```

cat /sys/class/net/*/device/rf_kill

```
This should either be 0 or 1.  If it is 0, it means the radio is on.  If it is 1, it means you need to go to NetworkManager, right click and enable wireless.  If it is 2, you have not got the same laptop or there is some error in the steps followed so far.

If this shows 0 but you still have problems with your wireless, they are not related to the rf-kill switch. Further analysis of that would be needed.

If this all works for you, then you just need to do this to make it work on each reboot.

```

echo "acerhk poll=1 autowlan=1" | sudo tee -a /etc/modules

```

Everything else will just work automatically when you boot.

I will be away from the forum for about a week.  You may catch me before I leave, but otherwise, I'll check back when I return.

---

### Post by mandeep kaur on 2007-08-18
Thanks for your reply

I have the same laptop that dpro have, exactly the same

Thanks & Regards

Mandeep Kaur

---

### Post by mandeep kaur on 2007-08-18
Yes in my case rf_kill is 2 and I am not able to make it 0. The lwireless light on my laptop is on.
Now what should I do? Please give instructions as am new in this field. Please let me know ASAP.

Thanks 
Mandeep Kaur

---

### Post by noob12 on 2007-08-18
Did you follow the instructions in posting #52?

---

### Post by noob12 on 2007-08-18
mandeep:  These instructions should work for that laptop when running kernel version 2.6.20-16-generic and the acerhk version 0.5.34 referenced in this thread and built following instructions in this thread.   It looks like you are running 2.6.20-15-386 which may also have an older ipw2100 driver module.  It also looks like you did not follow the instructions in this thread to build the acerhk module since it is in a different directory from where the instructions here would have put it, so maybe you also don't have the same version of the acerhk module?  Try to match exactly and you should be in the same situation as dpro.  That's the best I can do for now.  I will try to provide more specific help when I return in a week if you haven't got it working.  Best of luck.

---

### Post by berget on 2007-08-19
I can't install the acerhk-module. I am quite a newbie, but I have been sitting around here trying to get this to work for four hours now, so I don't know what to do anymore. Here's the terminal window:

berget@POWER:~$ # change KERNELSRC to the location of your kernel build tree only if
berget@POWER:~$ # autodetection does not work
berget@POWER:~$ #KERNELSRC=/usr/src/linux
berget@POWER:~$ KERNELSRC?=/lib/modules/`uname -r`/build
bash: KERNELSRC?=/lib/modules/2.6.20-16-generic/build: No such file or directory
berget@POWER:~$ # Starting with 2.6.18, the kernel version is in utsrelease.h instead of version.h, accomodate both cases
berget@POWER:~$ KERNELVERSION=$(shell awk -F\" '/REL/ {print $$2}' $(shell grep -s -l REL $(KERNELSRC)/include/linux/version.h $(KERNELSRC)/include/linux/utsrelease.h))
bash: KERNELSRC: command not found
bash: KERNELSRC: command not found
bash: shell: command not found
bash: shell: command not found
berget@POWER:~$ KERNELMAJOR=$(shell echo $(KERNELVERSION)|head -c3)
bash: KERNELVERSION: command not found
bash: shell: command not found
berget@POWER:~$ 
berget@POWER:~$ # next line is for kernel 2.6, if you integrate the driver in the kernel tree
berget@POWER:~$ # /usr/src/linux/drivers/acerhk - or something similar
berget@POWER:~$ # don't forget to add the following line to the parent dir's Makefile:
berget@POWER:~$ # (/usr/src/linux/drivers/Makefile)
berget@POWER:~$ # obj-m                           += acerhk/
berget@POWER:~$ CONFIG_ACERHK?=m
bash: CONFIG_ACERHK?=m: command not found
berget@POWER:~$ obj-$(CONFIG_ACERHK) += acerhk.o
bash: CONFIG_ACERHK: command not found
bash: obj-: command not found
berget@POWER:~$ 
berget@POWER:~$ CFLAGS+=-c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -W
bash: -Wall: command not found
berget@POWER:~$ INCLUDE=-I$(KERNELSRC)/include
bash: KERNELSRC: command not found
berget@POWER:~$ 
berget@POWER:~$ ifeq ($(KERNELMAJOR), 2.6)
bash: syntax error near unexpected token `$(KERNELMAJOR),'
berget@POWER:~$ TARGET := acerhk.ko
bash: TARGET: command not found
berget@POWER:~$ else
bash: syntax error near unexpected token `else'
berget@POWER:~$ TARGET := acerhk.o
bash: TARGET: command not found
berget@POWER:~$ endif
bash: endif: command not found
berget@POWER:~$ 
berget@POWER:~$ SOURCE := acerhk.c
bash: SOURCE: command not found
berget@POWER:~$ 
berget@POWER:~$ all: $(TARGET)
bash: TARGET: command not found
bash: all:: command not found
berget@POWER:~$ 
berget@POWER:~$ help:
bash: help:: command not found
berget@POWER:~$ @echo Possible targets:
bash: @echo: command not found
berget@POWER:~$ @echo -e all\\t- default target, builds kernel module
bash: @echo: command not found
berget@POWER:~$ @echo -e install\\t- copies module binary to /lib/modules/$(KERNELVERSION)/extra/
bash: KERNELVERSION: command not found
bash: @echo: command not found
berget@POWER:~$ @echo -e clean\\t- removes all binaries and temporary files
bash: @echo: command not found
berget@POWER:~$ 
berget@POWER:~$ # this target is only for me, don't use it yourself (Olaf)
berget@POWER:~$ export:
bash: export:: command not found
berget@POWER:~$ sh export.sh
sh: Can't open export.sh
berget@POWER:~$ 
berget@POWER:~$ acerhk.ko: $(SOURCE) acerhk.h
bash: SOURCE: command not found
bash: acerhk.ko:: command not found
berget@POWER:~$ $(MAKE) -C $(KERNELSRC) SUBDIRS=$(PWD) modules
bash: MAKE: command not found
bash: KERNELSRC: command not found
bash: PWD: command not found
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -C
bash: -C: command not found
berget@POWER:~$ 
berget@POWER:~$ acerhk.o: $(SOURCE) acerhk.h
bash: SOURCE: command not found
bash: acerhk.o:: command not found
berget@POWER:~$ $(CC) $(INCLUDE) $(CFLAGS) -DMODVERSIONS -DMODULE -D__KERNEL__ -o $(TARGET) $(SOURCE)
bash: CC: command not found
bash: INCLUDE: command not found
bash: CFLAGS: command not found
bash: TARGET: command not found
bash: SOURCE: command not found
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -D
bash: -DMODVERSIONS: command not found
berget@POWER:~$ 
berget@POWER:~$ asm:$(SOURCE)
bash: SOURCE: command not found
bash: asm:: command not found
berget@POWER:~$ ifeq ($(KERNELMAJOR), 2.6)
bash: syntax error near unexpected token `$(KERNELMAJOR),'
berget@POWER:~$ $(CC) $(INCLUDE) $(INCLUDE)/asm-i386/mach-default $(CFLAGS) -fverbose-asm -S -DMODVERSIONS -DMODULE -D__KERNEL__ $(SOURCE)
bash: CC: command not found
bash: INCLUDE: command not found
bash: INCLUDE: command not found
bash: CFLAGS: command not found
bash: SOURCE: command not found
bash: /asm-i386/mach-default: No such file or directory
berget@POWER:~$ else
bash: syntax error near unexpected token `else'
berget@POWER:~$ $(CC) $(INCLUDE) $(CFLAGS) -fverbose-asm -S -DMODVERSIONS -DMODULE -D__KERNEL__ $(SOURCE)
bash: CC: command not found
bash: INCLUDE: command not found
bash: CFLAGS: command not found
bash: SOURCE: command not found
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -f
bash: -fverbose-asm: command not found
berget@POWER:~$ endif
bash: endif: command not found
berget@POWER:~$ 
berget@POWER:~$ clean:
bash: clean:: command not found
berget@POWER:~$ rm -f *~ *.o *.s *.ko .acerhk* *.mod.c
berget@POWER:~$ 
berget@POWER:~$ load:$(TARGET)
bash: TARGET: command not found
bash: load:: command not found
berget@POWER:~$ insmod $(TARGET)
bash: TARGET: command not found
Usage: insmod filename [args]
berget@POWER:~$ 
berget@POWER:~$ unload:
bash: unload:: command not found
berget@POWER:~$ rmmod acerhk
ERROR: Module acerhk does not exist in /proc/modules
berget@POWER:~$ 
berget@POWER:~$ install: $(TARGET)
bash: TARGET: command not found
bash: install:: command not found
berget@POWER:~$ mkdir -p /lib/modules/$(KERNELVERSION)/extra
bash: KERNELVERSION: command not found
mkdir: cannot create directory `/lib/modules//extra': Permission denied
berget@POWER:~$ cp -v $(TARGET) /lib/modules/$(KERNELVERSION)/extra/
bash: TARGET: command not found
bash: KERNELVERSION: command not found
cp: missing destination file operand after `/lib/modules//extra/'
Try `cp --help' for more information.
berget@POWER:~$ depmod -a


iFATAL: Could not open /lib/modules/2.6.20-16-generic/modules.dep.temp for writing: Permission denied
berget@POWER:~$ 
berget@POWER:~$ 
berget@POWER:~$ sudo depmod -a
Password:
berget@POWER:~$ sudo depmod -a
berget@POWER:~$ make acerhk.ko
make: *** No rule to make target `acerhk.ko'.  Stop.
berget@POWER:~$ 
berget@POWER:~$ cat /sys/class/net/eth1/device/rf_kill
2
berget@POWER:~$  cat /sys/class/net/eth1/device/rf_kill
2
berget@POWER:~$ insmod/modprobe acerhk
bash: insmod/modprobe: No such file or directory
berget@POWER:~$ sudo insmod/modprobe acerhk
sudo: insmod/modprobe: command not found

---

### Post by noob12 on 2007-08-19
Apparently kernel version 2.6.20-16 comes with the 0.5.34 version of the module pre-installed under ubuntu/misc, (i.e. the whole exercise building acerhk can/should be skipped).

You can determine your kernel version using the command **uname -r**.


berget:  You seem to have 2.6.20-16-generic installed. No build necessary.  Just try
the instructions below.
mandeep:  Please try to upgrade to 2.6.20-16-generic and then try just the instructions below.

The following instructions are tested on the 2.6.20-16-generic Ubuntu kernel with the Tundra/AOpen 1555 laptop.  They may work for later kernel versions and 64-bit, but you may have other ipw2100 driver issues with 64-bit.  These assume that you have the Tundra/AOpen 1555 like dpro.  If you have a different laptop, you may need different options on acerhk, so these aren't the right instructions for you.  

You can use cut and paste to avoid errors in transcribing the commands.
```

sudo /etc/init.d/networking stop
sudo modprobe -r acerhk
sudo modprobe acerhk poll=1 autowlan=1
# Toggling the launchpad button should work now, but you can also do this
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
sudo modprobe -r ipw2100
sudo modprobe ipw2100
sudo /etc/init.d/networking start

```

At this point you should see
```

cat /sys/class/net/*/device/rf_kill

```
shows 0 or 1 (not 2).  If so, you're over the rf-switch hurdle.  Just enable wireless in NetworkManager and go.  If you see this no longer shows 2, but you still can't connect, start a new thread.  You've got some other problem.  I and others will still try to help.

If the above works for you, then all you need to do to make things work on reboots is the following:

```

echo "acerhk poll=1 autowlan=1" | sudo tee -a /etc/modules

```

If you get stuck, I apologize that I can't respond during my absence from the forum next week.  I will try to help you both when I return and write a proper short clean HOWTO without all the noise in this posting that occurred as dpro and I figured things out.

---

### Post by berget on 2007-08-20
I never thought I'd be so happy to see a zero in a terminal window. I followed the latest instructions and it works! 

Thanks for all the help, when you come to Norway I'll order the second round of beers following dpro :)

---

### Post by alexicon on 2007-09-02
hey nice one guys! i just installed feisty on a dell inspiron 600m which uses the same intel 2100 3B wifi chipset.

note to the dell users having problems, the key to this whole solve for me was the line:
cat /sys/class/net/*/device/rf_kill

mine was coming up with 2 at the start, but all i had to do to fix my wifi situation was hit the hotkey, fn+F2, ran the cat again and it went straight to 0 without having to do any other configuration (dmesg didnt really suggest that the radio had turned on, but when i checked iwconfig i noticed that it seemed to be working). had to wait a minute or so, for the change to permeate to the network-manager app, but after a minute it saw all my local wifi networks! win!

thanks again dpro for the well phrased question, and thanks much noob12 for your ace guidance.

ubuntu++

---

### Post by xc3RnbFO8P on 2007-09-02
> **noob12 said:**
> mandeep:  Here are some first steps.  Let me know if these work.  I will be away from the forum for about a week.  After my return, I will write a step-by-step HOWTO based on my instructions in this thread and dpro's feedback.

Your outputs suggest that you have built the module and installed it, apparently by hand (because it is not in the normal place that the Makefile puts it).  However you never loaded it.  If you installed it by hand-copying, make sure you ran depmod.  The makefile will install it with the proper commands.  If you did not run depmod after copying the driver into place, run it now as follows.

```

sudo depmod -a

```

I asked earlier whether you had the exact same laptop as dpro (Tundra or AOpen 1555), but you haven't explicitly told me that you do, or I may have missed it.  If you don't have the same laptop, different steps may be needed; so start a different thread in that case.  **These instructions assume that you do have the same model laptop as dpro.**

```

sudo modprobe -r acerhk
sudo modprobe acerhk poll=1 autowlan=1

```
Now pressing the wireless control button on the launchpad should toggle the wireless between ON and OFF.  The led should go on and off by pushing the button.  Put it in the ON state.
.

This worked on Medion MD 97600 Centrino.
Gutsy Gibbon T 5.:lolflag:

---

### Post by noob12 on 2007-09-02
Great to hear.  I don't know what the Medion brand really is, and whether it is another rebranding of the same laptop, but in general if you can identify it as a rebranded version of any of the laptops on the rfswitch support matrix page (here: [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)), you should be able to follow the instructions for acerhk options for that laptop.

---

### Post by xc3RnbFO8P on 2007-09-02
> **noob12 said:**
> Great to hear.  I don't know what the Medion brand really is, and whether it is another rebranding of the same laptop, but in general if you can identify it as a rebranded version of any of the laptops on the rfswitch support matrix page (here: [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)), you should be able to follow the instructions for acerhk options for that laptop.

Medion in known in Germany and Danmark, sold in [http://aldi.com/]("http://aldi.com/")
and I can see in hardware information  Acer hotkey driver.

---

### Post by mandeep kaur on 2007-09-24
Hi,

Thanks for all your help.
The value of 
cat /sys/class/net/*/device/rf_kill
is 0 now and the wireless is up but now the problem is when I restart the system it changes to the value 2.

Please help me how do I get my wireless up permanently.

I look forward to hearing from you.


Thanks

Mandeep Kaur

---

