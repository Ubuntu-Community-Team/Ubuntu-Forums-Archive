---
title: "Linksys WUSB11 v2.5 not working in Ubuntu 6.10"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by galmeida2007 on 2007-02-05
I have a Linksys WUSB11 v2.5 usb wireless card. I have installed the package linux-wlan-ng.
But the card refuses to work. dmesg messages show errors, as it can be seen in the following fragment:

[17182441.468000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[17182441.620000] usb 2-2: config 1 has an invalid interface number: 1 but max is 0
[17182441.620000] usb 2-2: config 1 has no interface number 0
[17182441.628000] usb 2-2: configuration #1 chosen from 1 choice
[17182441.724000] p80211: exports duplicate symbol p80211netdev_hwremoved (owned by kernel)
[17182441.724000] p80211: exports duplicate symbol p80211netdev_hwremoved (owned by kernel)
[17182442.800000] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[17182442.800000] hfa384x_drvr_start: cmd_initialize() failed, result=-5
[17182442.800000] prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5

Does anybody know if this problem has been solved. Some years ago (2003 if I remember well) I was able to have this wireless card working under Topologilinux 4 using the same driver, with wep 128 bit encryption enabled. The only problem, due to a bug in the driver, is that I needed to unplug and plug again the card in order to make it work). After a hard disk problem that killed my Topologilinux 10 GB file containing the system in a NTFS partition, I decided to go the orthodox Linux way by repartitioning my hard drive and installing Ubuntu 6.10 Edgy Eft. Almost everything worked as a charm, with this remarkable exception.

It seems that the newer 2.6.17-10 kernel made the prism2_usb driver to fail with this wireless card. I've seen similar posts reporting this problem since 2005.

Hence, I've been forced to try the unorthodox ndiswrapper driver along with the Windows driver for this card, but things do not work as well as it should be. It works Ok without wep, but with wep 128 bit encoding it refuses to work. In that case I can ping successfully my access point and even outside sites in the Internet until I try to use my web browser. After that, even those pings fail. And in any case, wep encryption enabled or not, unplugging the card freezes the system. With the wlan-ng driver, unplugging the card does not freeze my system. 

I would appreciate any help to make this card work with 128 bit encryption enabled for any of those 2 drivers, although a native Linux driver solution like wlan-ng is better.

---

