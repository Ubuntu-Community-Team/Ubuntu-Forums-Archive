---
title: "Flaky Bluetooth file sharing- Ubuntu PC to/from Samsung mobile phone"
date: 2024-01-09
forum: Networking &amp; Wireless
---

### Post by makem2 on 2024-01-09
I am using Ubuntu 23.04 on a desktop pc with the xfce4-indicator-plugin for default Bluetooth.

Having paired the pc and my Samsung A54 mobile Bluetooth I send files from to pc to the mobile phone. One or maybe two files transfer without a problem but I then start getting errors and cannot even make a connection which is always refused.

This is the flow:

1. Using the 'Send Files to Device' option in the above plugin, choosing the file and then the A54

2. Error occurred - connect to B4:0B:1D::3F:0C:9E: Permission denied (13) - B4:0B:1D:3F:0C:9E is A54 as shown in the Devices

3. Selecting 'Devices' from the plugin option I note that the A54 is trusted and paired. I then choose 'Send File' from the icon on the Devices list , choosing the A54. Navigate to the file and select 'Ok'

4. Error occurred - connect to B4:0B:1D:3F:0C:9E: Permission denied (13)

5. Using the 'Connect' option in the Devices menu I select 'Connect'

6. Connection Failed: br-connection-profile-unavailable

These errors occurred in the same short session during which I had previously successfully transferred 2 files.

The phone is new and was paired just before the session. I tried un-pairing and re-pairing with same results.

I hate to say this but, windows didn't have any problem.

I previously had an A51 and I seem to remember having an identical session with the same files in which I resorted to windows. However, after 3 years or so using an A51, I think it is time I asked for help as during those 3 years I did have Bluetooth problems quite often and I am wondering if it is my problem or if Bluetooth on Ubuntu is flaky and not fixed.

```
makem@makem-22:~$ hciconfig -a
hci0:	Type: Primary  Bus: USB
	BD Address: 8C:55:4A:9A:FA:00  ACL MTU: 1021:4  SCO MTU: 96:6
	UP RUNNING PSCAN 
	RX bytes:169492 acl:3379 sco:0 events:9102 errors:0
	TX bytes:1347194 acl:3713 sco:0 commands:4223 errors:0
	Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: PERIPHERAL ACCEPT 
	Name: 'makem-22'
	Class: 0x100104
	Service Classes: Object Transfer
	Device Class: Computer, Desktop workstation
	HCI Version: 5.2 (0xb)  Revision: 0x200f
	LMP Version: 5.2 (0xb)  Subversion: 0x200f
	Manufacturer: Intel Corp. (2)

```

---

