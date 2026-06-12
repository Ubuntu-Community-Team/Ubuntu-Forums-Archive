---
title: "Broadband networking causing cupsys problem"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by entryname on 2008-05-26
Hi guys

Since getting Broadband, cupsys server will not start automatically, though I can start it manually. It seems to be complaining about some missing files and that it can't use IP 0.0.0.0. I have configured network settings as hub appears to want them, but still no luck. Suggestions?

Cupsys error log:

I [26/May/2008:14:27:41 +0100] Listening to 127.0.0.1:631 (IPv4)
I [26/May/2008:14:27:41 +0100] Listening to :::631 (IPv6)
I [26/May/2008:14:27:41 +0100] Listening to 0.0.0.0:631 (IPv4)
I [26/May/2008:14:27:41 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
E [26/May/2008:14:27:41 +0100] Creating missing directory "/var/run/cups/certs"
W [26/May/2008:14:27:41 +0100] Repairing ownership of "/var/run/cups/certs"
W [26/May/2008:14:27:41 +0100] Repairing access permissions of "/var/run/cups/certs"
I [26/May/2008:14:27:41 +0100] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [26/May/2008:14:27:41 +0100] Configured for up to 100 clients.
I [26/May/2008:14:27:41 +0100] Allowing up to 100 client connections per host.
I [26/May/2008:14:27:41 +0100] Using policy "default" as the default!
I [26/May/2008:14:27:41 +0100] Full reload is required.
I [26/May/2008:14:27:41 +0100] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [26/May/2008:14:27:42 +0100] Loading job cache file "/var/cache/cups/job.cache"...
I [26/May/2008:14:27:42 +0100] Full reload complete.
I [26/May/2008:14:27:42 +0100] Listening to 127.0.0.1:631 on fd 0...
I [26/May/2008:14:27:42 +0100] Listening to :::631 on fd 1...
E [26/May/2008:14:27:42 +0100] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
I [26/May/2008:14:27:46 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=5443)
I [26/May/2008:14:28:29 +0100] Scheduler shutting down normally.
I [26/May/2008:14:28:29 +0100] Saving remote.cache...
I [26/May/2008:14:46:14 +0100] Listening to 127.0.0.1:631 (IPv4)
I [26/May/2008:14:46:14 +0100] Listening to :::631 (IPv6)
I [26/May/2008:14:46:14 +0100] Listening to 0.0.0.0:631 (IPv4)
I [26/May/2008:14:46:14 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
E [26/May/2008:14:46:14 +0100] Creating missing directory "/var/run/cups/certs"
W [26/May/2008:14:46:14 +0100] Repairing ownership of "/var/run/cups/certs"
W [26/May/2008:14:46:14 +0100] Repairing access permissions of "/var/run/cups/certs"
I [26/May/2008:14:46:14 +0100] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [26/May/2008:14:46:14 +0100] Configured for up to 100 clients.
I [26/May/2008:14:46:14 +0100] Allowing up to 100 client connections per host.
I [26/May/2008:14:46:14 +0100] Using policy "default" as the default!
I [26/May/2008:14:46:14 +0100] Full reload is required.
I [26/May/2008:14:46:14 +0100] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [26/May/2008:14:46:14 +0100] Loading job cache file "/var/cache/cups/job.cache"...
I [26/May/2008:14:46:14 +0100] Full reload complete.
I [26/May/2008:14:46:14 +0100] Listening to 127.0.0.1:631 on fd 0...
I [26/May/2008:14:46:14 +0100] Listening to :::631 on fd 1...
E [26/May/2008:14:46:14 +0100] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
I [26/May/2008:14:50:24 +0100] Scheduler shutting down normally.
I [26/May/2008:14:50:24 +0100] Saving remote.cache...
I [26/May/2008:21:26:40 +0100] Listening to 127.0.0.1:631 (IPv4)
I [26/May/2008:21:26:40 +0100] Listening to :::631 (IPv6)
I [26/May/2008:21:26:40 +0100] Listening to 0.0.0.0:631 (IPv4)
I [26/May/2008:21:26:40 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
E [26/May/2008:21:26:40 +0100] Creating missing directory "/var/run/cups/certs"
W [26/May/2008:21:26:40 +0100] Repairing ownership of "/var/run/cups/certs"
W [26/May/2008:21:26:40 +0100] Repairing access permissions of "/var/run/cups/certs"
I [26/May/2008:21:26:40 +0100] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [26/May/2008:21:26:40 +0100] Configured for up to 100 clients.
I [26/May/2008:21:26:40 +0100] Allowing up to 100 client connections per host.
I [26/May/2008:21:26:40 +0100] Using policy "default" as the default!
I [26/May/2008:21:26:40 +0100] Full reload is required.
I [26/May/2008:21:26:40 +0100] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [26/May/2008:21:26:41 +0100] Loading job cache file "/var/cache/cups/job.cache"...
I [26/May/2008:21:26:41 +0100] Full reload complete.
I [26/May/2008:21:26:41 +0100] Listening to 127.0.0.1:631 on fd 0...
I [26/May/2008:21:26:41 +0100] Listening to :::631 on fd 1...
E [26/May/2008:21:26:41 +0100] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
I [26/May/2008:21:30:38 +0100] Adding start banner page "none" to job 40.
I [26/May/2008:21:30:38 +0100] Adding end banner page "none" to job 40.
I [26/May/2008:21:30:38 +0100] Job 40 queued on "DeskJet-710C" by "michael".
I [26/May/2008:21:30:38 +0100] Started filter /usr/lib/cups/filter/pstops (PID 5140) for job 40.
I [26/May/2008:21:30:38 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 5141) for job 40.
I [26/May/2008:21:30:38 +0100] Started backend /usr/lib/cups/backend/hp (PID 5142) for job 40.
I [26/May/2008:21:32:53 +0100] Adding start banner page "none" to job 41.
I [26/May/2008:21:32:53 +0100] Adding end banner page "none" to job 41.
I [26/May/2008:21:32:53 +0100] Job 41 queued on "DeskJet-710C" by "michael".
I [26/May/2008:21:33:46 +0100] Started filter /usr/lib/cups/filter/pstops (PID 5219) for job 41.
I [26/May/2008:21:33:46 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 5220) for job 41.
I [26/May/2008:21:33:46 +0100] Started backend /usr/lib/cups/backend/hp (PID 5221) for job 41.
I [26/May/2008:21:41:45 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=5383)
I [26/May/2008:21:42:08 +0100] Started "/usr/lib/cups/cgi-bin/help.cgi" (pid=5387)
I [26/May/2008:21:42:18 +0100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=5388)
I [26/May/2008:21:42:19 +0100] Started "/usr/lib/cups/daemon/cups-deviced" (pid=5389)

---

### Post by superprash2003 on 2008-05-26
could you post your ifconfig output

---

### Post by entryname on 2008-05-27
Hi again... ifconfig as requested

michael@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:70:11:E3:54
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fe11:e354/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:387597 (378.5 KiB)  TX bytes:34048 (33.2 KiB)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39537 (38.6 KiB)  TX bytes:39537 (38.6 KiB)

---

### Post by superprash2003 on 2008-05-27
go to system->administration->network and go to Hosts and under ip address. do you see 0.0.0.0?

---

### Post by entryname on 2008-06-05
Hi guys

actually it looks a bit weird on the hosts bit would appreciate some advice on what it ought to say.

It actually says:
ff00::0 alias ip60-mcastprefix
127.0.0.1 alias localhost.localdomain localhost ubuntu
fe00::0 alias ip6-localnet
ff02::2 alias ip6-allrouters
ff02::1 alias ip6-allnodes
::1 alias ip6-localhost ip6-loopback [suspect this is the problem?? deleting]
ff02::3 alias ip6-allhosts

Should ANY of this be there apart from 127.0.0.1? what is it all for??

Michael R

---

### Post by dmizer on 2008-06-05
don't worry about the 0.0.0.0 thing.  my working cups server says the same thing.

try disabling ipv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

are there any cups errors in dmesg?

---

### Post by entryname on 2008-06-05
Hi guys

Well after deleting 0.0.0.0 from networking the CUPS error log on the next restart went

I [05/Jun/2008:17:19:30 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
E [05/Jun/2008:17:19:30 +0100] Creating missing directory "/var/run/cups/certs"
W [05/Jun/2008:17:19:30 +0100] Repairing ownership of "/var/run/cups/certs"
W [05/Jun/2008:17:19:30 +0100] Repairing access permissions of "/var/run/cups/certs"
I [05/Jun/2008:17:19:30 +0100] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [05/Jun/2008:17:19:30 +0100] Configured for up to 100 clients.
I [05/Jun/2008:17:19:30 +0100] Allowing up to 100 client connections per host.
I [05/Jun/2008:17:19:30 +0100] Using policy "default" as the default!
I [05/Jun/2008:17:19:30 +0100] Full reload is required.
I [05/Jun/2008:17:19:31 +0100] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [05/Jun/2008:17:19:31 +0100] Loading job cache file "/var/cache/cups/job.cache"...
I [05/Jun/2008:17:19:31 +0100] Full reload complete.
I [05/Jun/2008:17:19:31 +0100] Listening to 127.0.0.1:631 on fd 0...
I [05/Jun/2008:17:19:31 +0100] Listening to :::631 on fd 1...
E [05/Jun/2008:17:19:31 +0100] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
I [05/Jun/2008:17:19:53 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=4969)
I [05/Jun/2008:17:19:58 +0100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=4970)
I [05/Jun/2008:17:20:00 +0100] Started "/usr/lib/cups/daemon/cups-deviced" (pid=4971)

dmesg went:

michael@ubuntu:~$ sudo dmesg
[17179569.184000] Linux version 2.6.15-51-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Feb 12 16:52:52 UTC 2008
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000c000000 (usable)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 192MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 49152
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 45056 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.1 present.
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash vga=791 acpi=off
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01181000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 400.983 MHz processor.
[   55.663799] Using tsc for high-res timesource
[   55.663908] Console: colour dummy device 80x25
[   55.664888] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   55.665713] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   55.695846] Memory: 184372k/196608k available (1977k kernel code, 11704k reserved, 605k data, 288k init, 0k highmem)
[   55.695865] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   55.773685] Calibrating delay using timer specific routine.. 803.07 BogoMIPS (lpj=1606148)
[   55.773820] Security Framework v1.0.0 initialized
[   55.773855] SELinux:  Disabled at boot.
[   55.773916] Mount-cache hash table entries: 512
[   55.774287] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   55.774320] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   55.774356] CPU: L1 I cache: 16K, L1 D cache: 16K
[   55.774369] CPU: L2 cache: 512K
[   55.774381] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   55.774451] mtrr: v2.0 (20020519)
[   55.774470] CPU: Intel Pentium II (Deschutes) stepping 02
[   55.774487] Enabling fast FPU save and restore... done.
[   55.774503] Checking 'hlt' instruction... OK.
[   55.790265] checking if image is initramfs... it is
[   59.640038] Freeing initrd memory: 6669k freed
[   59.687411] NET: Registered protocol family 16
[   59.687548] EISA bus registered
[   59.702911] PCI: PCI BIOS revision 2.10 entry at 0xfb390, last bus=1
[   59.702939] PCI: Using configuration type 1
[   59.704572] ACPI: Subsystem revision 20051216
[   59.704584] ACPI: Interpreter disabled.
[   59.704597] Linux Plug and Play Support v0.97 (c) Adam Belay
[   59.704627] pnp: PnP ACPI: disabled
[   59.704644] PnPBIOS: Scanning system for PnP BIOS support...
[   59.705210] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbf80
[   59.705234] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbfa8, dseg 0xf0000[   59.710335] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   59.710404] PCI: Probing PCI hardware
[   59.710421] PCI: Probing PCI hardware (bus 00)
[   59.711009] PCI quirk: region 4000-403f claimed by PIIX4 ACPI
[   59.711026] PCI quirk: region 5000-500f claimed by PIIX4 SMB
[   59.711569] Boot video device is 0000:01:00.0
[   59.714137] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   59.808557] pnp: 00:0b: ioport range 0x208-0x20f has been reserved
[   59.809682] PCI: Bridge: 0000:00:01.0
[   59.809697]   IO window: d000-dfff
[   59.809713]   MEM window: e8000000-ebffffff
[   59.809727]   PREFETCH window: 10000000-100fffff
[   59.812301] audit: initializing netlink socket (disabled)
[   59.812340] audit(1212682580.460:1): initialized
[   59.812761] VFS: Disk quotas dquot_6.5.1
[   59.812863] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   59.813089] Initializing Cryptographic API
[   59.813110] io scheduler noop registered
[   59.813147] io scheduler anticipatory registered
[   59.813169] io scheduler deadline registered
[   59.813212] io scheduler cfq registered
[   59.813227] Limiting direct PCI/PCI transfers.
[   59.813918] isapnp: Scanning for PnP cards...
[   59.924564] isapnp: Card '5614Jx3(G) Internal Modem'
[   59.924580] isapnp: 1 Plug & Play card detected total
[   60.016174] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   60.018695] serio: i8042 AUX port at 0x60,0x64 irq 12
[   60.018998] serio: i8042 KBD port at 0x60,0x64 irq 1
[   60.019209] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   60.019529] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   60.029924] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   60.032714] pnp: Device 01:01.00 activated.
[   60.033086] 01:01.00: ttyS1 at I/O 0x2f8 (irq = 5) is a 16550A
[   60.035727] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   60.036009] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   60.036027] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   60.036587] mice: PS/2 mouse device common for all mice
[   60.037550] EISA: Probing bus 0 at eisa.0
[   60.037594] Cannot allocate resource for EISA slot 4
[   60.037606] Cannot allocate resource for EISA slot 5
[   60.037637] EISA: Detected 0 cards.
[   60.037815] NET: Registered protocol family 2
[   60.069460] input: AT Translated Set 2 keyboard as /class/input/input0
[   60.072147] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   60.072691] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[   60.072871] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   60.073056] TCP: Hash tables configured (established 8192 bind 8192)
[   60.073069] TCP reno registered
[   60.073400] TCP bic registered
[   60.073431] NET: Registered protocol family 1
[   60.073457] NET: Registered protocol family 8
[   60.073467] NET: Registered protocol family 20
[   60.073554] Using IPI Shortcut mode
[   60.073693] Freeing unused kernel memory: 288k freed
[   60.315883] vesafb: framebuffer at 0xe8000000, mapped to 0xcc880000, using 3072k, total 8192k
[   60.315905] vesafb: mode is 1024x768x16, linelength=2048, pages=4
[   60.315919] vesafb: protected mode interface info at c000:4785
[   60.315929] vesafb: scrolling: redraw
[   60.315943] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   60.315958] vesafb: Mode is VGA compatible
[   60.392599] Console: switching to colour frame buffer device 128x48
[   60.392622] fb0: VESA VGA frame buffer device
[   61.522066] Capability LSM initialized
[   63.475026] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   63.475075] PIIX4: chipset revision 1
[   63.475087] PIIX4: not 100% native mode: will probe irqs later
[   63.475114]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
[   63.475161]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[   63.475195] Probing IDE interface ide0...
[   63.762554] hda: WDC AC310200R, ATA DISK drive
[   64.042430] hdb: WDC WD153AA-00BAA0, ATA DISK drive
[   64.106669] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   64.107666] Probing IDE interface ide1...
[   65.010039] hdc: HITACHI DVD-ROM GD-2500, ATAPI CD/DVD-ROM drive
[   65.793806] hdd: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
[   65.908631] ide1 at 0x170-0x177,0x376 on irq 15
[   65.941153] hda: max request size: 128KiB
[   65.941174] hda: 20044080 sectors (10262 MB) w/512KiB Cache, CHS=19885/16/63, UDMA(33)
[   65.941197] hda: cache flushes not supported
[   65.941904]  hda: hda1 hda2 < hda5 >
[   66.033652] hdb: max request size: 128KiB
[   66.054265] hdb: 30064608 sectors (15393 MB) w/2048KiB Cache, CHS=29826/16/63, UDMA(33)
[   66.054292] hdb: cache flushes not supported
[   66.054761]  hdb: hdb1
[   66.187994] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[   66.188027] Uniform CD-ROM driver Revision: 3.20
[   67.350660] usbcore: registered new driver usbfs
[   67.351699] usbcore: registered new driver hub
[   67.361380] USB Universal Host Controller Interface driver v2.3
[   67.362525] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   67.363763] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   67.363798] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000e000
[   67.365064] hub 1-0:1.0: USB hub found
[   67.365118] hub 1-0:1.0: 2 ports detected
[   67.632937] Attempting manual resume
[   67.706710] EXT3-fs: mounted filesystem with ordered data mode.
[   67.708839] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   67.730162] kjournald starting.  Commit interval 5 seconds
[   88.802526] NET: Registered protocol family 10
[   88.802986] lo: Disabled Privacy Extensions
[   88.803307] IPv6 over IPv4 tunneling driver
[   97.441085] Linux agpgart interface v0.101 (c) Dave Jones
[   97.454048] agpgart: Detected an Intel 440BX Chipset.
[   98.250517] agpgart: AGP aperture is 256M @ 0xd0000000
[   98.397347] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   98.435669] input: PC Speaker as /class/input/input1
[   98.495442] Linux Tulip driver version 1.1.13 (December 15, 2004)
[   98.495614] PCI: Found IRQ 10 for device 0000:00:0e.0
[   98.496206] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
[   98.501028] eth0: ADMtek Comet rev 17 at 0001e400, 00:1A:70:11:E3:54, IRQ 10.[   98.549235] rt61: module license 'unspecified' taints kernel.
[   98.554981] PCI: Found IRQ 3 for device 0000:00:10.0
[   98.555039] RT61: Vendor = 0x1814, Product = 0x0301
[  100.007581] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[  100.204589] Real Time Clock Driver v1.12
[  100.293854] SCSI subsystem initialized
[  100.328898] Initializing USB Mass Storage driver...
[  100.334493] scsi0 : SCSI emulation for USB Mass Storage devices
[  100.340355] usb-storage: device found at 2
[  100.340368] usb-storage: waiting for device to settle before scanning
[  100.340403] usbcore: registered new driver usb-storage
[  100.340415] USB Mass Storage support registered.
[  100.661506] ide-floppy driver 0.99.newide
[  100.710158] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  100.739911] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  100.908435] hdd: 98304kB, 196608 blocks, 512 sector size
[  100.963024] hdd: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[  101.167524]  hdd: hdd4
[  101.768863] ts: Compaq touchscreen protocol output
[  102.912885] PCI: Found IRQ 9 for device 0000:00:12.0
[  103.079108]  hdd: hdd4
[  103.313860] Floppy drive(s): fd0 is 1.44M
[  103.333964] FDC 0 is a post-1991 82077
[  103.422913]  hdd:<6>parport: PnPBIOS parport detected.
[  103.460908] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  103.492881]  hdd4
[  105.346969]   Vendor: CD-RW     Model: CDR-6S52          Rev: 6SG4
[  105.347020]   Type:   CD-ROM                             ANSI SCSI revision: 00
[  105.351799] usb-storage: device scan complete
[  105.546211] lp0: using parport0 (interrupt-driven).
[  105.570746] sr0: scsi3-mmc drive: 59x/52x writer cd/rw xa/form2 cdda tray
[  105.572246] sr 0:0:0:0: Attached scsi CD-ROM sr0
[  105.634705] sr 0:0:0:0: Attached scsi generic sg0 type 5
[  106.265601] Adding 369452k swap on /dev/hda5.  Priority:-1 extents:1 across:369452k
[  106.411842] EXT3 FS on hda1, internal journal
[  106.958620] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  106.958638] md: bitmap version 4.39
[  107.302396] 0000:00:0e.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  107.302426] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
[  107.965472]  hdd: hdd4
[  108.476998]  hdd: hdd4
[  109.284116] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  110.007015] cdrom: open failed.
[  110.356221]  hdd: hdd4
[  110.807971]  hdd: hdd4
[  111.743037] cdrom: open failed.
[  111.995501]  hdd: hdd4
[  114.337623] eth0: no IPv6 routers present
[  115.107683] cdrom: open failed.
[  139.105023] kjournald starting.  Commit interval 5 seconds
[  139.105257] EXT3 FS on hdb1, internal journal
[  139.105279] EXT3-fs: mounted filesystem with ordered data mode.
[  149.034433] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[  167.909780] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  169.338245] ip_tables: (C) 2000-2002 Netfilter core team
[  169.523246] Netfilter messages via NETLINK v0.30.
[  169.696904] ip_conntrack version 2.4 (1536 buckets, 12288 max) - 232 bytes per conntrack
[  170.852259] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  170.852290] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  170.852304] ide: failed opcode was: 0xec
[  171.109848] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  171.109879] hdd: drive_cmd: error=0x04 { AbortedCommand }
[  171.109893] ide: failed opcode was: 0xec
[  171.392814] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  171.392843] hdd: drive_cmd: error=0x04 { AbortedCommand }
[  171.392857] ide: failed opcode was: 0xe3
[  252.240530] ppdev: user-space parallel port driver
[  285.841896] ppdev0: registered pardevice
[  285.891686] ppdev0: unregistered pardevice
michael@ubuntu:~$

