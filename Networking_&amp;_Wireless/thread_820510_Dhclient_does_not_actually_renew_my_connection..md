---
title: "Dhclient does not actually renew my connection."
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-06-06
When connecting to the internet through wireless, I use a little script in rc.local.

It looks like this:
```
ifconfig wlan0 up
dhclient -r wlan0
iwconfig wlan0 mode Managed
iwconfig wlan0 essid "linksys"
iwconfig wlan0 key MY_HEX_KEY open
dhclient wlan0
```


When I do it in terminal:
```
tom@Laptop:~$ sudo dhclient wlan0
[sudo] password for tom: 
There is already a pid file /var/run/dhclient.pid with pid 5547
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:44:7f:24:22
Sending on   LPF/wlan0/00:16:44:7f:24:22
Sending on   Socket/fallback
DHCPREQUEST of xxxxxx on wlan0 to 255.255.255.255 port 67
DHCPACK of xxxxx from xxxxxxx
bound to xxx.xxx.x.x -- **renewal in 42862 seconds.**
```

When it renews, it actually brakes my connection and have to manually run the script again.

How do I make it connect at renewal. or even make the time longer?

Thanks,
Tom

---

### Post by Tom--d on 2008-06-06
Bump

---

