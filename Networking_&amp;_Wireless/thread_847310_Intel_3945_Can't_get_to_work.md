---
title: "Intel 3945 Can't get to work"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by postalservice14 on 2008-07-02
Hello,

I have a Sony Vaio that ran Kubuntu, and wireless worked out of the box perfectly.  I recently removed Kubuntu and installed Ubuntu 8.04 and wireless does not work at all.  From what I am seeing on the other forum posts, it looks like it finds my wireless card no sweat, but it just won't connect or scan anything.  My wireless access point is WPA encryption btw and I have WPA Supplicant installed.

Thanks in advance,

John

---

### Post by pytheas22 on 2008-07-02
First, install all of the updates (using a wired connection) and reboot, and see if it helps.

If not, please try to connect to a network a couple of times, and then immediately after, open a terminal (Applications>Accessories) and post the output of these commands:
```

dmesg
iwconfig
iwlist scan
```

Also, when your card worked under Kubuntu, were you using 7.10 or 8.04?

---

### Post by postalservice14 on 2008-07-02
> **pytheas22 said:**
> First, install all of the updates (using a wired connection) and reboot, and see if it helps.

I have done this and it did not seem to change anything (as far as my problem)

> **pytheas22 said:**
> If not, please try to connect to a network a couple of times, and then immediately after, open a terminal (Applications>Accessories) and post the output of these commands:
```

dmesg
iwconfig
iwlist scan
```

