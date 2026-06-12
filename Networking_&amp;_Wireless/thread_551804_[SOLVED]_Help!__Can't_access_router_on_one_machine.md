---
title: "[SOLVED] Help!  Can't access router on one machine"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by TedGarvin on 2007-09-15
HI, I've been looking for an answer to the this problem and I can't find anything.  You're my only hope.  I have two internet boxes.  One can access the internet thru the router, the other can't.  The broken one can't ping the router, but it can ping itself.  The same machine can access thru xp, so the hardware is working.  I checked and Ubuntu is correctly recognizing the network card (3Com 3c900b),   Anyone have any idea of what I can try next?

 My sister saw me using Beryl and told me "I want that."  I want another Linux convert, so please help me out.

Thanks a lot in advance

I forgot to add, the machine can access the internet if I connect directly thru the dsl modem, but when it is connected to the routher, nothing.  I tried to manually set the router ip address as the DNS and still nothing.

---

### Post by TedGarvin on 2007-09-15
I'm adding the output from a few commands in the hope that it will help.  If anyone can point me in the right direction, I would really appreciate it.

**IFCONFIG**

eth0      Link encap:Ethernet  HWaddr 00:01:02:8E:CE:95  
          inet6 addr: fe80::201:2ff:fe8e:ce95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:60 dropped:0 overruns:0 frame:120
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:8994 (8.7 KiB)
          Interrupt:11 

eth0:avah Link encap:Ethernet  HWaddr 00:01:02:8E:CE:95  
          inet addr:169.254.7.209  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2052 (2.0 KiB)  TX bytes:2052 (2.0 KiB)

[B]
LSPCI[/B]
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0e.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:0f.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 18)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 18)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


**LSHW**

-network
             description: Ethernet interface
             product: 3c900B-TPO Etherlink XL [Cyclone]
             vendor: 3Com Corporation
             physical id: f
             bus info: pci@00:0f.0
             logical name: eth0
             version: 04
             serial: 00:01:02:8e:ce:95
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=3c59x latency=32 maxlatency=48 mingnt=10 multicast=yes


**OUTPUT FROM NETWORKING RESTART**

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5058
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:01:02:8e:ce:95
Sending on   LPF/eth0/00:01:02:8e:ce:95
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:01:02:8e:ce:95
Sending on   LPF/eth0/00:01:02:8e:ce:95
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by TedGarvin on 2007-09-17
I hope I'm not being too vague, but I'm very new to Linux.  If there is some information I should have addedto this post, just let me know.  If no one understands the problem or hasn't encountered it before, can anyone suggest any faqs or other forums where I could look around.  I'm pulling my hair out.  I know it's not a hardware problem because one computer can connect to the router using Ubuntu. 
When she boots into XP, the router sees her and dhcp works just fine.  She gets an IP address and the network and internet are work.  When I connect directly to the dsl modem in Ubuntu, she gets an IP address.   What am I missing???  HELP!

---

### Post by noob12 on 2007-09-17
Plug the machine that you're having problems with into the router, boot Ubuntu and get the output of the following commands:
```

sudo ethtool eth0

```

Also, try disabling ipv6 as follows:  

```
sudo gedit /etc/modprobe.d/aliases
```

Find the line that says "**alias net-pf-10 ipv6**".
**Replace** that line with this whole block:
```

# disabling ipv6
#alias net-pf-10 ipv6
alias net-pf-10 off
alias ipv6 off
# end disabling ipv6

```

Reboot, and see if that helps.

---

### Post by TedGarvin on 2007-09-18
Thanks for the reply Noob.  I replaced the line in the aliases file but it didn't seem to do anything.  Here are the results of ethtool eth0

        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

When I go to network tools, there are still two listings for eth0.  One shows ipv6 and seems to have a personal ip address ( 169.254.7.xxx)  I didn't even know Linux did that.  The other for eth0 has no info.

---

### Post by noob12 on 2007-09-18
OK.  Unless you plan to use IPv6, you will probably want to keep it disabled.  

The ethtool output shows the driver thinks it has a link (which is good).
[ADDED:  By the way, do you expect a 100mbps link?  It is 10, which may be a sign of some issue; we may see more in the dmesg.]

After you next boot that box, can you please post the output of the command ```
dmesg
```  It will be pretty long.  You will want a flash drive or something to transfer the text.

---

### Post by TedGarvin on 2007-09-18
ok here you go.  And when I go to Networking tools, I still see the two entries for eth0 with one using IPv6

