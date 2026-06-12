---
title: "ndisgtk &amp; WLI2-USB2-G54"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Juul on 2008-06-13
Hi,

So I'm trying to let my wireless wifi adapter (WLI2-USB2-G54) work. But now I've found the probably correct files ndisgtk won't start anymore I think it might have something to do with the ndiswrapper I tried to install which didn't work.
So when I now start ndisgtk it directly crashes. I'm totally a newbie so every help is welcome and I already totaly uninstalled ndisgtk and then installed it again but it still crashes directly.

---

### Post by Juul on 2008-06-13
Oke i fixed it now and the driver is installed succesfully but how can I get a wireless connection becausse in the network settings there isn't a wireless setting ;)

And when i do iwconfig there is said "no wireless connection"...

---

### Post by Juul on 2008-06-13
I now found something which could be intresting when I reconnected the usb cable and then used dmesg the latest lines where:
> [  427.438642] usb 2-9: USB disconnect, address 2
[  429.094899] usb 2-9: new high speed USB device using ehci_hcd and address 4
[  429.168691] usb 2-9: configuration #1 chosen from 1 choice
[  429.239095] usb 2-9: reset high speed USB device using ehci_hcd and address 4
[  429.315052] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  429.315060] ndiswrapper (load_sys_files:206): couldn't prepare driver 'wusb54g_hack'
[  429.317247] ndiswrapper (load_wrap_driver:108): couldn't load driver wusb54g_hack; check system log for messages from 'loadndisdriver'

I did everything like said in this "how to": [http://ubuntuforums.org/showthread.php?t=527817]("http://ubuntuforums.org/showthread.php?t=527817")

---

