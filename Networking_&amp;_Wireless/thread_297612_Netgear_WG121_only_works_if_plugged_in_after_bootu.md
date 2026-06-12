---
title: "Netgear WG121 only works if plugged in after bootup"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by oimon on 2006-11-11
Hello
After a fresh install of edgy, i have a problem where, if my usb wireless card (netgear wg121) is plugged in a boot-time, it detects as net2280+PCI (according to dmesg output). 

Nov 11 13:35:01 newt kernel: [17180343.276000] usb 5-3: new high speed USB device using ehci_hcd and address 2
Nov 11 13:35:01 newt kernel: [17180343.408000] usb 5-3: configuration #1 chosen from 1 choice
Nov 11 13:35:01 newt kernel: [17180343.540000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Nov 11 13:35:01 newt kernel: [17180343.540000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov 11 13:35:01 newt kernel: [17180343.716000] islusb: suitable configuration found for net2280 + PCI device
Nov 11 13:35:02 newt kernel: [17180344.152000] usbcore: registered new driver islusb

This shows as eth0 and doesn't work

However if I plug in the usb connection AFTER boot time, I get a wlan0 device which works


ov 11 17:14:33 newt kernel: [17179692.076000] usb 5-4: new high speed USB device using ehci_hcd and address 2
Nov 11 17:14:33 newt kernel: [17179692.212000] usb 5-4: configuration #1 chosen from 1 choice
Nov 11 17:14:34 newt kernel: [17179692.256000] ndiswrapper: driver netwg121 (NETGEAR, Inc.,11/13/2003, 1.0.5.1000) loaded
Nov 11 17:14:36 newt kernel: [17179694.856000] wlan0: vendor: 'NETGEAR WG121 802.11g Wireless USB2.0 Adapter'
Nov 11 17:14:36 newt kernel: [17179694.856000] wlan0: ndiswrapper ethernet device 00:09:5b:a2:24:d0 using driver netwg121, 0846:4210.F.conf
Nov 11 17:14:36 newt kernel: [17179694.856000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Nov 11 17:14:36 newt kernel: [17179695.004000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Nov 11 17:14:36 newt kernel: [17179695.004000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov 11 17:14:36 newt kernel: [17179695.112000] usbcore: registered new driver islusb



Weird...can anyone help? I added the following to the modprobe.d/blacklist file , to see if it would help...(but no)


blacklist islsm
blacklist islusb
blacklist lslsm_usb
blacklist islsm_device
blacklist prism2_usb
blacklist islsm_pci
blacklist net2280


thanks
oimon

---

### Post by oimon on 2006-11-11
Arrrrrrrrrrrgh! Thats what comes of doing ubuntu installations with the flu....

I found my problem was due to a typo in my blacklist file
blacklist lslsm_usb
should be
blacklist islsm_usb

I notice this thread was linked by another thread - can I assist? My card is working again now. The key is to blacklist the prism stuff (appears with eth0) and use ndiswrapper (which appears as wlan0)
I am using ndiswrapper 1.16 and 2.6.17.10 kernel (edgy)

---

### Post by FrodoB on 2006-11-11
Could you be kind enough to take a look at this post 

[http://www.ubuntuforums.org/showthread.php?t=294240](http://www.ubuntuforums.org/showthread.php?t=294240)

and see if you can help the yawnster get his WG121 working as you have. 

It seems that the procedure that you followed needs to be documented for other folks. 

Thanks in advance for any help that you may provide.

---