```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feec000 end: 000000001ffec000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffec000 size: 0000000000003000 end: 000000001ffef000 type: 3
[    0.000000] copy_e820_map() start: 000000001ffef000 size: 0000000000010000 end: 000000001ffff000 type: 2
[    0.000000] copy_e820_map() start: 000000001ffff000 size: 0000000000001000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
[    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131052
[    0.000000]   HighMem    131052 ->   131052
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131052
[    0.000000] On node 0 totalpages: 131052
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125965 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6da0
[    0.000000] ACPI: RSDT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @ 0x1ffec000
[    0.000000] ACPI: FADT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @ 0x1ffec080
[    0.000000] ACPI: BOOT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @ 0x1ffec040
[    0.000000] ACPI: DSDT (v001   ASUS A7V266   0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Detected 1059.510 MHz processor.
[   24.302800] Built 1 zonelists.  Total pages: 130029
[   24.302807] Kernel command line: root=UUID=c32943b2-82f6-4c70-bc1d-8e211d1886f4 ro quiet splash
[   24.303114] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   24.303130] mapped APIC to ffffd000 (0140a000)
[   24.303137] Enabling fast FPU save and restore... done.
[   24.303141] Enabling unmasked SIMD FPU exception support... done.
[   24.303161] Initializing CPU#0
[   24.303265] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   24.304549] Console: colour VGA+ 80x25
[   24.305208] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.305730] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.331060] Memory: 508600k/524208k available (1993k kernel code, 14988k reserved, 900k data, 328k init, 0k highmem)
[   24.331080] virtual kernel memory layout:
[   24.331082]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   24.331085]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.331087]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   24.331089]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
[   24.331092]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   24.331094]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   24.331096]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   24.331102] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.411216] Calibrating delay using timer specific routine.. 2121.12 BogoMIPS (lpj=4242259)
[   24.411297] Security Framework v1.0.0 initialized
[   24.411309] SELinux:  Disabled at boot.
[   24.411340] Mount-cache hash table entries: 512
[   24.411604] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[   24.411621] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.411626] CPU: L2 Cache: 256K (64 bytes/line)
[   24.411631] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[   24.411650] Compat vDSO mapped to ffffe000.
[   24.411660] Remapping vsyscall page to ffffe000
[   24.411677] Checking 'hlt' instruction... OK.
[   24.427424] SMP alternatives: switching to UP code
[   24.427876] Freeing SMP alternatives: 11k freed
[   24.428354] Early unpacking initramfs... done
[   24.992381] ACPI: Core revision 20060707
[   24.993721] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.995564] ACPI: setting ELCR to 0200 (from 0840)
[   25.020483] CPU0: AMD Athlon(TM) XP1600+ stepping 02
[   25.020493] SMP motherboard not detected.
[   25.020498] Local APIC not detected. Using dummy APIC emulation.
[   25.020584] Brought up 1 CPUs
[   25.021084] Booting paravirtualized kernel on bare hardware
[   25.021204] Time: 10:10:34  Date: 08/18/107
[   25.021270] NET: Registered protocol family 16
[   25.021470] EISA bus registered
[   25.021478] ACPI: bus type pci registered
[   25.023409] PCI: PCI BIOS revision 2.10 entry at 0xf0ed0, last bus=1
[   25.023414] PCI: Using configuration type 1
[   25.023417] Setting up standard PCI resources
[   25.043235] ACPI: Interpreter enabled
[   25.043244] ACPI: Using PIC for interrupt routing
[   25.044288] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.044640] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.044980] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.045316] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.045652] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.045663] PCI: Probing PCI hardware (bus 00)
[   25.045959] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   25.046794] Boot video device is 0000:01:00.0
[   25.046851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.053335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   25.059386] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.059411] pnp: PnP ACPI init
[   25.064610] pnp: PnP ACPI: found 12 devices
[   25.064620] PnPBIOS: Disabled by ACPI PNP
[   25.064741] PCI: Using ACPI for IRQ routing
[   25.064748] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.073787] NET: Registered protocol family 8
[   25.073791] NET: Registered protocol family 20
[   25.074189] pnp: 00:03: ioport range 0xe400-0xe47f could not be reserved
[   25.074195] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   25.074201] pnp: 00:03: ioport range 0x290-0x291 has been reserved
[   25.074206] pnp: 00:03: ioport range 0x370-0x373 has been reserved
[   25.074732] PCI: Bridge: 0000:00:01.0
[   25.074736]   IO window: disabled.
[   25.074745]   MEM window: ee000000-efdfffff
[   25.074751]   PREFETCH window: eff00000-fbffffff
[   25.074778] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.074831] NET: Registered protocol family 2
[   25.111031] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   25.111210] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   25.111570] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   25.111753] TCP: Hash tables configured (established 16384 bind 8192)
[   25.111759] TCP reno registered
[   25.123104] checking if image is initramfs... it is
[   26.195559] Freeing initrd memory: 6788k freed
[   26.195933] Simple Boot Flag at 0x3a set to 0x1
[   26.196451] audit: initializing netlink socket (disabled)
[   26.196481] audit(1190110235.056:1): initialized
[   26.196691] VFS: Disk quotas dquot_6.5.1
[   26.196733] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.196827] io scheduler noop registered
[   26.196833] io scheduler anticipatory registered
[   26.196838] io scheduler deadline registered
[   26.196851] io scheduler cfq registered (default)
[   26.197258] isapnp: Scanning for PnP cards...
[   26.550970] isapnp: No Plug & Play device found
[   26.596690] Real Time Clock Driver v1.12ac
[   26.596781] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.596948] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.597212] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.598212] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.598712] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.599103] mice: PS/2 mouse device common for all mice
[   26.600187] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.600669] input: Macintosh mouse button emulation as /class/input/input0
[   26.600735] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.600744] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.601097] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.601102] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   26.605388] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.605403] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.605718] EISA: Probing bus 0 at eisa.0
[   26.605769] EISA: Detected 0 cards.
[   26.635920] TCP cubic registered
[   26.635932] NET: Registered protocol family 1
[   26.635976] Using IPI No-Shortcut mode
[   26.636099] ACPI: (supports S0 S1 S4 S5)
[   26.636172]   Magic number: 7:47:174
[   26.636296]   hash matches device ttyr0
[   26.637196] Freeing unused kernel memory: 328k freed
[   26.638073] Time: tsc clocksource has been installed.
[   26.650550] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.140971] Capability LSM initialized
[   29.187617] PCI: Enabling device 0000:00:0f.0 (0014 -> 0017)
[   29.188340] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   29.188348] PCI: setting IRQ 11 as level-triggered
[   29.188355] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   29.188370] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[   29.188382] 0000:00:0f.0: 3Com PCI 3c900 Cyclone 10Mbps TPO at e0820000.
[   29.257697] SCSI subsystem initialized
[   29.267065] libata version 2.20 loaded.
[   29.270764] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   29.270808] VP_IDE: chipset revision 6
[   29.270813] VP_IDE: not 100% native mode: will probe irqs later
[   29.270832] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[   29.270845]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda:DMA, hdb:pio
[   29.270867]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc:DMA, hdd:pio
[   29.270880] Probing IDE interface ide0...
[   29.303262] usbcore: registered new interface driver usbfs
[   29.303322] usbcore: registered new interface driver hub
[   29.303370] usbcore: registered new device driver usb
[   29.336331] USB Universal Host Controller Interface driver v3.0
[   29.708707] hda: MDT MD800AB-00DYA0, ATA DISK drive
[   30.382474] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.394255] Probing IDE interface ide1...
[   31.255902] hdc: HL-DT-ST GCE-8483B, ATAPI CD/DVD-ROM drive
[   31.928587] ide1 at 0x170-0x177,0x376 on irq 15
[   31.933348] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   31.933360] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   31.933372] PCI: VIA VLink IRQ fixup for 0000:00:11.2, from 6 to 11
[   31.933408] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   31.934147] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[   31.934194] uhci_hcd 0000:00:11.2: irq 11, io base 0x0000d000
[   31.935386] usb usb1: configuration #1 chosen from 1 choice
[   31.935843] hub 1-0:1.0: USB hub found
[   31.935872] hub 1-0:1.0: 2 ports detected
[   31.950192] hda: max request size: 512KiB
[   31.971768] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
[   31.973375] hda: cache flushes supported
[   31.973466]  hda: hda1 hda2 hda3 < hda5 >
[   32.023815] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   32.023834] Uniform CD-ROM driver Revision: 3.20
[   32.039635] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   32.039650] PCI: VIA VLink IRQ fixup for 0000:00:11.3, from 6 to 11
[   32.039684] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   32.039733] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[   32.039768] uhci_hcd 0000:00:11.3: irq 11, io base 0x0000b800
[   32.039954] usb usb2: configuration #1 chosen from 1 choice
[   32.040002] hub 2-0:1.0: USB hub found
[   32.040021] hub 2-0:1.0: 2 ports detected
[   32.143528] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   32.143543] PCI: VIA VLink IRQ fixup for 0000:00:11.4, from 6 to 11
[   32.143576] uhci_hcd 0000:00:11.4: UHCI Host Controller
[   32.143632] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 3
[   32.143668] uhci_hcd 0000:00:11.4: irq 11, io base 0x0000b400
[   32.143859] usb usb3: configuration #1 chosen from 1 choice
[   32.143912] hub 3-0:1.0: USB hub found
[   32.143931] hub 3-0:1.0: 2 ports detected
[   32.279218] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   32.390860] Attempting manual resume
[   32.390869] swsusp: Resume From Partition 3:5
[   32.390872] PM: Checking swsusp image.
[   32.399201] PM: Resume from disk failed.
[   32.464084] kjournald starting.  Commit interval 5 seconds
[   32.464111] EXT3-fs: mounted filesystem with ordered data mode.
[   32.469087] usb 1-1: configuration #1 chosen from 1 choice
[   33.110790] usbcore: registered new interface driver hiddev
[   33.143627] input: HID 04d9:0420 as /class/input/input2
[   33.143668] input: USB HID v1.10 Mouse [HID 04d9:0420] on usb-0000:00:11.2-1
[   33.143698] usbcore: registered new interface driver usbhid
[   33.143705] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   43.959262] eth0:  setting full-duplex.
[   45.306274] NET: Registered protocol family 17
[   47.194870] Linux agpgart interface v0.102 (c) Dave Jones
[   47.231820] irda_init()
[   47.231866] NET: Registered protocol family 23
[   47.308726] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.335746] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.821245] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   47.824413] agpgart: AGP aperture is 32M @ 0xfc000000
[   47.834442] parport: PnPBIOS parport detected.
[   47.834547] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   47.972662] input: PC Speaker as /class/input/input3
[   48.572453] nvidia: module license 'NVIDIA' taints kernel.
[   48.841496] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   48.841508] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   48.842294] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   49.247105] PCI: Enabling device 0000:00:0e.0 (0004 -> 0006)
[   49.247721] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   49.247728] PCI: setting IRQ 9 as level-triggered
[   49.247734] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   49.800800] gameport: CS4281 Gameport is pci0000:00:0e.0/gameport0, speed 1924kHz
[   50.026156] fuse init (API version 7.8)
[   50.077891] lp0: using parport0 (interrupt-driven).
[   50.142499] Adding 497972k swap on /dev/disk/by-uuid/7dc8998f-0ffc-4252-8576-25ece5e632ef.  Priority:-1 extents:1 across:497972k
[   50.297239] EXT3 FS on hda2, internal journal
[   50.603942] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   50.703638] NTFS volume version 3.1.
[   57.007913] Using specific hotkey driver
[   57.227722] ibm_acpi: ec object not found
[   57.395944] No dock devices found.
[   57.496253] input: Power Button (FF) as /class/input/input4
[   57.505171] ACPI: Power Button (FF) [PWRF]
[   57.562191] input: Power Button (CM) as /class/input/input5
[   57.562658] ACPI: Power Button (CM) [PWRB]
[   57.710907] pcc_acpi: loading...
[   64.562896] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   64.562929] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   64.562978] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   64.945932] ppdev: user-space parallel port driver
[   66.278628] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   66.278639] apm: overridden by ACPI.
[   66.540031] Bluetooth: Core ver 2.11
[   66.540156] NET: Registered protocol family 31
[   66.540161] Bluetooth: HCI device and connection manager initialized
[   66.540169] Bluetooth: HCI socket layer initialized
[   66.731889] Bluetooth: L2CAP ver 2.8
[   66.731900] Bluetooth: L2CAP socket layer initialized
[   66.795052] Bluetooth: RFCOMM socket layer initialized
[   66.795087] Bluetooth: RFCOMM TTY layer initialized
[   66.795091] Bluetooth: RFCOMM ver 1.8
[  138.921242] ISO 9660 Extensions: Microsoft Joliet Level 3
[  139.028339] ISOFS: changing to secondary root
[  204.362274] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  204.535597] usb 1-2: configuration #1 chosen from 1 choice
[  204.748824] usbcore: registered new interface driver libusual
[  204.774915] Initializing USB Mass Storage driver...
[  204.775116] scsi0 : SCSI emulation for USB Mass Storage devices
[  204.775238] usbcore: registered new interface driver usb-storage
[  204.775245] USB Mass Storage support registered.
[  204.775508] usb-storage: device found at 3
[  204.775512] usb-storage: waiting for device to settle before scanning
[  209.772585] usb-storage: device scan complete
[  209.775585] scsi 0:0:0:0: Direct-Access     Sony     Storage media    0100 PQ: 0 ANSI: 0 CCS
[  209.837483] SCSI device sda: 1981440 512-byte hdwr sectors (1014 MB)
[  209.840474] sda: Write Protect is off
[  209.840480] sda: Mode Sense: 43 00 00 00
[  209.840485] sda: assuming drive cache: write through
[  209.853465] SCSI device sda: 1981440 512-byte hdwr sectors (1014 MB)
[  209.856461] sda: Write Protect is off
[  209.856467] sda: Mode Sense: 43 00 00 00
[  209.856470] sda: assuming drive cache: write through
[  209.857418]  sda: sda1
[  209.927594] sd 0:0:0:0: Attached scsi removable disk sda
[  209.955947] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  334.339185] usb 1-2: USB disconnect, address 3

```

