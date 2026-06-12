---
title: "Problems with bluetooth USB dongle"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by garlicsalt2 on 2008-03-02
Okay, not at all sure where to begin.

As soon as I plug in my Bluetooth USB Dongle, the console is flooded with the following message:

[ 9938.541507] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.541520] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.541523] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.541526] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.551500] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.551511] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.551514] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.561505] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.561520] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
[ 9938.561523] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92

This happens continuously, until I unplug it. If i stop bluetooth services first, ie, "sudo /etc/init.d/bluetooth stop", or "sudo killall hcid", then this does not occur.

hciconfig reveals:
hci0:   Type: USB
        BD Address: 11:11:11:11:11:11 ACL MTU: 672:3 SCO MTU: 48:1
        UP RUNNING
        RX bytes:17172108 acl:0 sco:336674 events:38 errors:0
        TX bytes:655 acl:0 sco:0 commands:38 errors:0

lsusb, gives me thus:
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 0e5e:6622
Bus 003 Device 002: ID 059b:0001 Iomega Corp. Zip 100 (Type 1)
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Yes, the device MAC address is correct; yes, I do have an Iomega Zip 100 USB drive connected; yes I have tried it without any other USB devices installed, and yes, I have tried moving the dongle to other USB ports. No noticeable differences encountered.

Is there anything else that I can try? The device works flawlessly under Windows 2000 Pro, and Windows XP Pro.

---

