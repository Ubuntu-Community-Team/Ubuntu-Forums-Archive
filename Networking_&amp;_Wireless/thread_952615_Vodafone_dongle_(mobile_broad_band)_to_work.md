---
title: "Vodafone dongle (mobile broad band) to work"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by rob2nd9th on 2008-10-19
Got my Vodafone dongle (mobile broad band) to work.

After lots of searching installing - uninstalling stuff this it the end result.

installed
wvdial
and
sl-modem-daemon

edited my  wvdial.conf

Vodafone told me the number....was *99*# it was actually *99***16#

so my wvdial.conf looks like this..

[Dialer Internet]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = on
Modem Type = USB Modem
ISDN = 0
Phone = *99***16#
New PPPD = no
Modem = /dev/ttyUSB0
Username = web
Carrier Check = no
Password = web
Baud = 460800

then I could not connect so changed my resolv.conf to look like

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4923
#
### END INFO

nameserver 208.67.222.222
nameserver 208.67.220.220 

reboot and ran wvdial and the green light came on and I had internet.

I hope this helps someone as I was heading to windows - but worked it out.

---

