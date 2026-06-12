---
title: "Zyxel G-202 usb wifi slow to startup on 13.10"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by samuelsimon on 2014-01-13
I recently upgraded to 13.10 with a clean installation. My Zyxel G-202 USB wifi adapter worked straight away with no drivers to install but I'm now have a problem. When I start-up or restart the computer it takes a few minutes before it connects to my wifi. No wireless networks appear in the network menu for the first few minutes, making me think the USB wifi adapter is not being 'turned on' straight away, or is taken a long time to start up. 

Any suggestions would be appreciated. Thanks

---

### Post by samuelsimon on 2014-01-14
When I first start-up if I run nm-tool there is no record of wifi as an option. A few minutes later it appears and successfully connects to my wireless network almost immediately.

  Type:              802.11 WiFi
  Driver:            zd1211rw
  State:             connected

---

### Post by samuelsimon on 2014-02-02
Some help with this would be greatly appreciated, some more information is below:[B]

Before wifi connects:
[/B]
ss4@lenovo:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1D:7D:B6:65:8C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

ss4@lenovo:~$ sudo iw dev wlan0 get power_save
[sudo] password for ss4: 
command failed: No such device (-19)


**5 minute later when I have a wifi connection: **


ss4@lenovo:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [TALKTALK-CC0AC4] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            zd1211rw
  State:             connected
  Default:           yes
  HW Address:        00:13:49:8E:DD:A5

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTHub4-T8F6:     Infra, CC:33:BB:5D:2F:28, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BTHub3-59NH:     Infra, 00:FE:F4:2E:10:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTWiFi:          Infra, 02:FE:F4:2E:10:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 36
    BTWiFi-with-FON: Infra, 12:FE:F4:2E:10:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    BTWifi-with-FON: Infra, CC:33:BB:5D:2F:2B, Freq 2437 MHz, Rate 54 Mb/s, Strength 31
    *TALKTALK-CC0AC4:Infra, 5C:7D:5E:CC:0A:C6, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    VM018815-2G:     Infra, 9C:D3:6D:20:8D:90, Freq 2452 MHz, Rate 54 Mb/s, Strength 8 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1D:7D:B6:65:8C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


ss4@lenovo:~$ sudo iw dev wlan0 get power_save
Power save: off

---

### Post by varunendra on 2014-02-02
> **samuelsimon said:**
> 
  Wireless Access Points (* = current AP)
....
    *TALKTALK-CC0AC4:Infra, 5C:7D:5E:CC:0A:C6, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**


Is the router/access-point under your control? If yes, try changing the encryption type to pure WPA2-PSK with AES. Currently it is set to WPA/WPA2 mixed mode which uses TKIP (should be avoided).

If that change alone doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by samuelsimon on 2014-02-02
varunendra, thank you for the reply. I pretty sure the issue is prior to the connection to the router.

Below is the output from dmesg which shows a cycle of a USB device resetting.

When I upgraded to 13.10 I installed the operating on a SSD which I had not used before and I installed additional RAM. I doubt either of these would cause the problem but thought it could be worth mentioning. 