---

### Post by noob12 on 2007-09-18
Hmm.  Not seeing any problem there.

Try this, based on an old post on the forum:

```

sudo modprobe -r 3c59x
sudo modprobe 3c59x
sudo /etc/init.d/networking restart

```

By the way, you can/should comment out the sections for the interfaces in your **/etc/network/interfaces** file that don't exist: ath0, wlan0, eth1, eth2.  This will avoid the benign error messages you get about nonexistent interfaces (and make startup just a bit faster).

If the reloading doesn't work, try a manual configuration and see if you can ping your router.  If you don't know the network information to set manually, then posting the output of **ifconfig** and **route -n** from your other Ubuntu host on the net would make it possible to suggest one.

---

### Post by TedGarvin on 2007-09-18
When I try the modprobe commands I get *FATAL: module 3c95x not found*

When I add the static IP address and set the default gateway and subnet mask it does nothing.  I still can't ping the router.  My router is a Dlink di-624.  It sees the machine, but only identifies it by MAC address and not the host name as it does mine.  Could it be the fault of the router somehow?  It seems as if the machine was messed up, it wouldn't connect up when I connect it directly to the dsl modem.    

Are you sure I should have a listing in network tools for eth0 with no information and eth0(avahi) with a private ip address, MTU, active state and everything.  That seems wrong, but I have no idea what to do about it.  Or even if it is wrong.

