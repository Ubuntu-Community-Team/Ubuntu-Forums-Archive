---
title: "Help! E220 modem connected but cant browse web!?"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by gruffbaby on 2007-12-03
Hi,

I've just done a fresh install of Kubuntu 7.10 from cd, and I have configured wvdial.conf to allow me to "connect" to Vodafone network.

The problem is that whilst it connects ok (i.e it gets an IP address and the led stays on constantly), when I open Konqueror it will not connect to web? I have plugged in an Ethernet wireless router that allows me to connect, but it is much slower than the E220.

I had it working previously under the old install, but I configured it months ago and have forgotten how to re-enable it (i thought I only needed to config wvdial.conf).As it is a new install, am I missing something? Kubuntu doesnt really seem to recognise the modem under network tools.

Thanks,
Gruffbaby

---

### Post by gruffbaby on 2007-12-03
Here is my wvdial.conf:

[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = USB Modem
Init5 =AT+CGDCONT=1,"IP","hs.vodafone.ie";

I've changed modem type from Analog to USB, same problem. The device is not listed in Knetwork manager.

Please help.

---