```
[    2.220120] ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.220247] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.220259] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.228352] ata2.00: ATA-8: Hitachi HDP725050GLA360, GM4OA52A, max UDMA/133
[    2.228356] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.244407] ata2.00: configured for UDMA/133
[    2.247010] ata1.00: ATA-8: KINGSTON SV300S37A120G, 521ABBF0, max UDMA/133
[    2.247015] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.278920] ata1.00: configured for UDMA/133
[    2.279084] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 521A PQ: 0 ANSI: 5
[    2.279233] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.279235] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.279323] sd 0:0:0:0: [sda] Write Protect is off
[    2.279326] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.279352] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.279354] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72505 GM4O PQ: 0 ANSI: 5
[    2.279493] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.279496] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.279557] sd 1:0:0:0: [sdb] Write Protect is off
[    2.279560] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.279585] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.280408]  sda: sda1 sda2 < sda5 >
[    2.280856] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.321833]  sdb: sdb1 sdb2 < sdb5 >
[    2.322157] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.323415] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    2.323418] Write protecting the kernel read-only data: 12288k
[    2.326642] Freeing unused kernel memory: 1032K (ffff8800016fe000 - ffff880001800000)
[    2.329021] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    2.342492] systemd-udevd[107]: starting version 204
[    2.354702] usb 6-2: New USB device found, idVendor=045e, idProduct=0040
[    2.354708] usb 6-2: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    2.354711] usb 6-2: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[    2.354713] usb 6-2: Manufacturer: Microsoft
[    2.360272] pata_acpi 0000:00:03.2: enabling device (0004 -> 0005)
[    2.360466] pata_acpi 0000:00:03.2: setting latency timer to 64
[    2.372032] pps_core: LinuxPPS API ver. 1 registered
[    2.372036] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.374329] PTP clock support registered
[    2.382009] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    2.382013] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    2.382200] e1000e 0000:00:19.0: setting latency timer to 64
[    2.382267] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.382292] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    2.407704] FDC 0 is a post-1991 82077
[    2.435807] hidraw: raw HID events driver (C) Jiri Kosina
[    2.453753] usbcore: registered new interface driver usbhid
[    2.453757] usbhid: USB HID core driver
[    2.456354] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input2
[    2.457600] hid-generic 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2/input0
[    2.459843] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.480109] Switched to clocksource tsc
[    2.596031] usb 8-1: new low-speed USB device number 2 using uhci_hcd
[    2.690008] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1d:7d:b6:65:8c
[    2.690012] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.690036] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    2.780382] usb 8-1: New USB device found, idVendor=04df, idProduct=0032
[    2.780389] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.780394] usb 8-1: Product: USB RF Combo Device 
[    2.780398] usb 8-1: Manufacturer: Interlink Electronics, Inc. 
[    2.816751] input: Interlink Electronics, Inc.  USB RF Combo Device  as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input3
[    2.816833] hid-generic 0003:04DF:0032.0002: input,hidraw1: USB HID v1.00 Keyboard [Interlink Electronics, Inc.  USB RF Combo Device ] on usb-0000:00:1d.2-1/input0
[    2.852841] input: Interlink Electronics, Inc.  USB RF Combo Device  as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input4
[    2.852932] hid-generic 0003:04DF:0032.0003: input,hidraw2: USB HID v1.00 Mouse [Interlink Electronics, Inc.  USB RF Combo Device ] on usb-0000:00:1d.2-1/input1
[    3.174735] Adding 8080380k swap on /dev/sda5.  Priority:-1 extents:1 across:8080380k SSFS
[    3.220110] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.285489] systemd-udevd[273]: starting version 204
[    3.348380] usb 2-3: new high-speed USB device number 6 using ehci-pci
[    3.382533] mei_me 0000:00:03.0: setting latency timer to 64
[    3.382574] mei_me 0000:00:03.0: irq 41 for MSI/MSI-X
[    3.387956] [drm] Initialized drm 1.1.0 20060810
[    3.414714] [drm] Memory usable by graphics device = 512M
[    3.414727] i915 0000:00:02.0: setting latency timer to 64
[    3.444642] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    3.444655] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.444657] [drm] Driver supports precise vblank timestamp query.
[    3.444719] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.445781] [drm] initialized overlay support
[    3.449907] parport_pc 00:09: reported by Plug and Play ACPI
[    3.449939] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[    3.535949] lp: driver loaded but no devices found
[    3.540711] coretemp coretemp.0: Using relative temperature scale!
[    3.540723] coretemp coretemp.0: Using relative temperature scale!
[    3.550277] lp0: using parport0 (interrupt-driven).
[    3.560583] tpm_tis 00:0b: 1.2 TPM (device-id 0xFE, rev-id 70)
[    3.562209] type=1400 audit(1391353790.137:2): apparmor="STATUS" operation="profile_load" parent=306 profile="unconfined" name="/sbin/dhclient" pid=316 comm="apparmor_parser"
[    3.562218] type=1400 audit(1391353790.137:3): apparmor="STATUS" operation="profile_load" parent=306 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=316 comm="apparmor_parser"
[    3.562224] type=1400 audit(1391353790.137:4): apparmor="STATUS" operation="profile_load" parent=306 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=316 comm="apparmor_parser"
[    3.562817] type=1400 audit(1391353790.137:5): apparmor="STATUS" operation="profile_replace" parent=306 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=316 comm="apparmor_parser"
[    3.562824] type=1400 audit(1391353790.137:6): apparmor="STATUS" operation="profile_replace" parent=306 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=316 comm="apparmor_parser"
[    3.562879] fbcon: inteldrmfb (fb0) is primary device
[    3.563357] type=1400 audit(1391353790.137:7): apparmor="STATUS" operation="profile_replace" parent=306 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=316 comm="apparmor_parser"
[    3.617124] microcode: CPU0 sig=0x6fd, pf=0x1, revision=0xa1
[    3.626491] Linux video capture interface: v2.00
[    3.628218] Console: switching to colour frame buffer device 240x67
[    3.629022] gspca_main: v2.14.0 registered
[    3.636219] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.636222] i915 0000:00:02.0: registered panic notifier
[    3.637869] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20130517/video-1264)
[    3.637892] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[    3.638026] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
[    3.638175] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.638485] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.PCI0.IEIT.EITR 1 (20130517/utaddress-251)
[    3.638493] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.PCI0.LPC0.PMIO 2 (20130517/utaddress-251)
[    3.638497] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.638501] ACPI Warning: 0x0000000000001180-0x00000000000011af SystemIO conflicts with Region \_SB_.PCI0.LPC0.GPOX 1 (20130517/utaddress-251)
[    3.638505] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.638553] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.646165] gspca_main: sonixj-2.14.0 probing 0c45:612c
[    3.654982] input: sonixj as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/input/input6
[    3.655421] usbcore: registered new interface driver sonixj
[    3.684544] tpm_tis 00:0b: TPM is disabled/deactivated (0x6)
[    3.749279] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    3.784060] usb 2-3: new high-speed USB device number 7 using ehci-pci
[    4.128301] hda_codec: AD1882: BIOS auto-probing.
[    4.128761] autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0) type:line
[    4.128763]    speaker_outs=1 (0x13/0x0/0x0/0x0/0x0)
[    4.128765]    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[    4.128767]    mono: mono_out=0x0
[    4.128768]    inputs:
[    4.128770]      Front Mic=0x14
[    4.128772]      Rear Mic=0x17
[    4.128774]      Line=0x15
[    4.128775]      CD=0x18
[    4.137226] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    4.138988] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    4.140245] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.140458] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.140664] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.359077] ppdev: user-space parallel port driver
[    4.392898] microcode: CPU1 sig=0x6fd, pf=0x1, revision=0xa1
[    4.398929] gpio_ich: GPIO from 195 to 255 on gpio_ich
[    4.441646] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.500955] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    4.827752] init: failsafe main process (564) killed by TERM signal
[    4.988056] usb 2-3: new high-speed USB device number 12 using ehci-pci
[    5.239131] Bluetooth: Core ver 2.16
[    5.239158] NET: Registered protocol family 31
[    5.239160] Bluetooth: HCI device and connection manager initialized
[    5.239173] Bluetooth: HCI socket layer initialized
[    5.239176] Bluetooth: L2CAP socket layer initialized
[    5.239184] Bluetooth: SCO socket layer initialized
[    5.257255] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.257261] Bluetooth: BNEP filters: protocol multicast
[    5.257275] Bluetooth: BNEP socket layer initialized
[    5.274774] Bluetooth: RFCOMM TTY layer initialized
[    5.274792] Bluetooth: RFCOMM socket layer initialized
[    5.274794] Bluetooth: RFCOMM ver 1.11
[    5.388286] init: avahi-cups-reload main process (646) terminated with status 1
[    5.405159] type=1400 audit(1391353791.981:8): apparmor="STATUS" operation="profile_load" parent=657 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=672 comm="apparmor_parser"
[    5.405171] type=1400 audit(1391353791.981:9): apparmor="STATUS" operation="profile_load" parent=657 profile="unconfined" name="/usr/sbin/cupsd" pid=672 comm="apparmor_parser"
[    5.405866] type=1400 audit(1391353791.981:10): apparmor="STATUS" operation="profile_replace" parent=657 profile="unconfined" name="/usr/sbin/cupsd" pid=672 comm="apparmor_parser"
[    5.544136] usb 2-3: new high-speed USB device number 14 using ehci-pci
[    5.618752] type=1400 audit(1391353792.193:11): apparmor="STATUS" operation="profile_load" parent=704 profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=710 comm="apparmor_parser"
[    5.618763] type=1400 audit(1391353792.193:12): apparmor="STATUS" operation="profile_load" parent=704 profile="unconfined" name="chromium_browser" pid=710 comm="apparmor_parser"
[    5.619259] type=1400 audit(1391353792.193:13): apparmor="STATUS" operation="profile_replace" parent=704 profile="unconfined" name="chromium_browser" pid=710 comm="apparmor_parser"
[    5.620026] type=1400 audit(1391353792.197:14): apparmor="STATUS" operation="profile_load" parent=704 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=709 comm="apparmor_parser"
[    5.620035] type=1400 audit(1391353792.197:15): apparmor="STATUS" operation="profile_load" parent=704 profile="unconfined" name="chromium_browser" pid=709 comm="apparmor_parser"
[    5.620787] type=1400 audit(1391353792.197:16): apparmor="STATUS" operation="profile_replace" parent=704 profile="unconfined" name="chromium_browser" pid=709 comm="apparmor_parser"
[    5.624603] type=1400 audit(1391353792.201:17): apparmor="STATUS" operation="profile_replace" parent=704 profile="unconfined" name="/sbin/dhclient" pid=712 comm="apparmor_parser"
[    5.624617] type=1400 audit(1391353792.201:18): apparmor="STATUS" operation="profile_replace" parent=704 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=712 comm="apparmor_parser"
[    5.624623] type=1400 audit(1391353792.201:19): apparmor="STATUS" operation="profile_replace" parent=704 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=712 comm="apparmor_parser"
[    5.625310] type=1400 audit(1391353792.201:20): apparmor="STATUS" operation="profile_replace" parent=704 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=712 comm="apparmor_parser"
[    5.840209] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    5.944104] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    5.944227] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.944565] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.104040] usb 2-3: new high-speed USB device number 16 using ehci-pci
[    6.660070] usb 2-3: new high-speed USB device number 18 using ehci-pci
[    7.216426] usb 2-3: new high-speed USB device number 20 using ehci-pci
[    7.772148] usb 2-3: new high-speed USB device number 22 using ehci-pci
[    8.396046] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[    8.396058] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[    8.544039] usb 2-3: new high-speed USB device number 25 using ehci-pci
[    9.100040] usb 2-3: new high-speed USB device number 27 using ehci-pci
[   10.304041] usb 2-3: new high-speed USB device number 32 using ehci-pci
[   11.508045] usb 2-3: new high-speed USB device number 37 using ehci-pci
[   13.576059] usb 2-3: new high-speed USB device number 46 using ehci-pci
[   13.916034] usb 2-3: new high-speed USB device number 47 using ehci-pci
[   14.256055] usb 2-3: new high-speed USB device number 48 using ehci-pci
[   14.408039] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   14.408049] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   14.812035] usb 2-3: new high-speed USB device number 50 using ehci-pci
[   15.368039] usb 2-3: new high-speed USB device number 52 using ehci-pci
[   16.792046] usb 2-3: new high-speed USB device number 58 using ehci-pci
[   17.348048] usb 2-3: new high-speed USB device number 60 using ehci-pci
[   18.120044] usb 2-3: new high-speed USB device number 63 using ehci-pci
[   18.460034] usb 2-3: new high-speed USB device number 64 using ehci-pci
[   18.800046] usb 2-3: new high-speed USB device number 65 using ehci-pci
[   20.004049] usb 2-3: new high-speed USB device number 70 using ehci-pci
[   20.420042] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   20.420056] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   20.560065] usb 2-3: new high-speed USB device number 72 using ehci-pci
[   21.116047] usb 2-3: new high-speed USB device number 74 using ehci-pci
[   21.456039] usb 2-3: new high-speed USB device number 75 using ehci-pci
[   21.796039] usb 2-3: new high-speed USB device number 76 using ehci-pci
[   22.352053] usb 2-3: new high-speed USB device number 78 using ehci-pci
[   24.420054] usb 2-3: new high-speed USB device number 87 using ehci-pci
[   26.056076] usb 2-3: new high-speed USB device number 94 using ehci-pci
[   26.432050] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   26.432060] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   27.260060] usb 2-3: new high-speed USB device number 99 using ehci-pci
[   28.032056] usb 2-3: new high-speed USB device number 102 using ehci-pci
[   28.372039] usb 2-3: new high-speed USB device number 103 using ehci-pci
[   28.928084] usb 2-3: new high-speed USB device number 105 using ehci-pci
[   29.700071] usb 2-3: new high-speed USB device number 108 using ehci-pci
[   30.688073] usb 2-3: new high-speed USB device number 112 using ehci-pci
[   32.444040] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   32.444052] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   32.756071] usb 2-3: new high-speed USB device number 121 using ehci-pci
[   33.312055] usb 2-3: new high-speed USB device number 123 using ehci-pci
[   34.084071] usb 2-3: new high-speed USB device number 126 using ehci-pci
[   34.640059] usb 2-3: new high-speed USB device number 2 using ehci-pci
[   35.196059] usb 2-3: new high-speed USB device number 4 using ehci-pci
[   35.536062] usb 2-3: new high-speed USB device number 5 using ehci-pci
[   35.876082] usb 2-3: new high-speed USB device number 6 using ehci-pci
[   36.216066] usb 2-3: new high-speed USB device number 7 using ehci-pci
[   36.772062] usb 2-3: new high-speed USB device number 9 using ehci-pci
[   37.112045] usb 2-3: new high-speed USB device number 10 using ehci-pci
[   38.456057] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   38.456068] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   38.532052] usb 2-3: new high-speed USB device number 16 using ehci-pci
[   38.872137] usb 2-3: new high-speed USB device number 17 using ehci-pci
[   39.212106] usb 2-3: new high-speed USB device number 18 using ehci-pci
[   39.984044] usb 2-3: new high-speed USB device number 21 using ehci-pci
[   40.324042] usb 2-3: new high-speed USB device number 22 using ehci-pci
[   41.528064] usb 2-3: new high-speed USB device number 27 using ehci-pci
[   41.868073] usb 2-3: new high-speed USB device number 28 using ehci-pci
[   43.072042] usb 2-3: new high-speed USB device number 33 using ehci-pci
[   43.412058] usb 2-3: new high-speed USB device number 34 using ehci-pci
[   44.468051] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   44.468063] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   46.776082] usb 2-3: new high-speed USB device number 49 using ehci-pci
[   48.844065] usb 2-3: new high-speed USB device number 58 using ehci-pci
[   49.616052] usb 2-3: new high-speed USB device number 61 using ehci-pci
[   49.956057] usb 2-3: new high-speed USB device number 62 using ehci-pci
[   50.296053] usb 2-3: new high-speed USB device number 63 using ehci-pci
[   50.480041] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   50.480054] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   50.852076] usb 2-3: new high-speed USB device number 65 using ehci-pci
[   52.920064] usb 2-3: new high-speed USB device number 74 using ehci-pci
[   54.124059] usb 2-3: new high-speed USB device number 79 using ehci-pci
[   54.464066] usb 2-3: new high-speed USB device number 80 using ehci-pci
[   55.020055] usb 2-3: new high-speed USB device number 82 using ehci-pci
[   55.792070] usb 2-3: new high-speed USB device number 85 using ehci-pci
[   56.492042] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   56.492054] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   56.564046] usb 2-3: new high-speed USB device number 88 using ehci-pci
[   57.120068] usb 2-3: new high-speed USB device number 90 using ehci-pci
[   57.676049] usb 2-3: new high-speed USB device number 92 using ehci-pci
[   58.664047] usb 2-3: new high-speed USB device number 96 using ehci-pci
[   59.220060] usb 2-3: new high-speed USB device number 98 using ehci-pci
[   60.208038] usb 2-3: new high-speed USB device number 102 using ehci-pci
[   60.764048] usb 2-3: new high-speed USB device number 104 using ehci-pci
[   61.752071] usb 2-3: new high-speed USB device number 108 using ehci-pci
[   62.092045] usb 2-3: new high-speed USB device number 109 using ehci-pci
[   62.504054] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   62.504063] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   62.648034] usb 2-3: new high-speed USB device number 111 using ehci-pci
[   63.204050] usb 2-3: new high-speed USB device number 113 using ehci-pci
[   63.544048] usb 2-3: new high-speed USB device number 114 using ehci-pci
[   64.100046] usb 2-3: new high-speed USB device number 116 using ehci-pci
[   64.440063] usb 2-3: new high-speed USB device number 117 using ehci-pci
[   66.292034] usb 2-3: new high-speed USB device number 125 using ehci-pci
[   66.848030] usb 2-3: new high-speed USB device number 127 using ehci-pci
[   67.404047] usb 2-3: new high-speed USB device number 3 using ehci-pci
[   67.744025] usb 2-3: new high-speed USB device number 4 using ehci-pci
[   68.516024] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   68.516037] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   68.732025] usb 2-3: new high-speed USB device number 8 using ehci-pci
[   69.720039] usb 2-3: new high-speed USB device number 12 using ehci-pci
[   72.004042] usb 2-3: new high-speed USB device number 22 using ehci-pci
[   73.640055] usb 2-3: new high-speed USB device number 29 using ehci-pci
[   74.528036] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   74.528049] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   74.628046] usb 2-3: new high-speed USB device number 33 using ehci-pci
[   74.968024] usb 2-3: new high-speed USB device number 34 using ehci-pci
[   75.524031] usb 2-3: new high-speed USB device number 36 using ehci-pci
[   75.864026] usb 2-3: new high-speed USB device number 37 using ehci-pci
[   76.204021] usb 2-3: new high-speed USB device number 38 using ehci-pci
[   76.976024] usb 2-3: new high-speed USB device number 41 using ehci-pci
[   77.316022] usb 2-3: new high-speed USB device number 42 using ehci-pci
[   77.872036] usb 2-3: new high-speed USB device number 44 using ehci-pci
[   78.428026] usb 2-3: new high-speed USB device number 46 using ehci-pci
[   78.984022] usb 2-3: new high-speed USB device number 48 using ehci-pci
[   79.756049] usb 2-3: new high-speed USB device number 51 using ehci-pci
[   80.096023] usb 2-3: new high-speed USB device number 52 using ehci-pci
[   80.436024] usb 2-3: new high-speed USB device number 53 using ehci-pci
[   80.540019] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   80.540031] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   80.776027] usb 2-3: new high-speed USB device number 54 using ehci-pci
[   81.332022] usb 2-3: new high-speed USB device number 56 using ehci-pci
[   82.104025] usb 2-3: new high-speed USB device number 59 using ehci-pci
[   83.092026] usb 2-3: new high-speed USB device number 63 using ehci-pci
[   84.080025] usb 2-3: new high-speed USB device number 67 using ehci-pci
[   84.420024] usb 2-3: new high-speed USB device number 68 using ehci-pci
[   86.056026] usb 2-3: new high-speed USB device number 75 using ehci-pci
[   86.396022] usb 2-3: new high-speed USB device number 76 using ehci-pci
[   86.552022] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   86.552034] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   86.736025] usb 2-3: new high-speed USB device number 77 using ehci-pci
[   87.940029] usb 2-3: new high-speed USB device number 82 using ehci-pci
[   90.656033] usb 2-3: new high-speed USB device number 94 using ehci-pci
[   91.644034] usb 2-3: new high-speed USB device number 98 using ehci-pci
[   92.200021] usb 2-3: new high-speed USB device number 100 using ehci-pci
[   92.564031] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   92.564045] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   93.404024] usb 2-3: new high-speed USB device number 105 using ehci-pci
[   93.744025] usb 2-3: new high-speed USB device number 106 using ehci-pci
[   94.084026] usb 2-3: new high-speed USB device number 107 using ehci-pci
[   94.640025] usb 2-3: new high-speed USB device number 109 using ehci-pci
[   94.980024] usb 2-3: new high-speed USB device number 110 using ehci-pci
[   96.184025] usb 2-3: new high-speed USB device number 115 using ehci-pci
[   96.740025] usb 2-3: new high-speed USB device number 117 using ehci-pci
[   97.080018] usb 2-3: new high-speed USB device number 118 using ehci-pci
[   98.068026] usb 2-3: new high-speed USB device number 122 using ehci-pci
[   98.576036] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[   98.576050] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[   99.272024] usb 2-3: new high-speed USB device number 127 using ehci-pci
[  100.692031] usb 2-3: new high-speed USB device number 7 using ehci-pci
[  101.680031] usb 2-3: new high-speed USB device number 11 using ehci-pci
[  102.020023] usb 2-3: new high-speed USB device number 12 using ehci-pci
[  102.576031] usb 2-3: new high-speed USB device number 14 using ehci-pci
[  103.780026] usb 2-3: new high-speed USB device number 19 using ehci-pci
[  104.588039] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  104.588052] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  105.416022] usb 2-3: new high-speed USB device number 26 using ehci-pci
[  105.972025] usb 2-3: new high-speed USB device number 28 using ehci-pci
[  107.392025] usb 2-3: new high-speed USB device number 34 using ehci-pci
[  110.108027] usb 2-3: new high-speed USB device number 46 using ehci-pci
[  110.600023] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  110.600036] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  113.256025] usb 2-3: new high-speed USB device number 60 using ehci-pci
[  113.596039] usb 2-3: new high-speed USB device number 61 using ehci-pci
[  114.152022] usb 2-3: new high-speed USB device number 63 using ehci-pci
[  116.612026] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  116.612039] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  116.652030] usb 2-3: new high-speed USB device number 74 using ehci-pci
[  116.992021] usb 2-3: new high-speed USB device number 75 using ehci-pci
[  117.332023] usb 2-3: new high-speed USB device number 76 using ehci-pci
[  117.888025] usb 2-3: new high-speed USB device number 78 using ehci-pci
[  118.444030] usb 2-3: new high-speed USB device number 80 using ehci-pci
[  118.784025] usb 2-3: new high-speed USB device number 81 using ehci-pci
[  119.988024] usb 2-3: new high-speed USB device number 86 using ehci-pci
[  120.328021] usb 2-3: new high-speed USB device number 87 using ehci-pci
[  121.316025] usb 2-3: new high-speed USB device number 91 using ehci-pci
[  121.872025] usb 2-3: new high-speed USB device number 93 using ehci-pci
[  122.624027] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  122.624040] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  122.644029] usb 2-3: new high-speed USB device number 96 using ehci-pci
[  124.496031] usb 2-3: new high-speed USB device number 104 using ehci-pci
[  126.132030] usb 2-3: new high-speed USB device number 111 using ehci-pci
[  127.552028] usb 2-3: new high-speed USB device number 117 using ehci-pci
[  128.636025] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  128.636038] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  128.756025] usb 2-3: new high-speed USB device number 122 using ehci-pci
[  129.744027] usb 2-3: new high-speed USB device number 126 using ehci-pci
[  130.732025] usb 2-3: new high-speed USB device number 4 using ehci-pci
[  131.288023] usb 2-3: new high-speed USB device number 6 using ehci-pci
[  131.844024] usb 2-3: new high-speed USB device number 8 using ehci-pci
[  132.184022] usb 2-3: new high-speed USB device number 9 using ehci-pci
[  132.524030] usb 2-3: new high-speed USB device number 10 using ehci-pci
[  132.864026] usb 2-3: new high-speed USB device number 11 using ehci-pci
[  133.204022] usb 2-3: new high-speed USB device number 12 using ehci-pci
[  134.648022] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  134.648035] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  135.056022] usb 2-3: new high-speed USB device number 20 using ehci-pci
[  136.908026] usb 2-3: new high-speed USB device number 28 using ehci-pci
[  137.896025] usb 2-3: new high-speed USB device number 32 using ehci-pci
[  139.100025] usb 2-3: new high-speed USB device number 37 using ehci-pci
[  139.440023] usb 2-3: new high-speed USB device number 38 using ehci-pci
[  139.780026] usb 2-3: new high-speed USB device number 39 using ehci-pci
[  140.120023] usb 2-3: new high-speed USB device number 40 using ehci-pci
[  140.660019] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  140.660032] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  141.972025] usb 2-3: new high-speed USB device number 48 using ehci-pci
[  143.176025] usb 2-3: new high-speed USB device number 53 using ehci-pci
[  143.516029] usb 2-3: new high-speed USB device number 54 using ehci-pci
[  144.936025] usb 2-3: new high-speed USB device number 60 using ehci-pci
[  145.492031] usb 2-3: new high-speed USB device number 62 using ehci-pci
[  146.264025] usb 2-3: new high-speed USB device number 65 using ehci-pci
[  146.672025] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  146.672037] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  146.820023] usb 2-3: new high-speed USB device number 67 using ehci-pci
[  147.808027] usb 2-3: new high-speed USB device number 71 using ehci-pci
[  148.148023] usb 2-3: new high-speed USB device number 72 using ehci-pci
[  148.704026] usb 2-3: new high-speed USB device number 74 using ehci-pci
[  149.476033] usb 2-3: new high-speed USB device number 77 using ehci-pci
[  150.032025] usb 2-3: new high-speed USB device number 79 using ehci-pci
[  150.372021] usb 2-3: new high-speed USB device number 80 using ehci-pci
[  151.576040] usb 2-3: new high-speed USB device number 85 using ehci-pci
[  152.684020] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  152.684032] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  152.996024] usb 2-3: new high-speed USB device number 91 using ehci-pci
[  153.984025] usb 2-3: new high-speed USB device number 95 using ehci-pci
[  154.324021] usb 2-3: new high-speed USB device number 96 using ehci-pci
[  154.664033] usb 2-3: new high-speed USB device number 97 using ehci-pci
[  155.004023] usb 2-3: new high-speed USB device number 98 using ehci-pci
[  155.560053] usb 2-3: new high-speed USB device number 100 using ehci-pci
[  156.332025] usb 2-3: new high-speed USB device number 103 using ehci-pci
[  157.536029] usb 2-3: new high-speed USB device number 108 using ehci-pci
[  158.092026] usb 2-3: new high-speed USB device number 110 using ehci-pci
[  158.432021] usb 2-3: new high-speed USB device number 111 using ehci-pci
[  158.696026] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  158.696038] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  159.420023] usb 2-3: new high-speed USB device number 115 using ehci-pci
[  161.056025] usb 2-3: new high-speed USB device number 122 using ehci-pci
[  161.188822] usb 2-3: New USB device found, idVendor=0586, idProduct=3410
[  161.188829] usb 2-3: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[  161.188835] usb 2-3: Product: ZyXEL G-202
[  161.188840] usb 2-3: Manufacturer: ZyDAS
[  161.229075] cfg80211: Calling CRDA to update world regulatory domain
[  161.238192] cfg80211: World regulatory domain updated:
[  161.238198] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  161.238200] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.238203] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.238205] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  161.238207] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.238209] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.364031] usb 2-3: reset high-speed USB device number 122 using ehci-pci
[  161.507966] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  161.508356] zd1211rw 2-3:1.0: phy0
[  161.508400] usbcore: registered new interface driver zd1211rw
[  161.661575] zd1211rw 2-3:1.0: firmware version 4725
[  161.714576] zd1211rw 2-3:1.0: zd1211b chip 0586:3410 v4810 high 00-13-49 AL2230_RF pa0 g---S
[  161.815628] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  161.816123] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  161.817428] cfg80211: Calling CRDA for country: DE
[  161.822488] cfg80211: Regulatory domain changed to country: DE
[  161.822495] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  161.822500] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  161.822504] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  161.822508] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  161.822512] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[  161.822515] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  164.520827] wlan0: authenticate with 5c:7d:5e:cc:0a:c6
[  164.653308] wlan0: send auth to 5c:7d:5e:cc:0a:c6 (try 1/3)
[  164.655000] wlan0: authenticated
[  164.656059] wlan0: associate with 5c:7d:5e:cc:0a:c6 (try 1/3)
[  164.664216] wlan0: RX AssocResp from 5c:7d:5e:cc:0a:c6 (capab=0x411 status=0 aid=2)
[  164.664965] wlan0: associated
[  164.665004] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  164.708848] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  164.708860] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  170.720026] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  170.720039] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  176.732039] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  176.732052] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  182.744108] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  182.744122] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  188.756019] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  188.756032] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  194.768036] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  194.768049] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  200.780030] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  200.780043] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  206.792030] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  206.792043] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  212.804030] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  212.804044] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  218.816018] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  218.816031] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  224.828024] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  224.828037] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  230.840016] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  230.840029] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  236.852032] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  236.852045] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  242.864033] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  242.864045] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  248.876039] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  248.876052] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  254.888036] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  254.888046] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  260.900038] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  260.900052] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  266.912025] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  266.912038] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  272.924040] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  272.924055] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  278.936040] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  278.936055] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  284.948045] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  284.948058] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  290.960036] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  290.960049] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  296.972037] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  296.972050] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  302.984017] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  302.984031] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  308.996024] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  308.996035] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  315.008023] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  315.008036] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  321.020040] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  321.020054] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  327.032025] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  327.032038] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  333.044029] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  333.044042] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  339.056025] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  339.056038] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  345.068026] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  345.068039] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  351.080041] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  351.080054] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
[  357.092028] mei_me 0000:00:03.0: reset: connect/disconnect timeout.
[  357.092041] mei_me 0000:00:03.0: unexpected reset: dev_state = RESETTING
```

---

### Post by varunendra on 2014-02-02
Have no experience about this, but does dmesg spit out same stuff if you plug in the adapter AFTER the OS has loaded and is ready to work? Or does the adapter get recognized quicker in that case?

Also, does the problem NOT exist on the previous version of Ubuntu? That is, if you have its ISO or live USB to test that.

---

