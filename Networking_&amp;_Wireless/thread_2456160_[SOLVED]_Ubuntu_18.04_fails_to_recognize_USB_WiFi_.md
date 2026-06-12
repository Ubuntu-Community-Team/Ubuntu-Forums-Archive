---
title: "[SOLVED] Ubuntu 18.04 fails to recognize USB WiFi dongle"
date: 2021-01-05
forum: Networking &amp; Wireless
---

### Post by extraspecialbitter2 on 2021-01-05
I've just received a Dell Optiplex 7080 running Ubuntu 18.04. I don't have a Wired connection available, so I bought a [SIZE=2][FONT=arial]BrosTrend 1200Mbps Linux USB WiFi Adapter that boasted out-of-the-box connectivity. Naturally that wasn't the case. Here's what happens when I plug it in:

```
[FONT=courier new]kernel: [ 1757.081514] usb 1-13: new high-speed USB device number 9 using xhci_hcd
[SIZE=2]kernel: [ [SIZE=2][SIZE=2]1757[/SIZE][/SIZE].230242] [SIZE=2]usb 1-13: New[/SIZE][/SIZE] USB device found, idVendor=0bda, idProduct=b812, bcdDevice= 2.10
.
.
.
mtp-probe: checking bus 1, device 9: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-13"
mtp-probe: bus 1, device: 9 was not an MTP device
upowerd[1573]: unhandled action 'bind' on [SIZE=2]/sys/devices/pci0000:00/0000:00:14.0/usb1/1-13"[/SIZE][/FONT]
```
[/FONT][/SIZE]
I don't have a Wired network connection and am hoping it's just a matter of a tweak under /etc/udev/rules.d

---

### Post by CelticWarrior on 2021-01-05
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

or at least post the results from 'lsusb' so the chipset can be identified.

---

### Post by morrownr on 2021-01-05
"idVendor=0bda, idProduct=b812" tells me this is a Realtek 8812bu chipset. Try the 88x2bu driver here:

[https://github.com/morrownr](https://github.com/morrownr)

FYI: The only dual band AC1200 USB WiFi adapters that are supported in kernel that I am aware of are based on the MT7612u chipset. An example:

[https://www.amazon.com/dp/B08BJS8FXD/?coliid=I2505JQB0PSJZZ]("https://www.amazon.com/dp/B00MX57AO4/?coliid=I2WSXNOY3WKYSC")

---

### Post by extraspecialbitter2 on 2021-01-05
Thanks for the reply. At the moment the Dell OptiPlex 7080 is not connected to the network, and evidently whoever installed Ubuntu on the computer didn't do much in the way of updating it beyond the base install. I'll need to move it to where I can connect to the wired internet and take it from there. Stay tuned.

---

### Post by extraspecialbitter2 on 2021-01-06
> **morrownr said:**
> "idVendor=0bda, idProduct=b812" tells me this is a Realtek 8812bu chipset. Try the 88x2bu driver here:

[https://github.com/morrownr](https://github.com/morrownr)

FYI: The only dual band AC1200 USB WiFi adapters that are supported in kernel that I am aware of are based on the MT7612u chipset. An example:

[https://www.amazon.com/dp/B08BJS8FXD/?coliid=I2505JQB0PSJZZ]("https://www.amazon.com/dp/B00MX57AO4/?coliid=I2WSXNOY3WKYSC")

Thanks for the informative reply. I thought the Amazon ad claiming out-of-the-box support for the dongle was too good to be true. I appreciate the link to the driver - as well as the detailed instructions - and will install it as soon as I can connect to the wired internet this weekend.

Thanks again!

Paul

---

### Post by CelticWarrior on 2021-01-06
I haven't seen any ad for that dongle claiming out-of-box-support. That was your assumption.
Any hardware is supported in a given OS provided drivers exist for said hardware. When they do then it's supported. Supported more often than not doesn't mean out-of-the-box support. If that was the case the vast majority of hardware out there wouldn't be supported in Windows either.

---

### Post by extraspecialbitter2 on 2021-01-06
> **CelticWarrior said:**
> I haven't seen any ad for that dongle claiming out-of-box-support. That was your assumption.
Any hardware is supported in a given OS provided drivers exist for said hardware. When they do then it's supported. Supported more often than not doesn't mean out-of-the-box support. If that was the case the vast majority of hardware out there wouldn't be supported in Windows either.

Yup, I'm guilty of wishfully thinking "support" meant "out-of-the-box support". I'm hoping to remedy the issue when I can move the computer to a wired internet connection - most likely this weekend. I might have similar issues with a Bluetooth Dongle, but at least I have a USB mouse and keyboard as a workaround.

---

### Post by morrownr on 2021-01-08
While Linux has good hardware support in many areas, USB WiFi is not one of those areas so it pays to research and ask before buying. I've been adding some USB WiFi information to this site:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

The information is pretty good but incomplete so if there is anyone who has information to add to this site, please post it in "Issues" on the site. Maybe we can make this a good resource for the community.

---

### Post by extraspecialbitter2 on 2021-01-08
> **morrownr said:**
> While Linux has good hardware support in many areas, USB WiFi is not one of those areas so it pays to research and ask before buying. I've been adding some USB WiFi information to this site:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

The information is pretty good but incomplete so if there is anyone who has information to add to this site, please post it in "Issues" on the site. Maybe we can make this a good resource for the community.

Thanks for compiling this guide. A few years back I went through some similar heartburn trying to implement Bluetooth via USB dongle on Linux. At the time, Debian had decent driver support, but finding the correct driver required a lot of trial and error. Now the necessary drivers are built into more recent kernels.

---

### Post by extraspecialbitter2 on 2021-01-09
> **extraspecialbitter2 said:**
> Thanks for the informative reply. I thought the Amazon ad claiming out-of-the-box support for the dongle was too good to be true. I appreciate the link to the driver - as well as the detailed instructions - and will install it as soon as I can connect to the wired internet this weekend.

Thanks again!

Paul

I followed the instructions to install the driver for the [COLOR=#000000][I]Realtek 8812bu chipset and upon reboot was able to connect to the network via wireless. Thank you so much for the help!

[/I][/COLOR]Paul

---

