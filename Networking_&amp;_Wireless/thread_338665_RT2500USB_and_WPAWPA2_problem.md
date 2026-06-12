---
title: "RT2500USB and WPA/WPA2 problem"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by giosetti on 2007-01-14
I proceeded the way described in WLAN Howto and chose "Sample configuration mixed mode (WPA1, WPA2) & DHCP, ESSID broadcast" with this result:

giosetti@ubuntu:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:5a:24:c1:35
Sending on LPF/eth0/00:80:5a:24:c1:35
Sending on Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/rausb0/00:13:d4:09:29:9c
Sending on LPF/rausb0/00:13:d4:09:29:9c
Sending on Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:5a:24:c1:35
Sending on LPF/eth0/00:80:5a:24:c1:35
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.102 -- renewal in 133651 seconds.
[ ok ]

Some complementary information:

giosetti@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

rausb0 RT2500USB WLAN ESSID:""
Mode:Managed Frequency=2.412 GHz Bit Rate=11 Mb/s
RTS thrff Fragment thrff
Link Quality=0/70 Signal level:-120 dBm Noise level:-216 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

giosetti@ubuntu:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

sit0 Interface doesn't support scanning.

rausb0 Scan completed :
Cell 01 - Address: 00:12:BF:9B:B1:A7
Mode:Managed
ESSID:"mywlanessid"
Encryption keyn
Channel:1

Any idea what the problem might be? Is wext the good WPA driver?

Thx,
J.

---

