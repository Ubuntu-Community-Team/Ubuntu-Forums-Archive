---
title: "USB Devices are Not Being Detected"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by insub2 on 2009-05-01
My laptop stopped detecting USB devices.  Looked around the forums a little and couldn't find anything.  One of the threads I found asked for the following output.  I've included it in case it's helpful.

```
insub2@Warpath:~$ sleep 10 && dmesg | tail
[  201.271052] hub 2-0:1.0: over-current change on port 2
[  201.557739] hub 2-0:1.0: over-current change on port 2
[  201.575265] hub 2-0:1.0: over-current change on port 2
[  201.590172] hub 2-0:1.0: over-current change on port 2
[  201.684815] hub 2-0:1.0: over-current change on port 2
[  201.788731] hub 2-0:1.0: over-current change on port 2
[  277.532190] usb 2-1: new high speed USB device using ehci_hcd and address 8
[  291.915268] uhci_hcd 0000:00:1d.3: FGR not stopped yet!
[  291.978954] uhci_hcd 0000:00:1d.1: FGR not stopped yet!
[  292.098804] usb 2-1: new high speed USB device using ehci_hcd and address 10
insub2@Warpath:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

---

### Post by lavinog on 2009-05-01
It looks like one of your usb devices is drawing too much current and overloading your usb headers.

What are you plugging in?
If you are using a usb hub, make sure it has its own power supply.
USB headers can only support 0.5 W and actually won't allow devices to draw more than 0.4 W

If the device is not a large load, look for damage to your ports.
Also post your whole dmesg to see any other information that may be relevant.
```
dmesg
```

---

