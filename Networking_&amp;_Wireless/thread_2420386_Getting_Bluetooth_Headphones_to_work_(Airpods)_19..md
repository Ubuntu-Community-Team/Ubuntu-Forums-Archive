---
title: "Getting Bluetooth Headphones to work (Airpods) 19.04"
date: 2019-06-04
forum: Networking &amp; Wireless
---

### Post by phillyd177 on 2019-06-04
I can't get my airpods to connect to my 13in 2015 MacBook pro running Ubuntu 19.04, but they work on my 2012 MBP using Ubuntu 19.04.

It says device not set up and will load till it crashes if I try and click the device. I have tried every option I've seen online, none have worked.

lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm'
03:00.0 [COLOR=#CC0000]**Net**[/COLOR]work controller [0280]: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 01)
	Subsystem: Apple Inc. BCM43602 802.11ac Wireless LAN SoC [106b:0133]
	Kernel driver in use: brcmfmac
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:0273 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 001 Device 002: ID 05ac:8290 Apple, Inc. Bluetooth Host Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:	Type: Primary  Bus: USB
	BD Address: 98:01:A7:8E:46:AC  ACL MTU: 1021:8  SCO MTU: 64:1
	DOWN 
	RX bytes:2554 acl:0 sco:0 events:134 errors:0
	TX bytes:5789 acl:0 sco:0 commands:127 errors:0
	Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: SLAVE ACCEPT 

[    0.141377] Spectre V2 : Enabling Restricted Speculation for [COLOR=#CC0000]**firm**[/COLOR]ware calls
[    0.166778] ACPI: [[COLOR=#CC0000]**Firm**[/COLOR]ware Bug]: BIOS _OSI(Linux) query ignored
[    0.181268] acpi PNP0A08:00: [[COLOR=#CC0000]**Firm**[/COLOR]ware Info]: MMCONFIG for domain 0000 [bus 00-9b] only partially covers this bridge
[    1.482061] usb 1-3: Product: [COLOR=#CC0000]**Blue**[/COLOR]tooth USB Host Controller
[    1.779772] input: Broadcom Corp. [COLOR=#CC0000]**Blue**[/COLOR]tooth USB Host Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:05AC:8290.0001/input/input4
[    1.836191] hid-generic 0003:05AC:8290.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp. [COLOR=#CC0000]**Blue**[/COLOR]tooth USB Host Controller] on usb-0000:00:14.0-3/input0
[    1.836296] input: Broadcom Corp. [COLOR=#CC0000]**Blue**[/COLOR]tooth USB Host Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:05AC:8290.0002/input/input5
[    1.836365] hid-generic 0003:05AC:8290.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp. [COLOR=#CC0000]**Blue**[/COLOR]tooth USB Host Controller] on usb-0000:00:14.0-3/input1
[    3.046601] [COLOR=#CC0000]**Blue**[/COLOR]tooth: Core ver 2.22
[    3.046619] [COLOR=#CC0000]**Blue**[/COLOR]tooth: HCI device and connection manager initialized
[    3.046715] [COLOR=#CC0000]**Blue**[/COLOR]tooth: HCI socket layer initialized
[    3.046718] [COLOR=#CC0000]**Blue**[/COLOR]tooth: L2CAP socket layer initialized
[    3.046722] [COLOR=#CC0000]**Blue**[/COLOR]tooth: SCO socket layer initialized
[    3.127332] brcmfmac 0000:03:00.0: Direct [COLOR=#CC0000]**firm**[/COLOR]ware load for brcm/brcmfmac43602-pcie.Apple Inc.-MacBookPro12,1.txt failed with error -2
[    3.127345] brcmfmac 0000:03:00.0: Direct [COLOR=#CC0000]**firm**[/COLOR]ware load for brcm/brcmfmac43602-pcie.txt failed with error -2
[    3.221960] [COLOR=#CC0000]**Blue**[/COLOR]tooth: hci0: BCM: chip id 102 build 0725
[    3.222917] [COLOR=#CC0000]**Blue**[/COLOR]tooth: hci0: BCM: product 05ac:8290
[    3.224130] [COLOR=#CC0000]**Blue**[/COLOR]tooth: hci0: BCM: features 0x2f
[    3.239922] [COLOR=#CC0000]**Blue**[/COLOR]tooth: hci0: phil-MacBookPro
[    3.663684] brcmfmac: brcmf_c_preinit_dcmds: [COLOR=#CC0000]**Firm**[/COLOR]ware: BCM43602/1 wl0: Nov 10 2015 06:38:10 version 7.35.177.61 (r598657) FWID 01-ea662a8c
[    5.144172] [COLOR=#CC0000]**Blue**[/COLOR]tooth: BNEP (Ethernet Emulation) ver 1.3
[    5.144173] [COLOR=#CC0000]**Blue**[/COLOR]tooth: BNEP filters: protocol multicast
[    5.144177] [COLOR=#CC0000]**Blue**[/COLOR]tooth: BNEP socket layer initialized
[   52.670243] [COLOR=#CC0000]**Blue**[/COLOR]tooth: RFCOMM TTY layer initialized
[   52.670251] [COLOR=#CC0000]**Blue**[/COLOR]tooth: RFCOMM socket layer initialized
[   52.670256] [COLOR=#CC0000]**Blue**[/COLOR]tooth: RFCOMM ver 1.11

---

### Post by #&amp;thj^% on 2019-06-04
Please use Code Tags with wrapping terminal outputs, see my sig if not sure how.
**In "/etc/bluetooth/main.conf"**
Set or Edit:
```
ControllerMode = bredr
```
And some have had to use:
```
ControllerMode = dual ##This may be the best for 18.04 and newer
```
Restart bluetooth service:
```
sudo systemctl restart bluetooth
```
Now try to pair your AirPods! Good Luck ;)

---