**EDIT: I'm not sure what happened, but I now only have eth0 and eth0(avahi) is gone.**

---

### Post by noob12 on 2007-09-18
Eek.  Typo in my instructions.  It should be 3c59x not 3c95x.  I just went back and corrected the earlier posting in place.  Can you please retry that?

For manually configuring, use the **System | Administration | Network** menu.   The avahi virtual interface is normal.

---

### Post by TedGarvin on 2007-09-18
OK Now we're getting somewhere.  :)  After I enter

```
sudo modprobe -r 3c59x
sudo modprobe 3c59x
sudo /etc/init.d/networking restart
```

I can ping the router and yahoo.com with auto or manual dhcp.  Auto seems to be faster.  But when I restart the machine, it goes back to offline.  What do I do next?

---

### Post by noob12 on 2007-09-18
OK, so chalk one up for searching through old forum stuff.  I believe this is a bug in that driver and I urge you to file a bug on launchpad or attach yourself to an existing one.  

However, you don't want to hold your breath for the fix.  Instead I will suggest a couple of methods for you to have this executed automatically.  Will post that later today (Pacific Time).  Sorry I have to delay for now.

---

### Post by noob12 on 2007-09-18
Before we set you up with that as a workaround, I want to be sure it seems to be working stably once you reload the module (the sequence of commands I suggested earlier).

