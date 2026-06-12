---
title: "moto4lin doesnt work"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by u-bar on 2007-04-21
hi,
i have a motorola v3c, and i have been trying to get it to connect to linux, im using Kubuntu fiesty.
when i plug the phone in, "dmesg" reads: 
> 
[ 5872.063037] usb 1-2: USB disconnect, address 19
[ 5875.322238] usb 1-2: new full speed USB device using uhci_hcd and address 20
[ 5875.489405] usb 1-2: configuration #1 chosen from 2 choices
[ 5875.491392] cdc_acm 1-2:1.0: ttyACM0: USB ACM device


and when i start moto4lin (which i installed from amptitude repositories)
it says:
> 
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: OK 
[info] Phone answer: OK 
[info] Phone pluged as P2K


but when i hit"connect":
> [info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name

"dmesg":
> [ 5891.570931] usb 1-2: config 1 has an invalid interface number: 6 but max is 3
[ 5891.570944] usb 1-2: config 1 has an invalid interface number: 8 but max is 3
[ 5891.570950] usb 1-2: config 1 has no interface number 2
[ 5891.570953] usb 1-2: config 1 has no interface number 3
[ 5891.583111] usb 1-2: configuration #1 chosen from 1 choice
[ 5891.586097] cdc_acm 1-2:1.0: ttyACM0: USB ACM device


p2ktest (which i compiled myself):
> P2k Test
Device list:
0000:0000: [Linux 2.6.20-15-generic uhci_hcd] [UHCI Host Controller]
0000:0000: [Linux 2.6.20-15-generic uhci_hcd] [UHCI Host Controller]
22b8:2a61: [Motorola Inc.] [Motorola V3c]
03f0:0904: [Hewlett-Packard] [DeskJet 845C]
04cc:1122: [] []
0000:0000: [Linux 2.6.20-15-generic uhci_hcd] [UHCI Host Controller]
No phone found.


using minicom, i have been able to get the phone model ("ati0"), and manually switch it to P2K mode ("at+mode=8"), but no change (2a62 changed to 2a61).
i get the same results with "Detach kernel driver on", and "Update list" (naturally) doesnt help...
my configuration is: 
device: /dev/ttyACM0
at vendor id: 22b8
at product id: 2a62
p2k vendor id: 22b8
p2k product id: 22b1


can anyone please help me? :( 
[SIZE="1"]sorry for all the quotations...[/SIZE]

---

### Post by u-bar on 2007-04-27
anyone? this is realy important :(

---

### Post by Erlander on 2007-04-27
I haven't had any luck with my Razr V3x but this thread may help you.

[http://ubuntuforums.org/showthread.php?t=56253](http://ubuntuforums.org/showthread.php?t=56253)

Rob

---

### Post by u-bar on 2007-04-28
i already read that thread, several times, but nothing seems to work...
is there an alternative? what do you do to upload and download files from/to your phone?

i noticed that all the people who had some success with moto4lin had "usb-3-1" in there "dmesg", is there any way to update these kernel drivers?

---

### Post by Erlander on 2007-04-28
Mine isn't working either.

I hadn't noticed the usb 3.1.  You really have been into the fine detail.  Mine is 3.0

```
25.605921] USB Universal Host Controller Interface driver v3.0
```

and I'm using Feisty 7.04 which has a very recent kernel.

Surely we don't have to compile a kernel.

Rob

---

### Post by u-bar on 2007-05-02
"dmesg" outputs on connect:
> usb 1-2: config 1 has no interface number 2

well... i think its right :)
'usbview' shows that although there are 2 interfaces, their count begins at 0, so there realy isnt an interface with the number 2! (btw, for some odd reason, now that i have connected my phone, there are interfaces numbered 6 and 8 )

> Motorola V3c
Manufacturer: Motorola Inc.
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 22b8
Product Id: 2a61
Revision Number:  0.01

Config Number: 1
	Number of Interfaces: 4
	Attributes: c0
	MaxPower Needed: 100mA

	-Interface Number: 0
		--Name: (none)
		--Alternate Number: 0
		--Class: 02(comm.) 
		--Sub Class: 2
		--Protocol: 1
		--Number of Endpoints: 1

			---Endpoint Address: 81
			---Direction: in
			---Attribute: 3
			---Type: Int.
			---Max Packet Size: 16
			---Interval: 32ms

	-Interface Number: 1
		--Name: (none)
		--Alternate Number: 0
		--Class: 0a(data ) 
		--Sub Class: 0
		--Protocol: 0
		--Number of Endpoints: 2

			---Endpoint Address: 82
			---Direction: in
			---Attribute: 2
			---Type: Bulk
			---Max Packet Size: 64
			---Interval: 0ms

			---Endpoint Address: 02
			---Direction: out
			---Attribute: 2
			---Type: Bulk
			---Max Packet Size: 64
			---Interval: 0ms


who selects interfaces numbered 3 and 2? if its moto4lin, is it possible to change this in the source code? or... is it cdc_acm?

---

### Post by JunCTionS on 2007-12-05
oh well... this didn't work for me... but I guess it might for some of you:

[http://www.seto.org/mt-diary/archives/2005/12/moto4lin_linuxm.html](http://www.seto.org/mt-diary/archives/2005/12/moto4lin_linuxm.html)

he's got a V3c just like me (and kubuntu).

in my case it seems to have done something different than before. but now I get:

```
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: OK 
[debug] nread=-1, errno=11
[error] Unable to connect
```

in the program log window and in the console: 

```
doActConnect
doActConnect
P2kProc::doConnect()
Unable to connect: Resource temporarily unavailable

```

any suggestions? I'll keep googling it.

---

