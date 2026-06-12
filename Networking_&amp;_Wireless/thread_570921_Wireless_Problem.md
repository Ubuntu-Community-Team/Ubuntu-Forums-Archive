---
title: "Wireless Problem"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by nspatel1986 on 2007-10-08
I have a Compex WLU54G USB Wireless Card based upon the Ralink 2500 chipset.

I installed ndiswrapper but it would not work

---------------------------------------------------------------------------------------------------------------------
me@my-computer:~$ ndiswrapper -l
prisma00 : driver installed
prisma02 : driver installed
rt2500usb : driver installed
        device (148F:2570) present (alternate driver: rt2570)
---------------------------------------------------------------------------------------------------------------------
me@my-computer:~$ lsusb
Bus 002 Device 003: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  
---------------------------------------------------------------------------------------------------------------------
neel@nilus-server:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

