---
title: "Detecting Hotplug Devices"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by ngensys on 2005-08-21
Hi guys,

Currently I'm trying to stop my USB ADSL modem from being detected during startup. I can see a message "Detecting Hotplug Devices" and my modem's lights turn on. How can I stop this?
I added dabusb in the blacklist file.

By the way, I ran lsusb & dmesg and got the following:

So which driver should I put in the blacklist file? I tried many things but still the modem is detected.
[COLOR=DarkGreen]
[I]root@freedom:/home/freedom # lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 06b9:a5a5 Alcatel Telecom DynaMiTe Modem
Bus 001 Device 001: ID 0000:0000

root@freedom:/home/freedom # dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xe400
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xe800
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xec00
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.3: irq 21, pci mem 0xdfffff00
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
irda_init()
NET: Registered protocol family 23
usb 1-1: USB disconnect, address 2
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
usb 1-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: new low speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:10.1-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ts: Compaq touchscreen protocol output
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root
root@freedom:/home/freedom #[/I][/COLOR]


Please help.....Thanks... ??:

---

### Post by mlomker on 2005-09-19
> 
I added dabusb in the blacklist file.


I've been playing with the blacklist file, myself, and it doesn't seem to function in Ubuntu.  I'm wondering if it hasn't been enabled in the hotplug scripts.

---

