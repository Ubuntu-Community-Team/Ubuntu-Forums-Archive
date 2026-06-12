---
title: "Bluetooth dongle can't detect any devices or vice versa"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by AnttiT on 2008-08-08
Hello,

I just got a bluetooth dongle. My system seems to be able to detect the dongle itself just fine: 
------------------
$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:14:35:00:16:D4 ACL MTU: 310:10 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:3272 acl:0 sco:0 events:69 errors:0
	TX bytes:773 acl:0 sco:0 commands:65 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'antti-laptop-0'
	Class: 0x18010c
	Service Classes: Capturing, Object Transfer
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0xc5c LMP Ver: 2.0 (0x3) LMP Subver: 0xc5c
	Manufacturer: Cambridge Silicon Radio (10)
-----------

But after this the comes the problem:
-----------
$ hcitool scan
Scanning ...
$
-----------
And that's it (doesn't find anything). Only thing that happens is that the led on the dongle is constantly on during the scan. When the dongle is idle the led blinks every two seconds or so.

Currently I'm trying to detect my phone (Nokia E65) which has Bluetooth enabled and visible. Also the phone is unable to detect the dongle although the dongle has been set up as "Visible and connectable for other devices" in Bluetooth preferences.

So any ideas? How can diagnose this more?

-antti

---

