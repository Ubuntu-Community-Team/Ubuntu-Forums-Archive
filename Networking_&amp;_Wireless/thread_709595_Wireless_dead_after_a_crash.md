---
title: "Wireless dead after a crash"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by heyster on 2008-02-27
Every 2 weeks my Lenovo laptop with Broadcom wireless hangs. Sometimes while using Skype, sometimes while serving the net.
I have no idea why the laptop with Gibson does not respond anymore.
After a reboot everything mostly works fine.
But every second crash, the wireless is not working anymore. It does not find any wirelesss network. I can only use the wired network.
Does anyone have a clue what is going on? 
It would save my weekend when someone can tell me what I need to check/change ;)

I am prepared to post any log file you need.

Regards

Jan

---

### Post by tgalati4 on 2008-02-27
You may have a wireless dsp hardware failure.  Sometimes wireless chips heat up and act wonky.  Because they are attached to the system bus, they tend to cause hard crashes.  I'm assuming your wireless is built-in and not a pcmcia card.  

In a terminal, post the output of:
```

dmesg | tail -100
```

Only include anything related to networking or wireless.  

Get familiar with the command iwconfig:
```

man iwconfig
```

and 

Install wifi-radar:

```
sudo apt-get install wifi-radar
```

Monitor your signal levels.  Sometimes weak wireless signals can cause slow system response that you may interpret as freezes.

Add a cpu monitor to your panel.  Right click on your Gnome panel, Add, CPU Monitor.  This way you can see if your computer freezes, the monitor will stop updating.  If the computer is busy, then it will show 100% use.

Sometimes it helps to remove the battery from the laptop (while powered off).  The digital tuner settings in the wireless chipset need resetting from time to time.

---

### Post by heyster on 2008-02-27
Here we go:

Dmesg makes:

