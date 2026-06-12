---
title: "Lubuntu and Bluetooth"
date: 2020-10-11
forum: Networking &amp; Wireless
---

### Post by asearle on 2020-10-11
Hallo Everyone,

I have recently switched to Lubuntu 20.04 and find that nowhere near as man Bluetooth devices are detected. The ones not detected include the ones I want to connect which are placed directly next to the computer.

I have compared with an installation of 18.04 and on that a whole host of devices are detected.  But under 20.04 only a handful.  This shows that Bluetooth is working but somehow not detecting certain devices.

I compared the settings between 18.04 and 20.04 and tried to match up the software installed (for bluetooth) but this didn't help. I tried BlueMan and BlueDevil.

Any ideas as to what I could do/check?

Many thanks.

Yours,
Alan in Cologne

---

### Post by mIk3_08 on 2020-10-11
try to run this command in your terminal and paste the result here in thread wrap with code.
```
dmesg | grep -i 'bluetooth'
```

---

### Post by asearle on 2020-10-15
Hi there,

Here (below) is the output.

It would be great if we could identify the problem.

I have been comparing with another (slightly newer) laptop with, as far as I can see, identical setup and the newer laptop seems to recognise far more bluetooth devices than the older one. The new one seems to see "named" devices while the older one (output below) only sees a few devices declared with their system IDs. (none named).

My worry is that maybe this is not a sofware problem but rather that the older laptop (a Fujitsu Lifebook P701) has an older/different bluetooth adapter which is not compatible with some modern devices.

Any thoughts?

Many thanks.

Yours,
Alan in Cologne

```
$ dmesg | grep -i 'bluetooth'
[   14.286416] Bluetooth: Core ver 2.22
[   14.286439] Bluetooth: HCI device and connection manager initialized
[   14.286443] Bluetooth: HCI socket layer initialized
[   14.286445] Bluetooth: L2CAP socket layer initialized
[   14.286449] Bluetooth: SCO socket layer initialized
[   14.570834] Bluetooth: hci0: BCM: chip id 20
[   14.571829] Bluetooth: hci0: BCM: features 0x07
[   14.587817] Bluetooth: hci0: BCM20702A
[   14.588809] Bluetooth: hci0: BCM20702A0 (001.001.024) build 0000
[   14.645614] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0489-e031.hcd failed with error -2
[   14.645623] Bluetooth: hci0: BCM: Patch brcm/BCM20702A0-0489-e031.hcd not found
[   26.090625] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.090627] Bluetooth: BNEP filters: protocol multicast
[   26.090634] Bluetooth: BNEP socket layer initialized
[   28.197725] Bluetooth: RFCOMM TTY layer initialized
[   28.197738] Bluetooth: RFCOMM socket layer initialized
[   28.197753] Bluetooth: RFCOMM ver 1.11

```

---

### Post by mIk3_08 on 2020-10-15
[Click here.]("https://forums.linuxmint.com/viewtopic.php?t=240505") It might help.

---

### Post by guiverc on 2020-10-15
I'm not sure this will be of any help (*I don't use bluetooth devices sorry*), but I'll provide the Lubuntu manual page :-

[https://manual.lubuntu.me/stable/2/2.1/2.1.4/bluedevil.html](https://manual.lubuntu.me/stable/2/2.1/2.1.4/bluedevil.html)

---

### Post by mIk3_08 on 2020-10-16
I prefer to do the hcd firmware load. It is very effective. Im sure 100% if you had the right one.

---

### Post by TheFu on 2020-10-16
Hopefully everyone knows that BT security on linux has been pretty poor for years. Appears that 3 CVEs were opened this week around Bluez and other bluetooth remote access problems with proof-of-concept code.  Kernel 5.9+ (don't quote me, might be 5.10+) will be getting some fixes.  I didn't see any mention of backporting in the fixes.
From 14 Oct, 2020: [https://arstechnica.com/information-technology/2020/10/google-and-intel-warn-of-high-severity-bluetooth-security-bug-in-linux/](https://arstechnica.com/information-technology/2020/10/google-and-intel-warn-of-high-severity-bluetooth-security-bug-in-linux/)
It doesn't apply to proprietary Android BT stacks, just desktop Linux systems.
> The flaw resides in BlueZ, the software stack that by default implements all Bluetooth core protocols and layers for Linux. Besides Linux laptops, it's used in many consumer or industrial Internet-of-things devices. It works with Linux versions 2.4.6 and later.
Seems like a good time to use wired connections until whatever fix happens in the next weeks and months trickles out to our desktops.

---

### Post by mIk3_08 on 2020-10-18
Thanks a lot  for the info TheFu. It was a great news.

---

