---
title: "ndiswrapper won't install wireless drivers on 10.10"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by thewasteland on 2011-01-11
I've arrived here through a series of threads; I'm running Ubuntu for the first time starting on Sunday, running Maverick Meerkat (10.10)

However, due to me getting this laptop from a terrible laptop company (Sahara), it arrived with absolutely no drivers for the wifi card, so I can't use wireless. Their site had no link to downloading Ubuntu drivers, so I downloaded the Windows drivers and attempted to run them using ndiswrapper by going to Administration > Windows Wireless Drivers and adding every one in the package I downloaded, as I wasn't sure which ones to use. Every one said "Hardware present: No" or "Invalid driver!". However, I know they're the right drivers for this wireless card as I downloaded them from the site of the company which made the thing. Can anyone help please?

P.S. Various people in other threads have asked me what my wireless card is and I have no idea. The complete lack of drivers has made it invisible to basically every Terminal command they've suggested. The Windows drivers which I downloaded divide into 3 subfolders: "Intel", "QMI-EM106" and "QMI-EM203", if that helps.

---

### Post by 3rdalbum on 2011-01-11
Did you try:

```
lsusb
```

Looking on the bottom of the machine for an FCC approval sticker that states the name of the wireless card?

Checking to see if the wireless switch is turned on? (most laptops have a physical switch for the wireless - if it's turned off, then the machine can't recognise the wireless).

You're more likely to get the device working correctly with native Linux drivers (which are probably built-into the kernel already) than with emulated Windows ones.

If you can find the model number of the wifi chipset, then google it with the words "Ubuntu 10.10" - for instance, "rtl8187 ubuntu 10.10".

EDIT: Note for subsequent posters: This is the previous thread by the OP: [http://ubuntuforums.org/showthread.php?t=1664054](http://ubuntuforums.org/showthread.php?t=1664054)

---

### Post by thewasteland on 2011-01-11
> **3rdalbum said:**
> Did you try:

```
lsusb
```Looking on the bottom of the machine for an FCC approval sticker that states the name of the wireless card?

Checking to see if the wireless switch is turned on? (most laptops have a physical switch for the wireless - if it's turned off, then the machine can't recognise the wireless).

You're more likely to get the device working correctly with native Linux drivers (which are probably built-into the kernel already) than with emulated Windows ones.

If you can find the model number of the wifi chipset, then google it with the words "Ubuntu 10.10" - for instance, "rtl8187 ubuntu 10.10".

EDIT: Note for subsequent posters: This is the previous thread by the OP: [http://ubuntuforums.org/showthread.php?t=1664054](http://ubuntuforums.org/showthread.php?t=1664054)

The wireless switch is most definitely switched on. The only sticker on the bottom is the "Agere Delphi D40" one. I even phoned the manufacturer, but the helpline was extremely incompetent and although they insisted there was a wireless card and offered various Windows drivers, they couldn't tell me what it was.

lsusb returns:
"Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:070a Western Digital Technologies, Inc. My Passport Essential SE
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0408:20ba Quanta Computer, Inc. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub"

lspci returns:
"00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)"

It's almost definitely their incompetence, but I could swear the guy said that there weren't any Ubuntu drivers or something. He was basically a receptionist though, clearly knew nothing about computers.

---

