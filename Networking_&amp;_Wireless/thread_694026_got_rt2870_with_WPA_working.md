---
title: "got rt2870 with WPA working"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Absurd on 2008-02-11
I got it working with the open driver this time

this will **not** work with networkmanager or wicd!

here's how I did it

first, get the rt2870 usb driver source tarball from [here](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

then, extract and follow the build instructions in README_STA for building

do

> sudo make install

then

> sudo rm -r /etc/Wireless
(don't need the start up script thingie

then, look in the iwpriv_usage.txt file in the directory for the driver source and scroll down to the "Examples" section for settings appropriate for you. For instance, for WPAPSK TKIP I entered (in a terminal)
> 	1. sudo iwpriv ra0 set NetworkType=Infra
	2. sudo iwpriv ra0 set AuthMode=WPAPSK
	3. sudo iwpriv ra0 set EncrypType=TKIP
	4. sudo iwpriv ra0 set SSID="AP's SSID"
	5. sudo iwpriv ra0 set WPAPSK="AP's wpa-preshared key"
	6. sudo iwpriv ra0 set SSID="AP's SSID"


then connect

> sudo dhclient ra0

voila

no networkmanager or wicd needed :D

[edit]dont' forget the alias in /etc/modprobe.d

create a file in /etc/modprobe.d/ titled rt2870sta, open it and enter

> alias ra0 rt2870sta

then edit /etc/modules and enter rt2870sta

---

