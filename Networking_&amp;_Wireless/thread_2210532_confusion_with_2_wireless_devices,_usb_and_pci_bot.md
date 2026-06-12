---
title: "confusion with 2 wireless devices, usb and pci both in the PC"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2014-03-11
I installed the PCI device and it works.
I then plugged in the usb device.
So network manager shows 2 wireless devices.
However I can not seem to turn on the usb device, I can still turn on the PCI device.
I was testing the wireless speed and thought to compare one to the other.

screens show the devices.
The broadcom br43legacy mn-730 device seems awful slow to me.

first pic shows pci device on and usb device off
sec pic shows both off
I can not turn off the pci device and turn on the usb device.

---

### Post by varunendra on 2014-03-14
Still on the quest?

> **sdowney717 said:**
> The broadcom br43legacy mn-730 device seems awful slow to me.

Hence why it's called "legacy" :p

From your description it seems there is no case when the USB adapter is turned on. If you turn the PCI adapter off using rfkill or hardware switch, does the USB one get used instead?

Please show us (while the USB one is plugged in) -
```
lspci -nnk | grep -iA2 net
lsusb
nm-tool
rfkill list
lsmod
cat /var/lib/NetworkManager/NetworkManager.state
```

---

