---
title: "Ubuntu 19.10 recognizing Neatgear ac1900 as Netgear Integrated Camera?"
date: 2019-12-23
forum: Networking &amp; Wireless
---

### Post by fired-spenser on 2019-12-23
I have a Lenovo c940 where I recently installed Ubuntu. I am trying to use a USB wifi adapter to improve my range/signal.  I plug the Netgear ac1900 in to the usb and the system doesn't seem to recognize it...  It doesn't appear when I check with iwconfig or ifconfig.

When I run lsusb, it appears on the list as a "Neatgear, Inc. Integrated Camera."  (If I unplug the adapter and run the command again, this entry disappears from the list.)

Thoughts?  System is up to date...  Not sure where else to look or start.

Thanks!

---

### Post by praseodym on 2019-12-23
Please show
```

lsusb
usb-devices
```with the stick plugged

---

### Post by fired-spenser on 2019-12-23
> **praseodym said:**
> Please show
```

lsusb
usb-devices
```with the stick plugged

Thanks for taking the time to reply. Happy to provide whatever info may be helpful... I put the questionable entry in bold. 

lsusb
Bus 004 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**Bus 003 Device 010: ID 0846:9054 NetGear, Inc. Integrated Camera**
Bus 003 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 06cb:00be Synaptics, Inc. 
Bus 003 Device 005: ID 8087:0026 Intel Corp. 
Bus 003 Device 002: ID 04f2:b61e Chicony Electronics Co., Ltd Integrated Camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And here it is with the dongle unplugged:

lsusb
Bus 004 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 003: ID 06cb:00be Synaptics, Inc. 
Bus 003 Device 005: ID 8087:0026 Intel Corp. 
Bus 003 Device 002: ID 04f2:b61e Chicony Electronics Co., Ltd Integrated Camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by praseodym on 2019-12-23
[https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426](https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426)

Seems to be this one

Edit: Yes, it is
```

modprobe -c | grep -i "0846.*9054"
alias usb:v[COLOR="#FF0000"]0846[/COLOR]p[COLOR="#FF0000"]9054[/COLOR]d*dc*dsc*dp*ic*isc*ip*in* [COLOR="#FF0000"]8814au[/COLOR]
```

---

### Post by Yellow Pasque on 2019-12-23
As for the USB ID, if you can give me a link to the product you have, I would be glad to submit the name to the USB database so users aren't confused in the future. Is this the one?:
[https://www.netgear.com/home/products/networking/wifi-adapters/A7000.aspx](https://www.netgear.com/home/products/networking/wifi-adapters/A7000.aspx)

---

### Post by fired-spenser on 2019-12-23
> **Yellow Pasque said:**
> As for the USB ID, if you can give me a link to the product you have, I would be glad to submit the name to the USB database so users aren't confused in the future. Is this the one?:
[https://www.netgear.com/home/products/networking/wifi-adapters/A7000.aspx](https://www.netgear.com/home/products/networking/wifi-adapters/A7000.aspx)

Thanks!  That is the one!

---

### Post by fired-spenser on 2019-12-23
> **praseodym said:**
> [https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426](https://ubuntuforums.org/showthread.php?t=2391042&p=13763426#post13763426)

Seems to be this one

Edit: Yes, it is
```

modprobe -c | grep -i "0846.*9054"
alias usb:v[COLOR=#FF0000]0846[/COLOR]p[COLOR=#FF0000]9054[/COLOR]d*dc*dsc*dp*ic*isc*ip*in* [COLOR=#FF0000]8814au[/COLOR]
```

Thanks!  But, that didn't do it...  Same results from lsusb, and system still acts as though the wifi adapter isn't there - doesn't show with iwconfig.

And, more concerning... Since making the change suggested on that other thread, I'm getting hung up on booting - stuck on the pink/purple screen - if I try to boot up with the dongle plugged in.  Without it, no problem.

ETA: I removed the dkms module that the other thread had me install, and I'm back where I started.  I can boot without problem, with the adapter plugged in or not, but it still shows as a Netgear camera instead of a wifi adapter.  

Thanks again, guys!  Still happy to take whatever help you've got and will experiment until it's working.

---

### Post by jeremy31 on 2019-12-24
try ```
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
reboot
Secure Boot will need to be disabled if Ubuntu is installed using UEFI
I am not sure why the description shows Integrated camera, see if it changes after
```
sudo update-usbids
```

---

### Post by praseodym on 2019-12-24
Lets see
```

sudo modprobe -v 8814au
dmesg | grep 88
```

---

### Post by fired-spenser on 2019-12-24
> **jeremy31 said:**
> try ```
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
```
reboot
Secure Boot will need to be disabled if Ubuntu is installed using UEFI
I am not sure why the description shows Integrated camera, see if it changes after
```
sudo update-usbids
```

This got it working!  Thanks!

But, I can't update the ids...

sudo update-usbids
[sudo] password for mike: 
sudo: update-usbids: command not found

Minor nuisance, since it works.  But, just a heads up in case I'm doing something stupid. Thanks again.

---

### Post by praseodym on 2019-12-24
Weird. Please show

```
modprobe -c | grep -i "0846.*9054"
lsmod
usb-devices
```

---

### Post by Yellow Pasque on 2019-12-24
1. I haven't submitted the USB ID change yet, because as you said, it's just an aesthetic thing (and I'm very good at procrastinating).
2. I don't think you can manually update with update-usbids anymore

---

### Post by jeremy31 on 2019-12-24
Check this ```
apt policy usbutils
```
The update-usbids is normally part of that package.  I wonder if there was some error in your file as everything I see upstream for that device is blank so lsusb should show it as just Bus 003 Device 010: ID 0846:9054 NetGear, Inc

---

### Post by Yellow Pasque on 2019-12-26
> **jeremy31 said:**
> Check this ```
apt policy usbutils
```
The update-usbids is normally part of that package.

Debian moved to using a copy of the USB ID's provided by systemd/udev (same thing with PCI ID's). So updates have to come through the package manager. I don't remember exactly when that happened, but I wouldn't be surprised if Ubuntu 19.10 pulled in that change. I hope updated USB/PCI ID's will be frequent (monthly?) on future LTS releases. That is better than making the user manually do it and will make life easier for those of us trying to troubleshoot other peoples' systems.

---

