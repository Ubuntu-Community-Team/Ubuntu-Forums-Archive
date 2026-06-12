---
title: "Belkin wireless usb adaptor stopped working?"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by gazz1982 on 2008-08-10
I have a belkin wirles G usb adapter, it has been working fine for the last 6 months this morning it refused to work

I tried sudo /etc/init.d/networking restart

but it said:

wlan: error while getting interface flags: no such device
error for wireless request "set encode" (8B2A) :
   Set failed on device wlan0 ; no such device.
Error for wireless request "SET ESSID" 8B1A
There is alredy a pid file /var/run/dhclient.wlan0.pid with pid 134519072

SIOCSIFADDR: no such device
wlan0 error while getting interface flags: no such device
wlan0 error while getting interface flags: no such device
Bind socket to interface: no such device
Failed to bring up wlan0.

any ideas?

I have been playing with virtual hosts yesterday but I cant see how that would affect it

Thanks

Gazz

---

