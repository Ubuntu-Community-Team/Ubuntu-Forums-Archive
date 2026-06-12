---
title: "Driver not  with Asus USB ac51 Wifi adapter (mt7610u/rt2870)"
date: 2015-12-26
forum: Networking &amp; Wireless
---

### Post by frank9184 on 2015-12-26
Hello ,

I bought Asus USB ac51 Wifi adapter last week ,and i dont know how to set up

I used the driver which is in the cd (3.001),and i got ERROR 2 in make program


After that i try MTK driver (3.002) and still the same with driver in cd

Here is lsusb list

```
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 003: ID 046d:c31d Logitech, Inc. Media Keyboard K200
Bus 001 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 001 Device 008: ID 0b05:17d1 ASUSTek Computer, Inc. AC51 802.11a/b/g/n/ac Wireless Adapter [Mediatek MT7610/Ralink RT2870]
Bus 001 Device 006: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

Any one can tell me how to solve the problem??:D

---

### Post by praseodym on 2015-12-26
Try to add the device ID to the native rt2800usb:
```

echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "0b05 17d1" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf 
```
This is one line, you better c/p it. Reboot and check:
```

dmesg | grep rt2
iwconfig
lsmod
```

---

