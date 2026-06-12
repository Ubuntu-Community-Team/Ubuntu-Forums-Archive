---
title: "HP printer not detected"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by al.adab on 2010-05-15
hello,

this HP C4485 was previously detected on my Dell Vostro 1310 via USB port. Nothing has changed in terms of settings, etc. The same HP printer is no longer detected. 

If I run *sudo hp-setup*, I get the following error message: 

[I]:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Error: "/var/tmp/kdecache-daniele" is owned by uid 1000 instead of uid 0.
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb[/I]

Can you please help? Thanks.

---

### Post by halitech on 2010-05-15
does it show up if you open a terminal and run
```
lsusb
```

---

### Post by al.adab on 2010-05-15
with or without connecting the printer via USB, this is what I get: 

[I]~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

---

### Post by halitech on 2010-05-15
looks like there is an issue with it being detected. Is it plugged into a hub or direct to the computer? try disconnecting it and reconnecting it. Wait about 20 seconds and then run
```
dmesg | tail
```
and see what it says.

---

### Post by al.adab on 2010-05-15
it's plugged into the laptop. 

I tested the laptop's three USB ports (each time disconnecting and reconnecting as you suggested): 

[I]~$ dmesg | tail
[  800.772033] hub 6-0:1.0: over-current change on port 1
[  800.876057] hub 6-0:1.0: over-current change on port 2
[  857.488341] Registered led device: iwl-phy0::radio
[  857.489124] Registered led device: iwl-phy0::assoc
[  857.489845] Registered led device: iwl-phy0::RX
[  857.490566] Registered led device: iwl-phy0::TX
[  857.492157] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  859.284032] hub 5-0:1.0: over-current change on port 1
[ 1125.388038] hub 5-0:1.0: over-current change on port 1
[ 1143.988031] hub 5-0:1.0: over-current change on port 1

~$ dmesg | tail
[ 1370.508056] hub 6-0:1.0: over-current change on port 2
[ 1393.141038] Registered led device: iwl-phy0::radio
[ 1393.141808] Registered led device: iwl-phy0::assoc
[ 1393.142528] Registered led device: iwl-phy0::RX
[ 1393.143245] Registered led device: iwl-phy0::TX
[ 1393.145828] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1395.134944] iwl3945 0000:06:00.0: Card state received: HW:Kill SW:On
[ 1395.135002] iwl3945 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[ 1395.212031] hub 6-0:1.0: over-current change on port 1
[ 1395.316048] hub 6-0:1.0: over-current change on port 2

~$ dmesg | tail
[ 1435.740033] hub 6-0:1.0: over-current change on port 2
[ 1442.160466] Registered led device: iwl-phy0::radio
[ 1442.161548] Registered led device: iwl-phy0::assoc
[ 1442.162306] Registered led device: iwl-phy0::RX
[ 1442.163029] Registered led device: iwl-phy0::TX
[ 1442.164540] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1443.995153] iwl3945 0000:06:00.0: Card state received: HW:Kill SW:On
[ 1443.995215] iwl3945 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[ 1444.068032] hub 6-0:1.0: over-current change on port 1
[ 1444.172054] hub 6-0:1.0: over-current change on port 2[/I]

---

### Post by halitech on 2010-05-15
no mention of the printer on any of the ports. I know this may sound like a dumb question but is the cable plugged into the printer and is the printer turned on? maybe try another cable.

---

### Post by al.adab on 2010-05-16
I checked and the cable is connected to the printer all right. I'll buy another cable and try + get back on this in a couple of days. Thanks for your help in the meantime.

---

### Post by al.adab on 2010-05-22
Got a new cable and it seems to work now - will mark this as solved and open a new thread should it act up again. thanks for your help!

---

