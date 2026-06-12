---
title: "Netgear WNDA3100"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by mailfordannym on 2014-05-11
I have a Netgear WNDA3100, and I need it to work with Ubuntu. I saw Chili555's post but sadly it didnt't work. I tried installing ndiswrapper in Synaptic. The strange thing is, I go to the Ubuntu Software Center to get the "Windows Wireless Driver" program and I check my applications and the app is not there. When I install ndiswrapper I also got ndisgtk, so it should've been there.

This is some information that I got from the terminal:

```
arch
```

I got

```
x86_64
```

Then I tried

```
lsusb
```

I got

```
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The first one on the list is the WI-FI adapter. The ID is 0846:9011 and it is a Broadcom BCM4323. 

Is there any other way I can get this to work?

When I was at the store I also saw a few linksys ones, I believe the N300 and N600 and another Netgear one that was N300 and a D-Link Xtreme. I am not sure what specfic model number they are.

Would any of those work better with Ubuntu?

---

### Post by praseodym on 2014-05-11
Hi,

Broadcom-USB devices only work with ndiswrapper and the windows driver:
```

sudo apt-get install ndisgtk ndiswrapper-dkms dkms build-essential linux-headers-generic
```
Windows driver here:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

---

### Post by mailfordannym on 2014-05-11
After whast to i do

---

### Post by mailfordannym on 2014-05-11
*what

---

### Post by praseodym on 2014-05-11
Unpack the driver and install the 64bit INF file via
```

gksudo ndisgtk
```

---

### Post by mailfordannym on 2014-05-11
Thanks, It works!

---

