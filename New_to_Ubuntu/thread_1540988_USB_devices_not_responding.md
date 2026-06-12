---
title: "USB devices not responding?"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by wallpaper_thief on 2010-07-28
My USB devices are taking an abnormally long time to mount. I sometimes plug them in then come back later to see if they loaded. Any suggestions?

anyway to manually force usb devices to mount if they're not showing up in /dev/?

---

### Post by cariboo on 2010-07-28
What does dmesg tell you when you have plugged in your device?

You can check by going to System->Administration->Log File Viewer, or open a terminal and type:

```
dmesg
```

---

### Post by wallpaper_thief on 2010-07-28
> **cariboo907 said:**
> What does dmesg tell you when you have plugged in your device?

You can check by going to System->Administration->Log File Viewer, or open a terminal and type:

```
dmesg
```


[   11.461300] usb-storage: device scan complete
[   11.463166] usb-storage: device scan complete
[   11.463265] scsi 11:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   11.465277] scsi 12:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[   11.484267] sr1: scsi-1 drive
[   11.484341] sr 11:0:0:0: Attached scsi CD-ROM sr1
[   11.484378] sr 11:0:0:0: Attached scsi generic sg7 type 5
[   11.484476] sd 12:0:0:0: Attached scsi generic sg8 type 0
[   11.493134] sd 12:0:0:0: [sdg] Attached SCSI removable disk
[   19.121260] udev: starting version 151
[   19.158066] EDAC MC: Ver: 2.1.0 Jul  5 2010
[   19.166028] lp: driver loaded but no devices found
[   19.170086] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   19.170089] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.170295] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.179147] Adding 6384632k swap on /dev/sda5.  Priority:-1 extents:1 across:6384632k 
[   19.204884] EDAC amd64_edac:  Ver: 3.2.0 Jul  5 2010
[   19.205888] vga16fb: initializing
[   19.205891] vga16fb: mapped to 0xffff8800000a0000
[   19.205939] fb0: VGA16 VGA frame buffer device
[   19.209926] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   19.210054] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   19.210055]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   19.210056]  (Note that use of the override may cause unknown side effects.)
[   19.210125] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   19.210911] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   19.210914] Disabling lock debugging due to kernel taint
[   19.255344] [fglrx] Maximum main memory to use for locked dma buffers: 3552 MBytes.
[   19.255370] [fglrx]   vendor: 1002 device: 9715 count: 1
[   19.255574] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[   19.255585] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.255588] pci 0000:01:05.0: setting latency timer to 64
[   19.255792] [fglrx] Kernel PAT support is enabled
[   19.255806] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   19.263843] usbcore: registered new interface driver hiddev
[   19.266204] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3.1/1-3.1:1.0/input/input3
[   19.266264] generic-usb 0003:413C:2005.0001: input,hidraw0: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:12.2-3.1/input0
[   19.266282] usbcore: registered new interface driver usbhid
[   19.266284] usbhid: v2.6:USB HID core driver
[   19.267216] type=1505 audit(1280335757.543:2):  operation="profile_load" pid=725 name="/sbin/dhclient3"
[   19.267399] type=1505 audit(1280335757.543:3):  operation="profile_load" pid=725 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.267501] type=1505 audit(1280335757.543:4):  operation="profile_load" pid=725 name="/usr/lib/connman/scripts/dhclient-script"
[   19.320632] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.348993] Console: switching to colour frame buffer device 80x30
[   19.367908] usbcore: registered new interface driver usbserial
[   19.367921] USB Serial support registered for generic
[   19.367952] usbcore: registered new interface driver usbserial_generic
[   19.367952] usbserial: USB Serial Driver core
[   19.591792] USB Serial support registered for GSM modem (1-port)
[   19.591830] option 2-4:1.0: GSM modem (1-port) converter detected
[   19.591908] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
[   19.591916] option 2-4:1.1: GSM modem (1-port) converter detected
[   19.591944] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
[   19.591951] option 2-4:1.2: GSM modem (1-port) converter detected
[   19.591979] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
[   19.591990] option 2-4:1.5: GSM modem (1-port) converter detected
[   19.592017] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB3
[   19.592025] usbcore: registered new interface driver option
[   19.592026] option: v0.7.2:USB Driver for GSM modems
[   19.607499] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   19.607536] HDA Intel 0000:01:05.1: setting latency timer to 64
[   19.863071] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   20.023502] type=1505 audit(1280335758.300:5):  operation="profile_load" pid=1012 name="/usr/share/gdm/guest-session/Xsession"
[   20.024393] type=1505 audit(1280335758.300:6):  operation="profile_replace" pid=1013 name="/sbin/dhclient3"
[   20.024582] type=1505 audit(1280335758.300:7):  operation="profile_replace" pid=1013 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.024687] type=1505 audit(1280335758.300:8):  operation="profile_replace" pid=1013 name="/usr/lib/connman/scripts/dhclient-script"
[   20.026372] type=1505 audit(1280335758.300:9):  operation="profile_load" pid=1014 name="/usr/bin/evince"
[   20.028668] type=1505 audit(1280335758.300:10):  operation="profile_load" pid=1014 name="/usr/bin/evince-previewer"
[   20.030144] type=1505 audit(1280335758.310:11):  operation="profile_load" pid=1014 name="/usr/bin/evince-thumbnailer"
[   20.125433] r8169: eth0: link down
[   20.125824] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.442248] kvm: Nested Virtualization enabled
[   20.442252] kvm: Nested Paging enabled


One is plugged in, but the other is still not working or showing up. Also, how far back do you want me to copy?

---

### Post by wallpaper_thief on 2010-07-29
bump

---

