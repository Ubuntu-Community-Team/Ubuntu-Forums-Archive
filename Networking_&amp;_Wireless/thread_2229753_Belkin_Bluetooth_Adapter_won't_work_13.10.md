---
title: "Belkin Bluetooth Adapter won't work 13.10"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by Josephkzez on 2014-06-15
Hi all,
I'm new to the forum

I have a ASUS K45VM with Ubuntu 13.10 on it, and a Windows 8
I have a belkin mini bluetooth adapter v 4.0 that I want to use to connect with a Logictech UE Boombox
It works fine on Windows 8.

First I I opened Synaptics and installed many things related to Bluetooth

Then

I tried lsusb command and this is what I get
```
[COLOR=#000000]josephkzez@josephkzez-K45VM:~$ lsusb[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 003: ID 1bcf:2883 Sunplus Innovation Technology Inc. [/COLOR]
[COLOR=#000000]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/COLOR]
[COLOR=#000000]Bus 003 Device 006: ID 050d:065a Belkin Components [/COLOR]
[COLOR=#000000]Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth[/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
```

I tried to check Blueman it is grayed out

I tried hciconfig command and nothing happened

I also tried sudo /etc/init.d/bluez-utils restart
```
[COLOR=#000000]josephkzez@josephkzez-K45VM:~$ sudo /etc/init.d/bluez-utils restart[/COLOR]
[COLOR=#000000]sudo: /etc/init.d/bluez-utils: command not found[/COLOR]
```

I tried what it says here [https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters](https://wiki.ubuntu.com/HardwareSupportComponentsBluetoothUsbAdapters) but no success

I don't know what to do. I searched the forum for couple of hours for solutions, the closes one's I got was
[http://ubuntuforums.org/showthread.php?t=2171214](http://ubuntuforums.org/showthread.php?t=2171214)
and [http://ubuntuforums.org/showthread.php?t=2200627&highlight=belkin+bluetooth+13.10](http://ubuntuforums.org/showthread.php?t=2200627&highlight=belkin+bluetooth+13.10)

I don't know if I have to provide more information, if so, I'd be glad to provide them

Thanks in advance

---

