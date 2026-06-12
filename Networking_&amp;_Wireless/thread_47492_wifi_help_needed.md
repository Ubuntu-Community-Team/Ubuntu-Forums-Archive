---
title: "wifi help needed"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by t2kburl on 2005-07-08
Hi. I am trying to connect a 2nd PC to my wireless network with ubuntu on it.
(the original is wired to the access point)
It has an Intel PRO/Wireless 2011B LAN USB connected to it.
When I installed ubuntu I selected it as  my internet connecting device (or something like that) buit it failed the config (no chance in the installer to config the WEP,etc)
So I proceeded with the installation and now, when I go to set up the wifi config in KDE Control center ... it cannot locate the wifi interface at all.  Where did it go? How do I locate it?   It does show up when I run~ lsusb
Any assistance would be greatly appreciated.

---

### Post by az on 2005-07-08
So you are trying to access a wireless router or an access point which is attached to a linux box which is attached to the net through a cable moedm or something?

Where does your internet plug into?

Also, what kind of device is your usb thinggie?  type dmesg after you plug and unlug it to show what kernel messages are displayed when it is recognised...

dmesg

---

### Post by t2kburl on 2005-07-08
sorry for the lacking clarity ... it is a USB wlan device. It connects to an Intel access point which is wired to the DSL modem and the other PC

here is the output of dmesg after unplugging it an plugging it in again:

ted@ubuntu:~$ dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:07.2: irq 10, io base 0xd400
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:07.3: irq 10, io base 0xd800
uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-2: new full speed USB device using uhci_hcd and address 2
usb 1-2: device descriptor read/64, error -71
usb 1-2: device descriptor read/64, error -71
usb 1-2: new full speed USB device using uhci_hcd and address 3
usb 1-2: device descriptor read/64, error -71
usb 1-2: device descriptor read/64, error -71
8139too Fast Ethernet driver 0.9.27
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: RealTek RTL8139 at 0xe000, 00:50:22:b0:6d:de, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 10 (level, low) -> IRQ 10
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
vga16fb: initializing
vga16fb: mapped to 0xc00a0000
Console: switching to colour frame buffer device 80x30
fb0: VGA16 VGA frame buffer device
eth0: no IPv6 routers present
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
ibm_acpi: ec object not found
usb 1-2: new full speed USB device using uhci_hcd and address 4
usb 1-2: config 1 has an invalid interface number: 1 but max is 0
usb 1-2: config 1 has no interface number 0
prism2usb_init: prism2_usb.o: 0.2.1-pre25 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb
usb 1-2: hald timed out on ep0in
usb 1-2: hald timed out on ep0in
ted@ubuntu:~$

I guess I'm too much of a nOOb to understand what that means

just a wild guess ... is prism2 the chipset?

---

### Post by kleeman on 2005-07-09
Your dmesg seems to show an eth0 interface as well. Do you have a wired network card as well as the usb wireless card? If you do you need to bring it down using ifconfig.

---

### Post by roblubbers on 2005-07-09
Do you know if the support for your card is build-in the kernel or do you have compile your own module?

---

### Post by t2kburl on 2005-07-09
I've been chipping away at this in another thread

[http://ubuntuforums.org/showthread.php?p=248045#post248045](http://ubuntuforums.org/showthread.php?p=248045#post248045)

I think i can pull eth0 down as soon as I can get wlan0 to come up at all

I have the drivers installed (now) ...  still having difficulties though

probably missing something stupid

---

