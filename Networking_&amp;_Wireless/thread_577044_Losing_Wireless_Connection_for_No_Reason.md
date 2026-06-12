---
title: "Losing Wireless Connection for No Reason"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by KDayz on 2007-10-15
Hey,

I have a weird problem. When Iam in Windows my internet works fine. But when I am in Ubuntu my internet works fine and then suddenly drops and its difficult for me to reconnect. Network Manager doesnt even detect the internet connection doesnt work. The thing is that I dont even move my  computer so its same location as if i had windows which never dropped my connection. Can anyone help?

---

### Post by osx424242 on 2007-10-16
Your profile says that you are using Dapper 6.06, is that still the case?  Have you tried upgrading to Feisty (7.04) or even the Gutsy beta (7.10; will no longer be a beta later this week)?  Wireless networking in Feisty is supposed to be very easy (although I can't get mine to work), so that might help you.  If you are still using Dapper, is there a reason you can't (or won't) upgrade?

If you are already using Feisty, can you post:
 - basic info about your wireless network (WAP vs. WEP vs. no encryption; are you broadcasting your ESSID)?
 - the last dozen or so lines of output from 'dmesg'?
 - what is your wireless card (e.g. Intel ipw3945abg)?
 - the output from 'iwconfig'?

I probably won't be able to help you (as I said, I still haven't gotten mine working), but this is some of the information that will be needed in order to diagnose your problem.

If you get it fixed, please remember to post a reply with what you did to fix it, then close this thread as 'solved!'

---

### Post by KDayz on 2007-10-16
Hey. I am using Dapper. I am propaly going to upgrade to 7.10 when its released. I alread yordered the CD's.

My basic info is i am using WEP and I am broadcasting my ESSID which is 'Dayz'

last lines of dmsg
> [17179591.216000] usbcore: registered new driver usbhid
[17179591.216000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.244000] ts: Compaq touchscreen protocol output
[17179591.280000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x23a0b1, caps: 0xa04713/0x200000
[17179591.312000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179591.472000] input: PC Speaker as /class/input/input3
[17179591.480000] sdhci: ============== REGISTER DUMP ==============
[17179591.480000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179591.480000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179591.480000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179591.480000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179591.480000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179591.480000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179591.480000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179591.480000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179591.480000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179591.480000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179591.480000] sdhci: ===========================================
[17179591.536000] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179591.536000] Yenta: CardBus bridge found at 0000:03:04.0 [103c:3085]
[17179591.536000] Yenta: Enabling burst memory read transactions
[17179591.536000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179591.536000] Yenta: Routing CardBus interrupts to ISA
[17179591.536000] Yenta TI: socket 0000:03:04.0, mfunc 0x00aa1b22, devctl 0x64
[17179591.536000] mmc1: SDHCI at 0xb0208c00 irq 233 DMA
[17179591.552000] Real Time Clock Driver v1.12
[17179591.652000] 8139too Fast Ethernet driver 0.9.27
[17179591.676000] sdhci: ============== REGISTER DUMP ==============
[17179591.676000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179591.676000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179591.676000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179591.676000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179591.676000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179591.676000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179591.676000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179591.676000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179591.676000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179591.676000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179591.676000] sdhci: ===========================================
[17179591.728000] mmc2: SDHCI at 0xb0208800 irq 233 DMA
[17179591.816000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179591.816000] Socket status: 30000006
[17179591.816000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[17179591.816000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179591.816000] cs: IO port probe 0xa000-0xafff: clean.
[17179591.816000] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[17179591.816000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179592.320000] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 22 (level, low) -> IRQ 50
[17179592.320000] eth0: RealTek RTL8139 at 0xe09e6400, 00:0f:b0:78:0e:60, IRQ 50[17179592.320000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.336000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.444000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 209
[17179592.448000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179592.552000] MC'97 0 converters and GPIO not ready (0x1)
[17179592.704000] cs: IO port probe 0x100-0x3af: clean.
[17179592.708000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179592.708000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179592.708000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179592.708000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.008000] lp: driver loaded but no devices found
[17179593.048000] SCSI subsystem initialized
[17179593.060000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179593.060000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.060000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179593.120000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179593.212000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[17179593.212000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 177
[17179593.220000] ndiswrapper: using irq 177
[17179594.372000] wlan0: vendor: ''
[17179594.372000] wlan0: ndiswrapper ethernet device 00:14:a5:1d:58:49 using driver bcmwl5, 14E4:4318:103C:1355.5.conf
[17179594.372000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179594.408000] Adding 1060248k swap on /dev/hda5.  Priority:-1 extents:1 across:1060248k
[17179594.680000] EXT3 FS on hda2, internal journal
[17179594.872000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.872000] md: bitmap version 4.39
[17179595.340000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179595.964000] NET: Registered protocol family 17
[17179596.644000] cdrom: open failed.
[17179597.208000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179597.260000] NTFS volume version 3.1.
[17179598.276000] NET: Registered protocol family 10
[17179598.276000] lo: Disabled Privacy Extensions
[17179598.276000] IPv6 over IPv4 tunneling driver
[17179598.432000] ip_tables: (C) 2000-2002 Netfilter core team
[17179599.216000] ACPI: AC Adapter [ACAD] (on-line)
[17179599.332000] ACPI: Battery Slot [BAT1] (battery present)
[17179599.400000] ACPI: Power Button (FF) [PWRF]
[17179599.400000] ACPI: Lid Switch [LID]
[17179599.400000] ACPI: Power Button (CM) [PWRB]
[17179599.524000] ibm_acpi: ec object not found
[17179599.552000] pcc_acpi: loading...
[17179599.628000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179600.020000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179600.024000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[17179600.024000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[17179600.024000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179600.024000] cpu_init done, current fid 0xc, vid 0x6
[17179604.472000] eth0: link down
[17179604.472000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179608.284000] eth1: no IPv6 routers present
[17179608.640000] [drm] Initialized drm 1.0.1 20051102
[17179609.156000] ppdev: user-space parallel port driver
[17179609.636000] apm: BIOS not found.
[17179610.236000] Bluetooth: Core ver 2.8
[17179610.236000] NET: Registered protocol family 31
[17179610.236000] Bluetooth: HCI device and connection manager initialized
[17179610.236000] Bluetooth: HCI socket layer initialized
[17179610.248000] Bluetooth: L2CAP ver 2.8
[17179610.248000] Bluetooth: L2CAP socket layer initialized
[17179610.256000] Bluetooth: RFCOMM socket layer initialized
[17179610.256000] Bluetooth: RFCOMM TTY layer initialized
[17179610.256000] Bluetooth: RFCOMM ver 1.7


MY Wireless Card is BCM4318

Output from iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Dayz"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:03:1C:07
          Bit Rate:1 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-72 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


---

### Post by KDayz on 2007-10-17
bump!

---

### Post by KDayz on 2007-10-18
bump

---

### Post by Thebear on 2007-10-19
I had a similar problem and was advised to switch to KDE KUBUNTU, which solved the problem.  However I am more at hom with Gnome so I am planning to go back to Ubuntu Gutsy as soon as I can download the image file.

---

