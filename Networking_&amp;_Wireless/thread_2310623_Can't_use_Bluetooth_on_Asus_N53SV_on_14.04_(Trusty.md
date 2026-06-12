---
title: "Can't use Bluetooth on Asus N53SV on 14.04 (Trusty)"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by pluc16 on 2016-01-20
Hi all,
I am relatively new to Ubuntu so forgive me if I'm missing something really basic, but I can't get my laptop bluetooth to work at all.

Some info:
Vendor Specifications: [https://www.asus.com/Notebooks/N53SV/specifications/](https://www.asus.com/Notebooks/N53SV/specifications/)
Ubuntu Help: [https://help.ubuntu.com/community/Asus_N53#Bluetooth](https://help.ubuntu.com/community/Asus_N53#Bluetooth)

According to this last page, the is "Fixed in Ubuntu 11.10" however here I am and I cant apply the proposed fix as I can't find those compat drivers at all.

Someone could give me a hand?

Thanks for your time!

---

### Post by jeremy31 on 2016-01-20
Things change a lot in linux, please post the result of ```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
```

It doesn't help that one model can have up to four or five different wifi cards that may or may not have a bluetooth chip, even the Asus spec says bluetooth(optional)

---

### Post by pluc16 on 2016-01-20
This is the output:
```
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
    Kernel driver in use: r8169
Bus 004 Device 003: ID 046d:c246 Logitech, Inc. Gaming Mouse G300
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 174f:1718 Syntek 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[    0.372910] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.594621] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040201)
[   20.571317] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   26.052565] Bluetooth: Core ver 2.20
[   26.052578] Bluetooth: HCI device and connection manager initialized
[   26.052581] Bluetooth: HCI socket layer initialized
[   26.052583] Bluetooth: L2CAP socket layer initialized
[   26.052592] Bluetooth: SCO socket layer initialized
[   26.055270] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.055273] Bluetooth: BNEP filters: protocol multicast
[   26.055276] Bluetooth: BNEP socket layer initialized
[   26.055860] Bluetooth: RFCOMM TTY layer initialized
[   26.055866] Bluetooth: RFCOMM socket layer initialized
[   26.055870] Bluetooth: RFCOMM ver 1.11

```

---

### Post by pluc16 on 2016-01-21
bump!

---

### Post by jeremy31 on 2016-01-21
No sign of your computer having a bluetooth chip in it

---

### Post by pluc16 on 2016-01-21
What is then all the Bluetooth stuff I am seeing?

On Windows I could use Bluetooth with no problems, I think is within WiFi chip (Intel).

---

### Post by jeremy31 on 2016-01-21
Not sure why it isn't detected in Ubuntu but it would show up in the lsusb results even when it is on the wifi card and the only Intel devices in lsusb are USB hubs.

The bluetooth info in the results I asked for shows up in computers without bluetooth but when a bluetooth device is detected in Linux there would be a bluetooth device in rfkill results

---

### Post by pluc16 on 2016-01-21
Mmm got it. Couldnt I even try those 'backports' drivers?

---

### Post by jeremy31 on 2016-01-21
Backports is mainly for wifi, about all you could do is try some of the other supported Ubuntu versions, 12.04, 15.10, and possibly the beta of 16.04 and see if the kernel will detect another device in lsusb

I haven't had any luck with changing the BIOS option for OS but you could see if it helps, usually the only option is Windows or other

---