[    6.884000] ACPI: PCI Interrupt 0000:05:09.1[B] -> GSI 19 (level, low) -> IRQ 20
[    6.932000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d2016000-d20167ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.952000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.952000] sd 0:0:0:0: [sda] Write Protect is off
[    6.952000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.952000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.952000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.952000] sd 0:0:0:0: [sda] Write Protect is off
[    6.952000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.952000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.952000]  sda: sda1 sda2
[    6.952000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.960000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.960000] Uniform CD-ROM driver Revision: 3.20
[    6.960000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.960000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.960000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    7.320000] kjournald starting.  Commit interval 5 seconds
[    7.320000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.204000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b2400004669df]
[   15.360000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.364000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.636000] intel_rng: FWH not detected
[   15.728000] iTCO_vendor_support: vendor-support=0
[   15.736000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.736000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.740000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.104000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.188000] Yenta: CardBus bridge found at 0000:05:09.0 [17aa:2075]
[   16.188000] Yenta: Enabling burst memory read transactions
[   16.188000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.188000] Yenta: Routing CardBus interrupts to PCI
[   16.188000] Yenta TI: socket 0000:05:09.0, mfunc 0x01101b22, devctl 0x66
[   16.256000] ieee80211_crypt: registered algorithm 'NULL'
[   16.260000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.260000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.416000] nvidia: module license 'NVIDIA' taints kernel.
[   16.520000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   16.520000] Socket status: 30000006
[   16.520000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[   16.520000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   16.520000] cs: IO port probe 0x2000-0x2fff: clean.
[   16.520000] pcmcia: parent PCI bridge Memory window: 0xd2000000 - 0xd20fffff
[   16.520000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   16.672000] bcm43xx driver
[   16.672000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.672000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   16.672000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   16.676000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.676000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.692000] ACPI: PCI Interrupt 0000:05:09.2[A] -> GSI 18 (level, low) -> IRQ 18
[   16.828000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1da0b1, caps: 0xa04713/0x204006
[   16.864000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   17.068000] cs: IO port probe 0x100-0x3af: clean.
[   17.068000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.072000] cs: IO port probe 0x820-0x8ff: clean.
[   17.072000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.072000] cs: IO port probe 0xa00-0xaff: clean.
[   17.256000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   17.256000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.788000] lp: driver loaded but no devices found
[   18.324000] EXT3 FS on sda1, internal journal
[   21.616000] No dock devices found.
[   21.732000] input: Power Button (FF) as /class/input/input3
[   21.732000] ACPI: Power Button (FF) [PWRF]
[   21.732000] input: Lid Switch as /class/input/input4
[   21.732000] ACPI: Lid Switch [LID]
[   21.744000] input: Power Button (CM) as /class/input/input5
[   21.744000] ACPI: Power Button (CM) [PWRB]
[   21.748000] input: Sleep Button (CM) as /class/input/input6
[   21.748000] ACPI: Sleep Button (CM) [SLPB]
[   21.920000] ACPI: AC Adapter [ACAD] (off-line)
[   22.008000] ACPI: Battery Slot [BAT1] (battery present)
[   22.032000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   23.364000] Failure registering capabilities with primary security module.
[   23.616000] ppdev: user-space parallel port driver
[   23.724000] PM: Writing back config space on device 0000:05:07.0 at offset c (was fde70000, writing 0)
[   23.724000] PM: Writing back config space on device 0000:05:07.0 at offset b (was 3ed173b, writing 207517aa)
[   23.724000] PM: Writing back config space on device 0000:05:07.0 at offset 3 (was 0, writing 2010)
[   23.724000] PM: Writing back config space on device 0000:05:07.0 at offset 2 (was 2000000, writing 2000003)
[   23.724000] PM: Writing back config space on device 0000:05:07.0 at offset 1 (was 2b00000, writing 2b00106)
[   23.724000] PM: Writing back config space on device 0000:05:07.0 at offset 0 (was 3ed173b, writing 169c14e4)
[   24.680000] audit(1204150135.060:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5062 profile="/usr/sbin/cupsd"
[   24.760000] apm: BIOS not found.
[   25.584000] Bluetooth: Core ver 2.11
[   25.584000] NET: Registered protocol family 31
[   25.584000] Bluetooth: HCI device and connection manager initialized
[   25.584000] Bluetooth: HCI socket layer initialized
[   25.664000] Bluetooth: L2CAP ver 2.8
[   25.664000] Bluetooth: L2CAP socket layer initialized
[   25.764000] Bluetooth: RFCOMM socket layer initialized
[   25.764000] Bluetooth: RFCOMM TTY layer initialized
[   25.764000] Bluetooth: RFCOMM ver 1.8
[   43.204000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   43.204000] tg3: eth0: Flow control is on for TX and on for RX.
[   45.512000] NET: Registered protocol family 17
[   46.888000] NET: Registered protocol family 10
[   46.888000] lo: Disabled Privacy Extensions
[   46.892000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   57.108000] eth0: no IPv6 routers present

The Wifi Radar finds nothing on the radar. 
The iwconfig tool is a kind of complicated I must say......

Already many thanks for helping me!

---

### Post by heyster on 2008-02-28
Even when I define with network manager or with Wifi Radar a new connection, it does not want to link me to my wifi.

---

### Post by heyster on 2008-02-29
"Does anybody out there even care
Wake up world before it's too late " by Lenny Kravitz

When no one has a clue what is happening to my Laptop, I will re-install another time.

Thanks anyway.

---

### Post by tgalati4 on 2008-03-01
How old is the laptop?  Sometimes the antenna wire that goes through the hinge gets worn out and shorted so you get no signal!  Try opening and closing the lid and watch wifi-radar to see if you can pick up any wifi signal.  If nothing shows up--take it to starbucks--then you may have an antenna problem.

Post the output of:

>ifconfig 

and

>iwconfig

---

### Post by heyster on 2008-03-01
Thanks tgalati4 
The laptop is 3 months old. After I installed Leopard, on a different partition the network was also not there. But after I gave the Linksys itself a reboot, I the internet was with Vista (must be a pain for the laptop :-) )back in action.
After that I tried to install Ubuntu again but grub gave me error 15.
After 6 hours of sleep I installed Ubuntu and now everything works fine. Tonight I will introduce my new best friend to the Lenovo laptop. 
He is called Backup

---

### Post by heyster on 2008-03-11
After the last re-install, the wireless was once dead. After a few reboots I could receive my access point's signal. Knock on wood.

---

### Post by uberlube on 2008-03-11
If you would like a method of installing the driver that will engage your wireless upon boot, check out the howto in my sig. Dont know if it will help, but it might be worth a try :)

---