I don't know where that gets us other than the comment that no IPv6 routers were found which appears to mean I can bin all IP6 aliases. Haven't at the moment done that (should I?).

BUT...
michael@ubuntu:~$ ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::21a:70ff:fe11:e354/64 scope link
michael@ubuntu:~$

however, adding blacklist IPv6 to blacklist anyway and rebooting... wish me luck... :-?

---

### Post by entryname on 2008-06-05
Nope no luck CUPS still didn't start. Still have network so it doesn't appear to have done any actual harm.

CUPS error log:

I [05/Jun/2008:17:45:38 +0100] Listening to 127.0.0.1:631 (IPv4)
I [05/Jun/2008:17:45:38 +0100] Listening to 0.0.0.0:631 (IPv4)
I [05/Jun/2008:17:45:38 +0100] Listening to :::631 (IPv6)
I [05/Jun/2008:17:45:38 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
E [05/Jun/2008:17:45:38 +0100] Creating missing directory "/var/run/cups/certs"
W [05/Jun/2008:17:45:38 +0100] Repairing ownership of "/var/run/cups/certs"
W [05/Jun/2008:17:45:38 +0100] Repairing access permissions of "/var/run/cups/certs"
I [05/Jun/2008:17:45:38 +0100] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [05/Jun/2008:17:45:38 +0100] Configured for up to 100 clients.
I [05/Jun/2008:17:45:38 +0100] Allowing up to 100 client connections per host.
I [05/Jun/2008:17:45:38 +0100] Using policy "default" as the default!
I [05/Jun/2008:17:45:38 +0100] Full reload is required.
I [05/Jun/2008:17:45:38 +0100] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [05/Jun/2008:17:45:39 +0100] Loading job cache file "/var/cache/cups/job.cache"...
I [05/Jun/2008:17:45:39 +0100] Full reload complete.
I [05/Jun/2008:17:45:39 +0100] Listening to 127.0.0.1:631 on fd 0...
E [05/Jun/2008:17:45:39 +0100] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
E [05/Jun/2008:17:45:39 +0100] Unable to open listen socket for address :::631 - Address family not supported by protocol.
I [05/Jun/2008:17:45:42 +0100] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=5140)
I [05/Jun/2008:17:45:47 +0100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=5141)
I [05/Jun/2008:17:45:49 +0100] Started "/usr/lib/cups/daemon/cups-deviced" (pid=5142)

