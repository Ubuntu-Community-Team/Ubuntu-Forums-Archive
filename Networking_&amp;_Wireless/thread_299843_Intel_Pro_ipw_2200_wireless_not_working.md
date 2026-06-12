---
title: "Intel Pro ipw 2200 wireless not working"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by typsy on 2006-11-14
Hello,
I have installed xubuntu 6.10 today on my sony vaio laptop and everything works great except that my wireless is not working. Iam trying to connect to netgear wireless router with security disabled, but still I get the following error message - 

Listening on LPF/eth1/00:13:ce:7f:cf:8d
Sending on   LPF/eth1/00:13:ce:7f:cf:8d
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

I searched this forum and tried to execute the recommended commands in other threads but nothing helped. Any help on this is greatly appreciated.

Thank you,
VJ

---

### Post by unbuntu kid on 2006-11-14
does your wireless device show up as an internet connection device in networking?

Try this: [http://ubuntuforums.org/showthread.php?t=290164](http://ubuntuforums.org/showthread.php?t=290164)

---

### Post by typsy on 2006-11-14
Yes,
I can see that.

VJ

---

### Post by unbuntu kid on 2006-11-14
do a google on Linuxant and try their software.  It uses the windows driver of the device and installs them in linux.  sadly, after 30 days it costs $20

---

### Post by peterw on 2006-11-14
Have you looked closely at
  [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

In my case ([http://www.tux.org/~peterw/v2000/](http://www.tux.org/~peterw/v2000/)), I merely had to switch from the "ipw" driver to the "wext" driver when I upgraded from 5.10 to 6.06.

I have not tried wireless with 6.10 (still running 6.06).

-Peter

---

