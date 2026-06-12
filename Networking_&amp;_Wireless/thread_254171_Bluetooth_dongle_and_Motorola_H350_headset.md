---
title: "Bluetooth dongle and Motorola H350 headset"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by kom on 2006-09-09
Hi all,

   I am running Ubuntu 6.06 (Dapper Drake) and had a pretty good time with it with reagrds to hardware compatibility, so far. I am actaully looking to use a Bluetooth adapter with Ubuntu to get my Motorola H350 headset running.

*lsusb* output:

```

Bus 001 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 008: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 002 Device 005: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 002 Device 004: ID 045e:00b0 Microsoft Corp.
Bus 002 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 8086:1120 Intel Corp.
Bus 002 Device 001: ID 0000:0000

```

I have tried many different things including kdebluetooth, gnome-bluetooth, blues-utils etc. but nothing worked. Is my Bluetooth dongle compatible with Ubuntu?

Best.

---

### Post by wieman01 on 2006-09-09
What dongle have you got? Can you find the brand here:

[http://www.holtmann.org/linux/bluetooth/features.html]("http://www.holtmann.org/linux/bluetooth/features.html")

If the brand is listed, there is a good chance that it is recognized. But since I cannot find anything relating to a Bluetooth dongle in your output I am afraid it's not recognized.

---

### Post by kom on 2006-09-09
Hi,
    My brand is listed there (Billionton) but I am not sure if the model number is, because I don't know mine. What's bothering me is that, if I my dongle is recognized (in the *lsusb* commnand) then shouldn't it work?

-kom

---

### Post by wieman01 on 2006-09-09
I've got Billionton as well. This one should definitely work.

I've also attached a screenshot of all the bluetooth-related tool that I have installed at some point. Perhaps that helps a bit.

Then... Have you tried this guide?

[https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup")

---

