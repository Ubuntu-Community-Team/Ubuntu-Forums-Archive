---
title: "How to install usb modem PROMATE"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Nazim Alrifai on 2008-05-21
I am new to the forum so i could not find place to share you my experience regarding installing this modem ,these are the steps :
1.log as a root to edit the wvdial.conf file to be like this :
[Dialer Defaults]

Phone = *99#
Username = pps
Password = pps
Stupid Mode = 1
Dial Command = ATDT

 

[Dialer ego]

Modem = /dev/ttyACM0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
pps is my password 
ttyACMO is the type of the port that the modem take .
then go to the terminal and write :lsusb
and the out come will be like this :
Bus 005 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05c6:3100 Qualcomm, Inc. CDMA Wireless Modem/Phone
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
the important line is :
Bus 002 Device 003: ID 05c6:3100 Qualcomm, Inc. CDMA Wireless Modem/Phone
go to terminal and write :
rmmod usbserial && modprobe usbserial vendor=0x05c6 product=0x3100
now to connect to the net write in the terminal :
wvdial ego


i hope it will wark

---

### Post by mbahrani on 2008-08-18
Thank you. i hope it will work. the only thing holding me back from installing ubuntu is the modem. so i hope it will work

thanks again

---

