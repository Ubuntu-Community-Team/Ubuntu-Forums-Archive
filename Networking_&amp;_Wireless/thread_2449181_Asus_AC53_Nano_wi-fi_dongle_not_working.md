---
title: "Asus AC53 Nano wi-fi dongle not working"
date: 2020-08-21
forum: Networking &amp; Wireless
---

### Post by forest-gump on 2020-08-21
I found this thread [https://ubuntuforums.org/showthread.php?t=2395729](https://ubuntuforums.org/showthread.php?t=2395729) and attempted to get the suggested fix working from this comment: [https://ubuntuforums.org/showthread.php?t=2395729&p=13782927#post13782927](https://ubuntuforums.org/showthread.php?t=2395729&p=13782927#post13782927)

There were a number of build errors that I slowly took care of 1 by 1 until finally the code was able to build. Then I ran
```

$ make
$ sudo make install
$ sudo modprobe 8822bu

```


Then I turned off the computer, plugged in the USB dongle and proceeded to reboot. Unfortunately that did not work.

Here is the output of **uname -r**
```
5.4.0-7642-generic
```

Here is the output of lsusb. Note: It now freezes when I run lsusb. The command does not finish..
```
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 002: ID 04d9:0269 Holtek Semiconductor, Inc. USB Keyboard
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

Before I did this process and ran lsusb I would see the Asus usb device, but now I dont see it. Also wifi does not work.


.
.
.
.
.
.
.
.

If it helps, I unloaded everything and then restarted the computer (with the dongle unplugged) and here is my lsusb output
```

Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 002: ID 04d9:0269 Holtek Semiconductor, Inc. USB Keyboard
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1e71:2006 NZXT NZXT USB Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

