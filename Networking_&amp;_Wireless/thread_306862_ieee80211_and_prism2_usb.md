---
title: "ieee80211 and prism2_usb"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by hdixon on 2006-11-25
I've installed Ubuntu 6.10 and was trying to get a Dlink DWL-122 working. I've been following some threads at 

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

regarding this. Ive installed the linux-wlan-ng pkg. The device is listed in lsmod. The prism2 driver is loaded. ifconfig shows wlan0 and I have routes in the routing table.

The how-to above shows the following output for lsmod | grep prism:

$ lsmod | grep prism
prism2_usb    xxxxx           0
ieee80211     xxxxx           1 prism2_usb
usbcore       xxxxx           3 prism2_usb,ohci_hcd

I have both the prism2 and ieee80211 modules loaded but I dont have ieee80211 being used(linked to/referenced) by the prism2 driver as in the output above. My output is:
$ lsmod | grep prism
prism2_usb    xxxxx           0
usbcore       xxxxx           4 prism2_usb,usbhid, uhci_hcd

I also have an old 3com pci card in this box but its currently disabled.
I'm assuming my problem is the ieee80211 and prism2. If so is there a module config file or something similar that i need to edit to get this going?

Thank you for any assistance.

hdixon

---

### Post by zgornel on 2006-11-27
What is the problem ?

---

### Post by wpowel on 2006-12-20
Did you ever get a solution?  I have the same problem.  The stick loads and is recognized by the kernel.  The stick can see the access point and identifies it correctly by MAC address, has correct essid, etc.  However, it says it is trying to obtain an IP address by DHCP (which it should), but sniffing the wireless network shows absolutely no traffic from the stick to the access point.

I've read the same HOWTO and have the same lsmod output as you.  I'm suspicious that the stick can't talk ieee80211 unless it can associate with that module.

---

