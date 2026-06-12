---
title: "USB Bluetooth Adapter Not Recognized"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by rjonesx on 2008-06-26
I have attempted to install an Insignia NS-BTHDST Headset and with no luck so far. I am on an HP Pavilian dv2000 laptop (AMD64) with Hardy Heron.

lsusb shows the following, where Bus

Bus 002 Device 011: ID 0a5c:4503 Broadcom Corp.
Bus 002 Device 010: ID 0a5c:4502 Broadcom Corp.
Bus 002 Device 009: ID 0a5c:4500 Broadcom Corp.
Bus 002 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0c45:62c0 Microdia
Bus 001 Device 001: ID 0000:0000

Where Bus 002 Device 011,010, and 009 are all Bluetooth USB device.

However, if I run hciconfig or hcitool, it shows nothing.

~# hciconfig scan
Can't get device info: No such device

:~# hcitool dev
Devices:

Any ideas? I would really like to get this working.

Russ

---

### Post by KenBW2 on 2008-06-26
My Belkin adapter wouldn't work either. I found the fix here:
[https://wiki.ubuntu.com/Belkin_F8T012xx1_USB_Adapter](https://wiki.ubuntu.com/Belkin_F8T012xx1_USB_Adapter)
> 
Works with Ubuntu 7.04 and 7.10 if you add "blacklist pegasus" in the file "/etc/modprobe.d/blacklist" and restart the system.

Maybe it could work for you as well?

---

### Post by rjonesx on 2008-10-27
Gave it a shot but no luck - thanks though.

Anyone have any ideas?

Looking a dmesg when I plug in the USB adapter, it appears that the device is being interpreted as HID instead of HCI...

:0b.0/usb2/2-6/2-6.2/2-6.2:1.0/input/input11
[  603.017742] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:0b.0-6.2
[  603.135248] usb 2-6.3: new full speed USB device using ohci_hcd and address 7
[  603.198291] usb 2-6.3: configuration #1 chosen from 1 choice
[  603.203373] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6.3/2-6.3:1.0/input/input12
[  603.217722] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:0b.0-6.3

---

### Post by go_beep_yourself on 2008-10-30
Having the same problem. Did you ever find a solution? Would be greatly appreciated!

---

### Post by Ferrat on 2008-10-30
I'm having a similar problem, I can find the USB dongle in termial, the GUI version that comes with Ubuntu 8.10 register that there is a Bluetooth device but doesn't seem to search with it, when ever I start the Wizard my bluetooth gets disconnected. 

```
icebreaker@iceblock:~$ hciconfig 
hci0:	Type: USB
	BD Address: 00:XX:XX:XX:XX:XX ACL MTU: 377:10 SCO MTU: 64:8
	UP RUNNING 
	RX bytes:675 acl:0 sco:0 events:20 errors:0
	TX bytes:620 acl:0 sco:0 commands:31 errors:0

```

however it looks like Ubuntu doesn't give the bluetooth adapter a name 

```

icebreaker@iceblock:~$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:XX:XX:XX:XX:XX ACL MTU: 377:10 SCO MTU: 64:8
	UP RUNNING 
	RX bytes:675 acl:0 sco:0 events:20 errors:0
	TX bytes:620 acl:0 sco:0 commands:31 errors:0
	Features: 0xff 0xfe 0x0d 0x38 0x08 0x18 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)

```

I have been able to use **hciconfig** and **hcitool** to set a name and even search for devices and find them but the only connect for a second with 
**hcitool cc XX:XX:XX:XX:XX:XX**
then the connection is lost and I have to connect again (like it's kicking me because of no linking, that's my guess anyway)

after 
icebreaker@iceblock:~$ [B]sudo hciconfig hci0 name NewBluetooth
[/B]

```

icebreaker@iceblock:~$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:XX:XX:XX:XX:XX ACL MTU: 377:10 SCO MTU: 64:8
	UP RUNNING 
	RX bytes:1312 acl:0 sco:0 events:36 errors:0
	TX bytes:940 acl:0 sco:0 commands:50 errors:0
	Features: 0xff 0xfe 0x0d 0x38 0x08 0x18 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: 
	Link mode: SLAVE ACCEPT 
	Name: 'NewBluetooth'
	Class: 0x000000
	Service Classes: Unspecified
	Device Class: Miscellaneous, 
	HCI Ver: 1.2 (0x2) HCI Rev: 0x0 LMP Ver: 1.2 (0x2) LMP Subver: 0x696f
	Manufacturer: Broadcom Corporation (15)

```

with name added I can search 

```

icebreaker@iceblock:~$ sudo hcitool scan
Scanning ...
	00:XX:XX:XX:XX:XX	Mobile
	00:XX:XX:XX:XX:XX	Nintendo RVL-CNT-01

```

without sudo, hcitool can't retrive name of the bluetooth devices.

```

icebreaker@iceblock:~$ sudo hcitool inq
Inquiring ...
	00:XX:XX:XX:XX:XX	clock offset: 0x68ab	class: 0x5a0204

```

That's as far as I come, after that there isn't much more I can do, connecting etc doesn't work as stated =/

---

### Post by paraplegicpanda on 2008-11-08
I'm having the same problems...
```
paraplegicpanda@hacktopix:~$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:0C:55:38:13:AF ACL MTU: 377:10 SCO MTU: 16:0
	UP RUNNING 
	RX bytes:657 acl:0 sco:0 events:18 errors:0
	TX bytes:363 acl:0 sco:0 commands:27 errors:0
	Features: 0xff 0xfe 0x0d 0x38 0x08 0x08 0x00 0x00
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)
```
I have pegasus blacklisted and there is no change. I have also tried using
```
sudo hciconfig -a
```
instead of
```
hciconfig -a
```
and no change.

When I tried changing the name
```
paraplegicpanda@hacktopix:~$ sudo hciconfig hci0 name topiXbt
[sudo] password for paraplegicpanda: 
Can't change local name on hci0: Connection timed out (110)
```

Scanning times out as well. Any more suggestions?

---

