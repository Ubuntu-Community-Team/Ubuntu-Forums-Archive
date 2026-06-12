---
title: "Bluetooth is disabled, Asus X550CA"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by degomme-bruno on 2016-03-01
Hello,

I have the following problem : when I open the default Bluetooth manager on Ubuntu, it states that "Bluetooth is disabled", and clicking on the "ON/OFF" button doesn't have any effect.

I do have Bluetooth hardware on my computer, and it doesn't seem blocked as you can see in the result of "rfkill list" : 

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

I tried reinstalling the software and using Bluetooth manager without success. I formerly used Windows, and may have left Bluetooth blocked on Windows, but I am single boot on Ubuntu now.

Thank you for your time

---

### Post by jeremy31 on 2016-03-01
Post the terminal results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

Please use code tags on terminal output [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) it preserves the format and prevents smilies from showing up

---

### Post by degomme-bruno on 2016-03-04
Here they are 

```

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 13d3:5188 IMC Networks 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0461:4d7a Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.168202] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.875010] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   19.050052] Bluetooth: Core ver 2.20
[   19.050066] Bluetooth: HCI device and connection manager initialized
[   19.050070] Bluetooth: HCI socket layer initialized
[   19.050072] Bluetooth: L2CAP socket layer initialized
[   19.050077] Bluetooth: SCO socket layer initialized
[   19.053280] Bluetooth: RFCOMM TTY layer initialized
[   19.053288] Bluetooth: RFCOMM socket layer initialized
[   19.053293] Bluetooth: RFCOMM ver 1.11
[   19.068923] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.068927] Bluetooth: BNEP filters: protocol multicast
[   19.068931] Bluetooth: BNEP socket layer initialized

```

---

### Post by jeremy31 on 2016-03-04
Post ```
uname -a; hciconfig -a; lspci -nnk | grep -iA2 net; usb-devices | awk '/5188/' RS=
```

---

### Post by degomme-bruno on 2016-03-05
```

Linux brunoob-X550CA 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Kernel driver in use: ath9k
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
T:  Bus=03 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=5188 Rev=08.14
S:  Manufacturer=Azurewave
S:  Product=USB2.0 UVC HD Webcam
S:  SerialNumber=NULL
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

```

---

### Post by jeremy31 on 2016-03-05
Is there an option in BIOS to enable bluetooth?  Linux can't find any trace of it and it should have showed up in the lsusb results.  I did a search for the wifi cards subsytem ID [11ad:6627] and didn't see any of them with bluetooth working in Linux.

---