After you reload and things seem to be working, do you see any errors from eth0 in **tail /var/log/kern.log** ?   Try browsing, etc.

---

### Post by noob12 on 2007-09-18
Try this method of automating the commands; it is probably the cleanest/easiest.

Edit **/etc/network/interfaces**  (use, e.g. **sudo gedit /etc/network/interfaces**)

Edit the stanza for **eth0** so that it reads:

```

auto eth0
iface eth0 inet dhcp
pre-up modprobe -r 3c59x
pre-up modprobe 3c59x

```

These lines tell **ifup** to execute these commands just before bringing the interface up.  Hopefully this will work.

Reboot.  See if you have working networking.  

Hopefully you do.  But if not,  revert that (remove the **pre-up** lines from the **eth0** section in  **/etc/network/interfaces**), and I can provide you with an /etc/init.d script that will run just before networking starts.

---

### Post by TedGarvin on 2007-09-18
Thanks so much for all your help.  I did try browsing and chat features on it earlier, and they worked just fine.  I can't add the code to automate it till tomorrow.  I let you know what happens.  Whatever it does, your help has been invaluable.

---

### Post by TedGarvin on 2007-09-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/140813](https://bugs.launchpad.net/ubuntu/+bug/140813) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:guitar:  **IT WORKED!!** :guitar:  Thanks a lot.   I did go to launchpad, looked around and didn't see a problem quite like this and reported it as a new bug.

---

