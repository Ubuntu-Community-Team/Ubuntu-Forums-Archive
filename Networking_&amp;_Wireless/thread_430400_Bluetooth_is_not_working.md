---
title: "Bluetooth is not working"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by xav42 on 2007-05-02
Hi !

I can't get bluetooth to work on my HP nx9420 laptop...

```
xav@xav-laptop:/$ hcitool dev
Devices:
xav@xav-laptop:/$ ls /dev/hci*
ls: /dev/hci*: No such file or directory
xav@xav-laptop:/$ dmesg | grep Bluetooth
[   47.344000] Bluetooth: Core ver 2.11
[   47.344000] Bluetooth: HCI device and connection manager initialized
[   47.344000] Bluetooth: HCI socket layer initialized
[   47.480000] Bluetooth: L2CAP ver 2.8
[   47.480000] Bluetooth: L2CAP socket layer initialized
[   47.556000] Bluetooth: RFCOMM socket layer initialized
[   47.556000] Bluetooth: RFCOMM TTY layer initialized
[   47.556000] Bluetooth: RFCOMM ver 1.8

```

Any idea someone ?

Regards.

---

### Post by xav42 on 2007-05-02
I forget to mention I'm using Kubuntu Feisty.

Does anyone have a clue ?

---

### Post by cjsteele on 2007-09-29
I can see my bluetooth adapter from my Blackberry, but can't pair to it without researching.  That leads me to believe that the stack is there and the device is working, but... 

I'm using Fiesty on an nx9420.

---

### Post by qwerion on 2008-01-31
lspci | grep blue
lsusb | grep blue

like theres no blutooth hardware in my computer...but there is...

I would like to know, if it is posible to compile kernel module for this bluetooth device...

---

