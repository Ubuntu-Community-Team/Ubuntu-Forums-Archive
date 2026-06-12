---
title: "wvdial setup"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2006-11-19
I am trying to set up wvdial and I need to get into the config file so I can set up my connection settings. Could someone tell me how to get the wvdial.txt so I can edit and save that file. I have tried to use wvdialconf but have not been able to edit that file. If I dubble click on it it will open but it will not let me save the file after I edit.

---

### Post by Amitava on 2006-11-19
The wvdial config file wvdial.conf is in /etc, so without adm(who installed ) privilage you can't edit the file , so do the following --

sudo vim /etc/wvdial.conf
_My /etc/wvdial.conf file for bluetooth conn to my GPRS mobile_
[Modem0]
Modem = /dev/rfcomm0
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
[Dialer gprs]
Username = guest
Password = guest
Phone = *99#
Stupid Mode = 1
**Inherits = Modem0**
Command to connect
wvdial gprs

---

