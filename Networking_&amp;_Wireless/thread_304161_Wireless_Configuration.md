---
title: "Wireless Configuration"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by joaomario@edgy on 2006-11-21
Hi people, 

I did all teh process described on the document file:///F:/WifiDocs-Device-Belkin%20F5D7050%20ver%203000%20(Ralink%20rt73%20driver)%20-%20Community%20Ubuntu%20Documentation.htm to get the new driver working properly with the D-link G-122 device.

But, It is not working yet. Maybe it isn't configured properly.
- I tried to get an essid to rausb, but typing it with iwconfig rausb0 essid simply won't go in.
- I've tried the wep key(128)with the 7 numbers in the ASCII s:******* mode ( shown below), and the 13 digit key without the s. It did not work in both ways. And, below the key is weird, it doesn't match the one that is in the router.

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Channel=6  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:3734-3734-3533-3000-0000-0000-00
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**ifup rausb0**
There is already a pid file /var/run/dhclient.rausb0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:17:9a:b0:28:83
Sending on   LPF/rausb0/00:17:9a:b0:28:83
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**netstat -rn**
no values under Destination, Gateway, etc.

Windows says there is very good signal, so maybe there is someway to get a better signal level in Ubuntu.

Thank you very much for your attention.

Ps.: The tutorial about the driver installation is very well written and did work ok. I know it's close now...

---

### Post by FrodoB on 2006-11-21
If you are using 128bit wep the keys should either be 13 characters for ASCII  or 26 characters for HEX.

Here is a good generator that can help you make sure that these are correct:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

---

