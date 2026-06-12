---
title: "Does a UniFi Access Point need a driver?"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by robert48 on 2015-11-24
Hello

I'm trying to get a UniFi AP by Ubiquiti working on 64bit Ubuntu 15.10. It works on Windows 7 which makes me think it may be a driver issue with Ubuntu.

The device works as a wireless access point and connects itself by ethernet cable to an wired ethernet port on the router.

Thanks in advance
Bob

---

### Post by Hadaka on 2015-11-24
Hi, short answer. No it does not. The driver controls the computers wifi device and if correct
should connect to any access point *if the configuration for the access point is also correct.
You are able to access it with windows so you or someone has obviously set up the access point
correctly. Does your Ubuntu machine attach to other wifi connections?..your router,starbucks,or
where ever?? If so, all you need to do is configure the ssid and whaterver setting like you do with
any other router,range extender,repeater,hotspot..its just an access point..no special driver

---

### Post by robert48 on 2015-11-24
Thanks Hadaka, I'll keep trying to work out what's happening. I've  changed USB wireless adapter and have that running OK at the moment. I  find that turning off wireless network, unplugging USB adapter, turning  on wireless network then plugging in USB adapter works. Tried it with  original USB adapter and that works as well. However if I restart with  wireless network on and USB adapter attached when it comes up again the  network icon looks OK but there is no internet connectivity. The router  was set with a dynamic dns service which indicated it needed updating.  I've turned the dynamic dns off and we'll see if that helps.

---

### Post by rslater on 2015-12-03
If you know the IP address of the UniFi you can connect to it through a browser, using the standard Ubiquiti account and password (unless changed) and configure the UniFi from there.  The only software with the UniFi is a management package which can be useful if you are running many access points.

Hope this is of some help.

---

