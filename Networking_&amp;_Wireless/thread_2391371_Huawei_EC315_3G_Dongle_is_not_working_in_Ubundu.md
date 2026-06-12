---
title: "Huawei EC315 3G Dongle is not working in Ubundu"
date: 2018-05-09
forum: Networking &amp; Wireless
---

### Post by bala1405 on 2018-05-09
Hi,

I'm a newbie to Ubuntu. I have an Ubuntu running board for Embedded development. I'm trying to configure Huawei EC315 modem for network connectivity. 

The output of **lsusb **is the below:
root@texe_hub:~# lsusb
lsusb: cannot open "/usr/share/usb.ids", No such file or directoryBus 002 Device 001: ID 1d6b:0002
Bus 001 Device 002: ID 12d1:14db
Bus 001 Device 001: ID 1d6b:0002

I'm successfully able to switch the device from Mass storage to Modem using the below command:
root@texe_hub:/etc/udev/rules.d# **usb_modeswitch -v 12d1 -p 1f01 -J**
Look for default devices ...
product ID matched
Found devices in default mode (1)
Access device 003 on bus 001
Current configuration number is 1
Use interface number 0
Use endpoints 0x01 (out) and 0x81 (in)


USB description data (for identification)
-------------------------
Manufacturer: Huawei Technologies
Product: HUAWEI Mobile
Serial No.: not provided
-------------------------
Using standard Huawei switching message
Looking for active driver ...
OK, driver detached
Set up interface 0
Use endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
OK, message successfully sent
Reset response endpoint 0x81
Reset message endpoint 0x01
-> Run lsusb to note any changes. Bye!


After that when I try to load the driver using modprobe, I'm getting the below error. 
root@texe_hub:~# **modprobe****usbserial**** vendor=0x12d1 product=0x14db**
[ 312.839711] usbcore: registered new interface driver usbserial
[ 312.857796] usbcore: registered new interface driver usbserial_generic
[ 312.877136] usbserial: USB Serial support registered for generic
[ 312.883334] usbserial_generic 1-1:1.0: Generic device with no bulk out, not allowed.
[ 312.904695] usbserial_generic: **probe of 1-1:1.0 failed with error -5**
[ 312.911203] usbserial_generic 1-1:1.1: The "generic" usb-serial driver is only for testing and one-off prototypes.
[ 312.934684] usbserial_generic 1-1:1.1: Tell [EMAIL="linux-usb@vger.kernel.org"]linux-usb@vger.kernel.org[/EMAIL] to add your device to a proper driver.
[ 312.954987] usbserial_generic 1-1:1.1: generic converter detected
[ 312.979489] usb 1-1: generic converter now attached to ttyUSB0

How to fix this issue? Please guide on what I can do to get it working.

Thanks in advance,
Bala

---

