---
title: "RT2500 with an ASUS WL-167G - Help"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by boreal on 2005-12-04
Hi,

I am trying to use my ASUS wlan adapter with breezy. This device use a Ralink 2500 chipset that is supposed to be directly supported by breezy. When I plug my adapter, I have the following:

tail -f /var/log/message: Dec  4 20:13:46 localhost kernel: [  425.948528] usb 2-2: new full speed USB device using uhci_hcd and address 3
 
lsusb: Bus 002 Device 003: ID 0b05:1706 ASUSTek Computer, Inc.

lshw :
[INDENT]              *-usb UNCLAIMED
                   description: Generic USB device
                   product: 802.11g WLAN Drive
                   vendor: ASUS
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: maxpower=300mA speed=12.0MB/s

[/INDENT]
lsmod | grep rt2500: nothing is found

Has anyboy already managed to make such an USB wlan adapter work ? What can be the problem ?

Any help would be greatly appreciated.

---

### Post by Lambert on 2005-12-04
I show this using a newer driver (rt2x00) and not the rt2500. The newer driver is in beta stage currently and not in breezy.
[http://linux-wless.passys.nl/query_part.php?brandname=Asus&zoek=brandname](http://linux-wless.passys.nl/query_part.php?brandname=Asus&zoek=brandname)

[http://rt2x00.serialmonkey.com/wiki/index.php/Rt2x00_beta](http://rt2x00.serialmonkey.com/wiki/index.php/Rt2x00_beta)

If you want to compile driver.
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

