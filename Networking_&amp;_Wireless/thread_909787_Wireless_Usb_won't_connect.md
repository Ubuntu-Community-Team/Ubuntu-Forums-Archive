---
title: "Wireless Usb won't connect"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Tweek3d920 on 2008-09-03
Ok, so I followed the steps in this [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495") Howto but the only out put I get is this

root@KungFu:~# sudo ifconfig wlan0 down
root@KungFu:~# sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:d1:47:d3:f5
Sending on   LPF/wlan0/00:14:d1:47:d3:f5
Sending on   Socket/fallback
root@KungFu:~# sudo ifconfig wlan0 up
root@KungFu:~# sudo iwconfig wlan0 essid "2WIRE724"
root@KungFu:~# sudo iwconfig wlan0 key restricted 1502805346
root@KungFu:~# sudo iwconfig wlan0 mode Managed
root@KungFu:~# sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:d1:47:d3:f5
Sending on   LPF/wlan0/00:14:d1:47:d3:f5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any suggestions? Thank you in advance

---

### Post by mavreix on 2008-09-05
I have the same issue, except Im connecting with WPA encryption.  I wish I could solve the problem, if you do let me know.  I have a connection shown but theres no information being sent.

---

### Post by Tweek3d920 on 2008-09-05
Well, I tried connecting with KNetworkManager and it will connect to my network but when it gets to the IP configuration stage it disconnects saying that an IP address could not be assigned. As far as I know my router uses DHCP but then again it's one of those piece of **** router/modem combos included with the ATT Internet Service. Any suggestions please let me know. I'm going to continue trying

---

