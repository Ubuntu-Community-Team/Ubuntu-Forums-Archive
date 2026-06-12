---
title: "Belkin F8T001 Bluetooth Dongle"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by kjsteuer on 2007-06-13
I am using the current version of Ubuntu and I have a Belkin F8T001 bluetooth adapter. I do not think it is version 2. Wouldn’t it say v2 on it? 

I have read that version 2 of the dongle should work when you plug it in. However when I run hciconfig, I get no output which I think means no detected devices. I have been messing with this the last few days and have had no luck. 

Does anyone have any suggestions? Should I go out and buy a more compatible dongle? If so what are some good ones that work on both Windows and Linux?

---

### Post by kjsteuer on 2007-06-13
I have some success...Ubuntu does recognize the device but there is an error. 

When running the dmesg command I get the following output:

dmesg
...
[   35.133846] Bluetooth: HCI device and connection manager initialized

[   35.133851] Bluetooth: HCI socket layer initialized

[   35.167375] Bluetooth: L2CAP ver 2.8

[   35.167383] Bluetooth: L2CAP socket layer initialized

[   35.274844] Bluetooth: RFCOMM socket layer initialized

[   35.274862] Bluetooth: RFCOMM TTY layer initialized

[   35.274867] Bluetooth: RFCOMM ver 1.8

[   47.740411] eth0: no IPv6 routers present

[  445.410620] usb 4-1: new full speed USB device using uhci_hcd and address 2

[  445.561687] usb 4-1: configuration #1 chosen from 1 choice

[  445.779612] Bluetooth: Broadcom Blutonium firmware driver ver 1.1

[  445.806461] bcm203x_probe: Mini driver request failed

[  445.807002] bcm203x: probe of 4-1:1.0 failed with error -5

[  445.807715] usbcore: registered new interface driver bcm203x

[  445.836079] Bluetooth: HCI USB driver ver 2.9

[  445.837058] usbcore: registered new interface driver hci_usb


My device uses Broadcom drivers. 
There is a solution to this at: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85247](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85247)

I need to backport a driver. From the link above “I backported drivers/bluetooth/bcm203x.c from 2.6.20 to 2.6.18 and recompiled the module within the 2.6.20 source” 

Does anyone know how to do this?

---

### Post by CityofAsh on 2007-06-15
Im having similar problems. I can discover the device from other bluetooth devices but unable to pair them.  

```
root@CityofAsh-Linux:~# hcitool dev
Devices:
        hci0    00:0A:3A:55:92:FA
```

```
root@CityofAsh-Linux:~# sudo hidd --search
Searching ...
root@CityofAsh-Linux:~# 
```
 i get nothing here. 
```
root@CityofAsh-Linux:~# hciconfig hci0 inqmode 0
Can't set inquiry mode on hci0: Input/output error (5)
root@CityofAsh-Linux:~# 

```
not sure why.
```

root@CityofAsh-Linux:~# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 050d:0081 Belkin Components 

```

If you figure anything out please post it.

Thanks

~City

---

