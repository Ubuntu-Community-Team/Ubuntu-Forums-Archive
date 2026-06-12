---
title: "USB-Tethereing Galaxy S4 - AT commands"
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by tmt4 on 2015-10-05
Hello,

i try to communicate with my Samsung Galaxy S4 via serial port (USB) to test some AT-commands. I connected the S4 and set it to usb-tethering. 
I'm using kubuntu 14.04.

While the phone is listed in the Network Interfaces with USB0, the cu command doesn't work. 

> 
$ lsusb

Bus 002 Device 006: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0566:3107 Monterey International Corp. Keyboard
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



> 
# usb-devices

...
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04e8 ProdID=6863 Rev=02.28
S:  Manufacturer=SAMSUNG
S:  Product=SAMSUNG_Android
S:  SerialNumber=5b120c2d
C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=96mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=e0(wlcon) Sub=01 Prot=03 Driver=rndis_host
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=rndis_host
...




> 
$ cu -l ttyUSB0
cu: open (/dev/ttyUSB0): No such file or directory
cu: ttyUSB0: Line in use


$ cu -l /dev/ttyUSB0
cu: open (/dev/ttyUSB0): No such file or directory
cu: /dev/ttyUSB0: Line in use




**EDIT!**

I managed to connect to the smartphone by searching for the correct path:

> $ sudo cu -l /dev/bus/usb/002/008
Connected.
@&#65533;ch(   K&#65533;0
          &#65533;     &#65533;$$$$&#65533;
                                &#65533;cu: Got hangup signal



But when I want to test some AT commands the permission is denied.

> $ sudo echo "ATi^M">/dev/bus/usb/002/008
bash: /dev/bus/usb/002/008: Permission denied





I'm new to linux and I need some clues. I hope you can help me!

---

