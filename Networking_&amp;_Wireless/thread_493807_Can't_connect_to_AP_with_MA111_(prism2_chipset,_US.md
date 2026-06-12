---
title: "Can't connect to AP with MA111 (prism2 chipset, USB)"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by MatBi on 2007-07-06
I'm trying to connect to my router wirelessy using a Netgear MA111; i'm running Feisty.
The device seems to be recognized, but there's no connection to the access point.
I disabled encryption in the AP, to make it easier.
I installed the packages linux-wlan-ng and followed the docs at:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
and some other posts.

Here's my actual status:

[FONT="Courier New"]# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:09:5B:B2:09:27
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:4368 (4.2 KiB)[/FONT]

A snippet from /etc/network/interfaces:
[FONT="Courier New"]iface wlan0 inet dhcp
        wireless_mode managed
        wireless_essid frittole
auto wlan0[/FONT]

lsusb gives thumbs up: 
[FONT="Courier New"]Bus 003 Device 002: ID 0846:4110 NetGear, Inc. MA111 WiFi (v1)[/FONT]

kernel module look ok:
[FONT="Courier New"]# lsmod | grep prism
prism2_usb             72964  0
p80211                 30860  1 prism2_usb
usbcore               130072  8 prism2_usb,ohci_hcd,uhci_hcd,ehci_hcd,usbhid,usb_storage,libusual
[/FONT]

if i restart the interface, on ifup i get:
[FONT="Courier New"]# ifup  wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:09:5b:b2:09:27
Sending on   LPF/wlan0/00:09:5b:b2:09:27
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/FONT]

As far as i understand, the "SET failed" errors are ok, because of the partial support for this chipset.
The AP is working fine with my XP laptop.
I'm not sure what am i doing wrong, and how to get more information. 
Can anyone please help me on this?

---

### Post by fredj on 2007-07-06
The set errors seem to show that with this driver you can't set the ESSID from your interfaces file.
Use the network icon in the taskbar, can you see your wireless network? Try to connect to it from
there.

---

### Post by az on 2007-07-06
Perhaps you need to update the firmware?
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb#head-d95a38acee91f65835afddd0a2bc973346e6a931](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb#head-d95a38acee91f65835afddd0a2bc973346e6a931)

---

### Post by MatBi on 2007-07-06
Thanks everybody for the quick answer. 
after some reboot, i managed to get a connection with 40 bits WEP. 
Weird...

---

