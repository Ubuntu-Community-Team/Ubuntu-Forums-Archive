---
title: "How to know where is my gamepad ?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-17
Hell:popcorn:o,

/dev/input/js0 is not working
but 
 /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input19

I am sure that there is nothing to /dev/input/js0 

how to know where is the input of my joystick please?


 ```

[23445.592181] usb 2-1: USB disconnect, address 5
[23453.024115] usb 2-1: new low speed USB device using uhci_hcd and address 6
[23453.202654] usb 2-1: New USB device found, idVendor=044f, idProduct=b315
[23453.202670] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[23453.202683] usb 2-1: Product: Thrustmaster dual analog 3.2
[23453.202693] usb 2-1: Manufacturer: Mega World
[23453.202999] usb 2-1: configuration #1 chosen from 1 choice
[23453.230710] input: Mega World Thrustmaster dual analog 3.2 as** /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input19**
[23453.231006] generic-usb 0003:044F:B315.0006: input,hidraw0: USB HID v1.10 Gamepad [Mega World Thrustmaster dual analog 3.2] on usb-0000:00:1d.0-1/input0



```

```
# lsusb 
Bus 001 Device 005: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3249 IMC Networks 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 044f:b315 ThrustMaster, Inc. 
Bus 002 Device 003: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by frenchn00b on 2010-01-20
here it is : ```
 cat /proc/bus/input/devices

```

---

