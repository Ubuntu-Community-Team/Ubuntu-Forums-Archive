---
title: "Lubuntu 14.04 can't install Netgear WNA3100"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by daniel146 on 2014-08-01
Ok so I am currently trying to install my wireless adapter for my computer that I just bought yesterday. Lubuntu doesn't want to run the installation cd that came with it. I was able to get the cd recognized, but that's as far as it went; double clicking on "autorun.exe" in those files does not help either, when done so it reads, "Archive manager: An error occurred while loading the archive."
Also, here is what I get when I go to the terminal and type, " lsusb"
Bus 001 device 008: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 device 002: ID 413c:2107 Dell Computer Corp.
Bus 002 device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by praseodym on 2014-08-01
Hi,

Broadcom-USB sticks only work wit Ndiswrapper and the corresponding Windows drivers. Installation via cable:
```

sudo apt-get install linux-headers-generic linux-headers-$(uname -r) dkms build-essential ndisgtk ndiswrapper-dkms
```
Then use these drivers (chose 32 or 64 bit there) and install the corresponding *.INF file via
```

gksudo ndisgtk
```

Drivers:

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

You may need to change the router mode to b/g.

---

### Post by daniel146 on 2014-08-01
Thanks, but how am I supposed to get the drivers if my computer can't connect to the internet?
*EDIT* I just wanted to point out I am not using my computer to connect to the forum - this is all via my phone (typing the above was a giant pain).

---

### Post by praseodym on 2014-08-01
No internal LAN or WLAN card? Lets check:
```

lspci -nnk | grep -iA2 net
pccardctl info
```
You can upload a screenshot

---

### Post by daniel146 on 2014-08-01
Here's what it told me after following your last message: grep: pccardctl: No such file or directory
Grep: info: No such file or directory
*EDIT*
After attempting to follow the instructions for ndiswrapper - most came back with: failed to fetch
While others returned with: Could not resolve 'security.ubuntu.com'

---

### Post by praseodym on 2014-08-01
Can you add a screenshot of the above terminal outputs?

---