dmesg output: (it had a lot more text, but didn't think you wanted ALL of it)
```

[   19.181389] usb usb3: configuration #1 chosen from 1 choice

[   19.181434] hub 3-0:1.0: USB hub found

[   19.181445] hub 3-0:1.0: 2 ports detected

[   19.284975] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 17 (level, low) -> IRQ 18

[   19.284995] PCI: Setting latency timer of device 0000:00:1d.3 to 64

[   19.285004] uhci_hcd 0000:00:1d.3: UHCI Host Controller

[   19.285048] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4

[   19.285087] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00001880

[   19.285294] usb usb4: configuration #1 chosen from 1 choice

[   19.285339] hub 4-0:1.0: USB hub found

[   19.285350] hub 4-0:1.0: 2 ports detected

[   19.310648] libata version 3.00 loaded.

[   19.316858] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI

[   19.316864] e100: Copyright(c) 1999-2006 Intel Corporation

[   19.389091] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 21

[   19.389115] PCI: Setting latency timer of device 0000:00:1d.7 to 64

[   19.389122] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[   19.389167] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5

[   19.393097] ehci_hcd 0000:00:1d.7: debug port 1

[   19.393109] PCI: cache line size of 32 is not supported by device 0000:00:1d.7

[   19.393127] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xd4444000

[   19.408759] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[   19.408965] usb usb5: configuration #1 chosen from 1 choice

[   19.409013] hub 5-0:1.0: USB hub found

[   19.409024] hub 5-0:1.0: 8 ports detected

[   19.513016] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 17

[   19.544233] e100: eth0: e100_probe: addr 0xd4005000, irq 17, MAC addr 00:13:a9:8a:46:15

[   19.544282] ACPI: PCI Interrupt 0000:06:04.1[B] -> GSI 21 (level, low) -> IRQ 20

[   19.594140] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d4006000-d40067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[   19.619584] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 22 (level, low) -> IRQ 22

[   19.619641] PCI: Setting latency timer of device 0000:00:1f.1 to 64

[   19.619664] ACPI: PCI interrupt for device 0000:00:1f.1 disabled

[   19.630073] ata_piix 0000:00:1f.1: version 2.12

[   19.630095] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 22 (level, low) -> IRQ 22

[   19.630146] PCI: Setting latency timer of device 0000:00:1f.1 to 64

[   19.631644] scsi0 : ata_piix

[   19.632758] scsi1 : ata_piix

[   19.634026] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14

[   19.634033] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15

[   19.961229] ata1.00: ATA-6: TOSHIBA MK8009GAH, BQ001A, max UDMA/100

[   19.961237] ata1.00: 156301488 sectors, multi 16: LBA48 

[   19.961289] ata1.01: ATAPI: MATSHITAUJ-842D, 1.20, max UDMA/33

[   19.969056] ata1.00: configured for UDMA/100

[   20.142138] ata1.01: configured for UDMA/33

[   20.142211] ata2: port disabled. ignoring.

[   20.142432] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8009GA BQ00 PQ: 0 ANSI: 5

[   20.144439] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-842D          1.20 PQ: 0 ANSI: 5

[   20.412189] usb 3-1: new full speed USB device using uhci_hcd and address 2

[   20.483579] Driver 'sd' needs updating - please use bus_type methods

[   20.483714] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[   20.483739] sd 0:0:0:0: [sda] Write Protect is off

[   20.483744] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   20.483779] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   20.483865] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[   20.483887] sd 0:0:0:0: [sda] Write Protect is off

[   20.483892] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   20.483925] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   20.483932]  sda:<4>Driver 'sr' needs updating - please use bus_type methods

[   20.523654]  sda1 sda2 sda3

[   20.543905] sd 0:0:0:0: [sda] Attached SCSI disk

[   20.556388] sd 0:0:0:0: Attached scsi generic sg0 type 0

[   20.556425] sr 0:0:1:0: Attached scsi generic sg1 type 5

[   20.559376] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray

[   20.559383] Uniform CD-ROM driver Revision: 3.20

[   20.559459] sr 0:0:1:0: Attached scsi CD-ROM sr0

[   20.590629] usb 3-1: configuration #1 chosen from 1 choice

[   20.831949] usb 4-1: new full speed USB device using uhci_hcd and address 2

[   20.888089] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030246a370]

[   21.036354] usb 4-1: configuration #1 chosen from 1 choice

[   21.144833] Attempting manual resume

[   21.144840] swsusp: Resume From Partition 8:3

[   21.144844] PM: Checking swsusp image.

[   21.145115] PM: Resume from disk failed.

[   21.210804] kjournald starting.  Commit interval 5 seconds

[   21.210822] EXT3-fs: mounted filesystem with ordered data mode.

[   40.970338] Linux agpgart interface v0.102

[   41.048614] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   41.123511] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   41.268217] agpgart: Detected an Intel 945GM Chipset.

[   41.269360] agpgart: Detected 7932K stolen memory.

[   41.328418] agpgart: AGP aperture is 256M @ 0xc0000000

[   41.784921] iTCO_vendor_support: vendor-support=0

[   41.847782] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)

[   41.847975] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware

[   41.848024] iTCO_wdt: No card detected

[   42.383457] intel_rng: FWH not detected

[   43.179211] input: Lid Switch as /devices/virtual/input/input2

[   43.187218] ACPI: Lid Switch [LID0]

[   43.187348] input: Power Button (CM) as /devices/virtual/input/input3

[   43.202963] ACPI: Power Button (CM) [PWRB]

[   43.279186] input: PC Speaker as /devices/platform/pcspkr/input/input4

[   44.054503] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0

[   44.054512] iwl3945: Copyright(c) 2003-2007 Intel Corporation

[   44.054726] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16

[   44.054747] PCI: Setting latency timer of device 0000:02:00.0 to 64

[   44.054777] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection

[   46.869655] sony-laptop: Sony Programmable IO Control Driver v0.5.

[   46.869669] sony-laptop: detected Type3 model

[   46.909318] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY6001:00/input/input5

[   46.930188] input: Sony Vaio Jogdial as /devices/virtual/input/input6

[   46.940921] sony-laptop: device allocated minor is 63

[   46.945290] sony-laptop: Sony Notebook Control Driver v0.5.

[   49.140649] input: PS/2 Mouse as /devices/virtual/input/input7

[   49.167514] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8

[   49.295257] ACPI: AC Adapter [ACAD] (on-line)

[   49.895182] ACPI: Battery Slot [BAT1] (battery present)

[   50.043308] Bluetooth: Core ver 2.11

[   50.076574] NET: Registered protocol family 31

[   50.076580] Bluetooth: HCI device and connection manager initialized

[   50.076587] Bluetooth: HCI socket layer initialized

[   50.132870] Bluetooth: HCI USB driver ver 2.9

[   50.135605] usbcore: registered new interface driver hci_usb

[   50.195355] tpm_inf_pnp 00:07: Found TPM with ID IFX0102

[   50.195424] tpm_inf_pnp 00:07: TPM found: config base 0x2e, data base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)

[   51.814257] Yenta: CardBus bridge found at 0000:06:04.0 [104d:8207]

[   51.814290] Yenta: Enabling burst memory read transactions

[   51.814300] Yenta: Using CSCINT to route CSC interrupts to PCI

[   51.814304] Yenta: Routing CardBus interrupts to PCI

[   51.814314] Yenta TI: socket 0000:06:04.0, mfunc 0x01a21b22, devctl 0x64

[   51.857827] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels

[   51.863355] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

[   52.046570] Yenta: ISA IRQ mask 0x0cb8, PCI irq 17

[   52.046578] Socket status: 30000006

[   52.046583] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a

[   52.046593] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff

[   52.046599] cs: IO port probe 0x3000-0x3fff: clean.

[   52.047104] pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd40fffff

[   52.061868] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 22 (level, low) -> IRQ 22

[   52.062101] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19

[   52.062128] PCI: Setting latency timer of device 0000:00:1b.0 to 64

[   52.095583] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...

[   53.487648] cs: IO port probe 0x100-0x3af: clean.

[   53.490179] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7

[   53.491251] cs: IO port probe 0x820-0x8ff: clean.

[   53.492138] cs: IO port probe 0xc00-0xcf7: clean.

[   53.493318] cs: IO port probe 0xa00-0xaff: clean.

[   53.765375] lp: driver loaded but no devices found

[   54.193938] Adding 3068404k swap on /dev/sda3.  Priority:-1 extents:1 across:3068404k

[   54.898255] EXT3 FS on sda2, internal journal

[   56.540414] ip_tables: (C) 2000-2006 Netfilter Core Team

[   57.645225] No dock devices found.

[   59.173256] apm: BIOS not found.

[   59.348516] ppdev: user-space parallel port driver

[   59.586064] audit(1215029228.054:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4946 profile="/usr/sbin/cupsd" namespace="default"

[   59.703261] sonypi: Sony Programmable I/O Controller Driver v1.26.

[   59.703610] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers

[   59.703977] sonypi: ioport 0x1080 busy, using sony-laptop? if not use check_ioport=0

[   59.703983] sonypi: failed to request ioports

[   59.704337] sonypi: probe of sonypi failed with error -16

[   61.726269] Bluetooth: L2CAP ver 2.9

[   61.726278] Bluetooth: L2CAP socket layer initialized

[   61.852912] Bluetooth: RFCOMM socket layer initialized

[   61.852933] Bluetooth: RFCOMM TTY layer initialized

[   61.852937] Bluetooth: RFCOMM ver 1.8

[   62.430023] iwl3945: Microcode SW error detected.  Restarting 0x82000008.

[   62.430097] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B

[   63.424996] iwl3945: Can't stop Rx DMA.

[   66.090295] [drm] Initialized drm 1.1.0 20060810

[   66.106363] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16

[   66.106378] PCI: Setting latency timer of device 0000:00:02.0 to 64

[   66.107292] [drm] Initialized i915 1.6.0 20060119 on minor 0

[   85.624050] NET: Registered protocol family 10

[   85.624859] lo: Disabled Privacy Extensions

[   85.625916] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   85.627095] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  158.826066] NET: Registered protocol family 17

```

iwconfig output:
```

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:""  Nickname:""

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


iwlist scan output:
```

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



wlan0     Failed to read scan data : Resource temporarily unavailable



```


> Also, when your card worked under Kubuntu, were you using 7.10 or 8.04?

Crap, I can't remember, I think it was the beta version of 8.04.

Thanks a ton for your help,

John

---

### Post by pytheas22 on 2008-07-02
These lines from dmesg are telling:
```
[   62.430023] iwl3945: Microcode SW error detected.  Restarting 0x82000008.

[   62.430097] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B

[   63.424996] iwl3945: Can't stop Rx DMA.

```

let me do some Googling and see what comes up.

---

### Post by pytheas22 on 2008-07-02
Apparently there's a [problem]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/226134") with the way the driver firmware is handled in the most recent build of the kernel (ironically, if you had not upgraded, or upgraded to the right point but no further, you wouldn't have this problem).  Please try this:
```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

and then try to connect.  If it works we can make the fix permanent.

---

### Post by postalservice14 on 2008-07-02
> **pytheas22 said:**
> Apparently there's a [problem]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/226134") with the way the driver firmware is handled in the most recent build of the kernel (ironically, if you had not upgraded, or upgraded to the right point but no further, you wouldn't have this problem).  Please try this:
```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

and then try to connect.  If it works we can make the fix permanent.

Yes!  That fixed it!  Thank you so much!

John

---

### Post by pytheas22 on 2008-07-02
> Yes! That fixed it! Thank you so much!

John

No problem.  If you want to make this fix permanent, run this command:
```

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```

Otherwise you will have to run the first command that I gave you after reach reboot in order to get the wireless working (until this gets fixed by an update or something), which you can do if you want, but making the fix permanent should be more convenient.

By the way, this fix is thanks to chili555 at [http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297) .

---

### Post by chili555 on 2008-07-02
Thanks for the thanks! I found it elsewhere, too. Glad it's working for all.

---

### Post by postalservice14 on 2008-07-02
> **pytheas22 said:**
> No problem.  If you want to make this fix permanent, run this command:
```

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```

Otherwise you will have to run the first command that I gave you after reach reboot in order to get the wireless working (until this gets fixed by an update or something), which you can do if you want, but making the fix permanent should be more convenient.

By the way, this fix is thanks to chili555 at [http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297) .

Thank you again.  This worked perfect for me.

---

### Post by bu3askoor on 2009-07-27
> **postalservice14 said:**
> Thank you again.  This worked perfect for me.

This finally worked for me and i tiried everything before!!  thanks a lot

---

