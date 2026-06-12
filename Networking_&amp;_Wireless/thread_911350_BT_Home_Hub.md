---
title: "BT Home Hub"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by Lex-Man on 2008-09-05
I'm trying to connect to a BT home hub (the white old one) from Ubuntu 8.04.

I have two wireless cards both which connect to the hub under windows (vista ultimate 64-bit) fine.  

I have a second router 3Com office connect which I can connect to from linux fine as long as I don't use WEP encryption. WPA-TSK works fine.

I have set the BT router to WEP/WPA-TSK/open and have not been able to connect at all.

I have tried using both wireless cards set to roaming and also tried to manually configure the cards nothing seems to work.  

Can anyone tell me what I am doing wrong?

---

### Post by Lex-Man on 2008-09-07
Ok I tried it again with the networking set on roaming and the router set to have no encryption and managed to connect for a few seconds before it failed.

Each time I tried to re connect to the router I was able to connect for a few seconds before the connection died.  Has anyone had a similar problem?

---

### Post by Lex-Man on 2008-09-07
I've also tried running through the manual wireless guide.

Here is a transcript of what happened.

lexman@lexman-desktop:~$ sudo ifconfig wlan0 down
lexman@lexman-desktop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:17:31:eb:8f:d0
Sending on   LPF/wlan0/00:17:31:eb:8f:d0
Sending on   Socket/fallback
lexman@lexman-desktop:~$ sudo ifconfig wlan0 up
lexman@lexman-desktop:~$ sudo iwconfig wlan0 essid "**********"
lexman@lexman-desktop:~$ sudo iwconfig wlan0 **********
iwconfig: unknown command "ad863633ee"
lexman@lexman-desktop:~$ sudo iwconfig wlan0 key  **********
lexman@lexman-desktop:~$ sudo iwconfig wlan0 key open
lexman@lexman-desktop:~$ sudo iwconfig wlan0 mode Managed
lexman@lexman-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:17:31:eb:8f:d0
Sending on   LPF/wlan0/00:17:31:eb:8f:d0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