dmesg:

michael@ubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.15-51-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Feb 12 16:52:52 UTC 2008
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000c000000 (usable)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 192MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 49152
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 45056 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.1 present.
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash vga=791 acpi=off
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01181000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 400.990 MHz processor.
[   55.369922] Using tsc for high-res timesource
[   55.370031] Console: colour dummy device 80x25
[   55.371005] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   55.371849] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   55.401962] Memory: 184372k/196608k available (1977k kernel code, 11704k reserved, 605k data, 288k init, 0k highmem)
[   55.401981] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   55.479487] Calibrating delay using timer specific routine.. 803.04 BogoMIPS (lpj=1606094)
[   55.479622] Security Framework v1.0.0 initialized
[   55.479657] SELinux:  Disabled at boot.
[   55.479717] Mount-cache hash table entries: 512
[   55.480089] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   55.480122] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   55.480158] CPU: L1 I cache: 16K, L1 D cache: 16K
[   55.480170] CPU: L2 cache: 512K
[   55.480182] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   55.480252] mtrr: v2.0 (20020519)
[   55.480271] CPU: Intel Pentium II (Deschutes) stepping 02
[   55.480289] Enabling fast FPU save and restore... done.
[   55.480304] Checking 'hlt' instruction... OK.
[   55.496066] checking if image is initramfs... it is
[   59.345786] Freeing initrd memory: 6669k freed
[   59.393167] NET: Registered protocol family 16
[   59.393303] EISA bus registered
[   59.408668] PCI: PCI BIOS revision 2.10 entry at 0xfb390, last bus=1
[   59.408696] PCI: Using configuration type 1
[   59.410330] ACPI: Subsystem revision 20051216
[   59.410342] ACPI: Interpreter disabled.
[   59.410355] Linux Plug and Play Support v0.97 (c) Adam Belay
[   59.410385] pnp: PnP ACPI: disabled
[   59.410402] PnPBIOS: Scanning system for PnP BIOS support...
[   59.410968] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbf80
[   59.410992] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbfa8, dseg 0xf0000[   59.416092] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   59.416161] PCI: Probing PCI hardware
[   59.416178] PCI: Probing PCI hardware (bus 00)
[   59.416765] PCI quirk: region 4000-403f claimed by PIIX4 ACPI
[   59.416783] PCI quirk: region 5000-500f claimed by PIIX4 SMB
[   59.417327] Boot video device is 0000:01:00.0
[   59.419892] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   59.514316] pnp: 00:0b: ioport range 0x208-0x20f has been reserved
[   59.515441] PCI: Bridge: 0000:00:01.0
[   59.515456]   IO window: d000-dfff
[   59.515471]   MEM window: e8000000-ebffffff
[   59.515485]   PREFETCH window: 10000000-100fffff
[   59.518075] audit: initializing netlink socket (disabled)
[   59.518114] audit(1212684024.164:1): initialized
[   59.518533] VFS: Disk quotas dquot_6.5.1
[   59.518637] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   59.518863] Initializing Cryptographic API
[   59.518883] io scheduler noop registered
[   59.518921] io scheduler anticipatory registered
[   59.518943] io scheduler deadline registered
[   59.518986] io scheduler cfq registered
[   59.519000] Limiting direct PCI/PCI transfers.
[   59.519714] isapnp: Scanning for PnP cards...
[   59.630339] isapnp: Card '5614Jx3(G) Internal Modem'
[   59.630355] isapnp: 1 Plug & Play card detected total
[   59.721444] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   59.724100] serio: i8042 AUX port at 0x60,0x64 irq 12
[   59.724403] serio: i8042 KBD port at 0x60,0x64 irq 1
[   59.724615] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   59.724933] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   59.735300] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   59.738076] pnp: Device 01:01.00 activated.
[   59.738449] 01:01.00: ttyS1 at I/O 0x2f8 (irq = 5) is a 16550A
[   59.741092] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   59.741338] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   59.741357] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   59.741951] mice: PS/2 mouse device common for all mice
[   59.742915] EISA: Probing bus 0 at eisa.0
[   59.742959] Cannot allocate resource for EISA slot 4
[   59.742971] Cannot allocate resource for EISA slot 5
[   59.743002] EISA: Detected 0 cards.
[   59.743180] NET: Registered protocol family 2
[   59.774956] input: AT Translated Set 2 keyboard as /class/input/input0
[   59.777948] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   59.778493] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[   59.778674] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   59.778860] TCP: Hash tables configured (established 8192 bind 8192)
[   59.778872] TCP reno registered
[   59.779203] TCP bic registered
[   59.779235] NET: Registered protocol family 1
[   59.779260] NET: Registered protocol family 8
[   59.779270] NET: Registered protocol family 20
[   59.779356] Using IPI Shortcut mode
[   59.779496] Freeing unused kernel memory: 288k freed
[   60.022112] vesafb: framebuffer at 0xe8000000, mapped to 0xcc880000, using 3072k, total 8192k
[   60.022135] vesafb: mode is 1024x768x16, linelength=2048, pages=4
[   60.022148] vesafb: protected mode interface info at c000:4785
[   60.022158] vesafb: scrolling: redraw
[   60.022172] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   60.022186] vesafb: Mode is VGA compatible
[   60.098825] Console: switching to colour frame buffer device 128x48
[   60.098848] fb0: VESA VGA frame buffer device
[   61.231983] Capability LSM initialized
[   63.178732] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   63.178781] PIIX4: chipset revision 1
[   63.178792] PIIX4: not 100% native mode: will probe irqs later
[   63.178819]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
[   63.178864]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[   63.178897] Probing IDE interface ide0...
[   63.464354] hda: WDC AC310200R, ATA DISK drive
[   63.744235] hdb: WDC WD153AA-00BAA0, ATA DISK drive
[   63.808474] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   63.809465] Probing IDE interface ide1...
[   64.711840] hdc: HITACHI DVD-ROM GD-2500, ATAPI CD/DVD-ROM drive
[   65.495609] hdd: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
[   65.610429] ide1 at 0x170-0x177,0x376 on irq 15
[   65.642885] hda: max request size: 128KiB
[   65.642906] hda: 20044080 sectors (10262 MB) w/512KiB Cache, CHS=19885/16/63, UDMA(33)
[   65.642930] hda: cache flushes not supported
[   65.643627]  hda: hda1 hda2 < hda5 >
[   65.733810] hdb: max request size: 128KiB
[   65.751149] hdb: 30064608 sectors (15393 MB) w/2048KiB Cache, CHS=29826/16/63, UDMA(33)
[   65.751177] hdb: cache flushes not supported
[   65.751324]  hdb: hdb1
[   65.886174] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[   65.886208] Uniform CD-ROM driver Revision: 3.20
[   67.048855] usbcore: registered new driver usbfs
[   67.049886] usbcore: registered new driver hub
[   67.059576] USB Universal Host Controller Interface driver v2.3
[   67.060745] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   67.061995] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   67.062030] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000e000
[   67.063270] hub 1-0:1.0: USB hub found
[   67.063333] hub 1-0:1.0: 2 ports detected
[   67.389009] Attempting manual resume
[   67.406674] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   67.461884] EXT3-fs: mounted filesystem with ordered data mode.
[   67.482607] kjournald starting.  Commit interval 5 seconds
[   97.051087] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   97.077067] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   97.315001] Linux Tulip driver version 1.1.13 (December 15, 2004)
[   97.315178] PCI: Found IRQ 10 for device 0000:00:0e.0
[   97.315703] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[   97.320516] eth0: ADMtek Comet rev 17 at 0001e400, 00:1A:70:11:E3:54, IRQ 10.[   97.460534] Linux agpgart interface v0.101 (c) Dave Jones
[   97.499994] agpgart: Detected an Intel 440BX Chipset.
[   97.528778] agpgart: AGP aperture is 256M @ 0xd0000000
[   98.364139] ide-floppy driver 0.99.newide
[   98.510651] hdd: 98304kB, 196608 blocks, 512 sector size
[   98.559211] hdd: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[   98.754269]  hdd:<4>rt61: module license 'unspecified' taints kernel.
[   99.625473] PCI: Found IRQ 3 for device 0000:00:10.0
[   99.625536] RT61: Vendor = 0x1814, Product = 0x0301
[   99.661693] input: PC Speaker as /class/input/input1
[  100.506387] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[  101.698779] SCSI subsystem initialized
[  101.702808]  hdd4
[  101.751103] Floppy drive(s): fd0 is 1.44M
[  101.769314] parport: PnPBIOS parport detected.
[  101.769366] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  101.776704] FDC 0 is a post-1991 82077
[  102.116601] Real Time Clock Driver v1.12
[  102.130725] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[  102.168428] Initializing USB Mass Storage driver...
[  102.168836] scsi0 : SCSI emulation for USB Mass Storage devices
[  102.169088] usb-storage: device found at 2
[  102.169100] usb-storage: waiting for device to settle before scanning
[  102.169131] usbcore: registered new driver usb-storage
[  102.169143] USB Mass Storage support registered.
[  102.364851] ts: Compaq touchscreen protocol output
[  102.463990] PCI: Found IRQ 9 for device 0000:00:12.0
[  102.472595]  hdd: hdd4
[  102.812908]  hdd: hdd4
[  104.877778] lp0: using parport0 (interrupt-driven).
[  105.316403] Adding 369452k swap on /dev/hda5.  Priority:-1 extents:1 across:369452k
[  105.468898] EXT3 FS on hda1, internal journal
[  105.480792] 0000:00:0e.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  105.480821] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
[  106.004565] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  106.004584] md: bitmap version 4.39
[  107.023523]  hdd: hdd4
[  107.174843]   Vendor: CD-RW     Model: CDR-6S52          Rev: 6SG4
[  107.174893]   Type:   CD-ROM                             ANSI SCSI revision: 00
[  107.179888] usb-storage: device scan complete
[  107.489556] sr0: scsi3-mmc drive: 59x/52x writer cd/rw xa/form2 cdda tray
[  107.490898] sr 0:0:0:0: Attached scsi CD-ROM sr0
[  107.556629] sr 0:0:0:0: Attached scsi generic sg0 type 5
[  107.686954]  hdd: hdd4
[  108.562534] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  109.252035] cdrom: open failed.
[  109.602176]  hdd: hdd4
[  110.057978]  hdd: hdd4
[  110.998753] cdrom: open failed.
[  111.249500]  hdd: hdd4
[  114.302219] cdrom: open failed.
[  117.364362] kjournald starting.  Commit interval 5 seconds
[  117.364739] EXT3 FS on hdb1, internal journal
[  117.364763] EXT3-fs: mounted filesystem with ordered data mode.
[  124.192088] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[  142.173784] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  143.374197] ip_tables: (C) 2000-2002 Netfilter core team
[  143.673003] Netfilter messages via NETLINK v0.30.
[  143.746800] ip_conntrack version 2.4 (1536 buckets, 12288 max) - 232 bytes per conntrack
[  145.255424] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  145.255456] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  145.255470] ide: failed opcode was: 0xec
[  145.406691] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  145.406725] hdd: drive_cmd: error=0x04 { AbortedCommand }
[  145.406739] ide: failed opcode was: 0xec
[  145.430272] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  145.430304] hdd: drive_cmd: error=0x04 { AbortedCommand }
[  145.430318] ide: failed opcode was: 0xe3
[  375.464073] ppdev: user-space parallel port driver
[  391.279848] ppdev0: registered pardevice
[  391.326060] ppdev0: unregistered pardevice
michael@ubuntu:~$

The only thing I notice there is that the comment about IPv6 has gone, and that there is a complaint telling me to fix the driver for ra0 (which I don't know how to do, although it may explain why ra0 won't work).

So we're still at square one. I can start CUPS using a password, but I want it to start when the system starts. Suggestions?? :confused:

---

