---
title: "USB wireless device listing as eth1"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Atreus12 on 2007-01-20
I am using Ubuntu 6.06 and have sucessfully configured wireless before, but I am running into some troubles this time.

I followed a guide on how to install ndiswrapper, and that is running fine. But when I plug the usb device in, it shows up under eth1, not wlan0. How do I change this?

-Andrew

---

### Post by Atreus12 on 2007-01-20
Anyone? I'm pretty sure this is the reason it isn't working. I just want it recognized as wlan0 instead of eth0.

-Andrew

---

### Post by heathen on 2007-01-20
is it a problem being eth1?  my laptop does that... never really thought about it being an issue..

---

### Post by Floppyjoe on 2007-01-20
My laptop shows up as eth1 also but i can still connect with it. I think it screws up some programs like network manager though.

---

### Post by az on 2007-01-20
> **Atreus12 said:**
> I am using Ubuntu 6.06 and have sucessfully configured wireless before, but I am running into some troubles this time.

I followed a guide on how to install ndiswrapper, and that is running fine. But when I plug the usb device in, it shows up under eth1, not wlan0. How do I change this?

-Andrew

A few wireless devices use ethx instead of wlanx.  That's not your problem.

Type

tail -f /var/log/messages
in a terminal and then plug the thing into your usb port.  Boot the computer beforehand without the thing in so that is the first time it is plugged in.  Post the output after a few seconds.

---

### Post by Atreus12 on 2007-01-20
> 
Jan 21 02:35:02 localhost syslogd 1.4.1#17ubuntu7: restart.
Jan 21 02:55:02 localhost -- MARK --
Jan 21 03:08:26 localhost kernel: [17181952.380000] e100: eth0: e100_watchdog: link down
Jan 21 03:08:34 localhost kernel: [17181960.536000] usb 5-6: new high speed USB device using ehci_hcd and address 2
Jan 21 03:08:34 localhost kernel: [17181960.788000] usb 5-6: reset high speed USB device using ehci_hcd and address 2
Jan 21 03:08:34 localhost kernel: [17181960.948000] ndiswrapper: driver wusb54g (The Cisco-Linksys, LLC.,01/12/2004, 1.0.8.0) loaded
Jan 21 03:08:36 localhost kernel: [17181963.048000] wlan0: vendor: 'Linksys Wireless-G USB Network Adapter'
Jan 21 03:08:36 localhost kernel: [17181963.048000] wlan0: ethernet device 00:0c:41:fb:87:80 using NDIS driver wusb54g, 1915:2234.F.conf
Jan 21 03:08:36 localhost kernel: [17181963.048000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Jan 21 03:08:37 localhost kernel: [17181963.120000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Jan 21 03:08:37 localhost kernel: [17181963.120000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan 21 03:08:37 localhost kernel: [17181963.140000] usbcore: registered new driver islusb


I don't know why, but after shutting down for 4+ hours, it registers as wlan0, and works. I've had this happen before, where it showed up as eth0 and wouldn't work. I don't know why, but for some reason it needs to be wlan0.

Anyway, wireless is working now. =D> 

-Andrew

---

