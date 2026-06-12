---
title: "[SOLVED] Feisty and Sagem F@st 800 drivers compile"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by zeusalmighty on 2007-05-06
I'm using the ADSL Sagem F@ST 800 usb modem, but I can't get to connect to my provider. I've used some guides to install the driver, mainly "ueagle-data-1.1.tar.gz", by extracting it to where the guide states and configuring the "secrets" file and all, even "modprobe" works fine. The problem starts when I try to use "pon ueagle-atm".

When I issue that command, the terminal starts outputting jibberish "{#@}^$@{}", stuff like that. It outputs for about 4-5 lines, then it stops. I then check my network connection status with "ifconfig" and I get a "Local Loopback".

Everything seems to work fine, but I can't connect, and I suspect that I need to install extra firmware "ueagle-atm-1.3.tar.gz". The problem is this driver needs compiling, and apparently Feisty can't compile it, because I keep getting errors when I try the "make" command. So, does anyone know which packages I need to install in Feisty to make this compilable? If I can compile this and use the drivers, I'll know if that was the problem or not.

Thanks in advance!

EDIT: SOLVED, use this link:  [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm]("https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm")
It works perfectly in Gutsy Gibbon (7.10)

---

