---
title: "Belkin FD7050 V1000 can be seen but isnt working"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by pfwd.tech on 2007-05-26
Hi,
i have a Belkin FD7050 usb wireless adapter.  When i lsusb it says that its version 1000
I'm also using Ubuntu 7.04.
In system/administration/network it lists that i have a wireless connection and that it's in roaming mode. Also in the network icon (by the date and volume control) it list my wirless network.
When i try and access it it refuses the connection. 

When  $ sudo ifup wlan0
i get the following 

```

wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


```
This is out of the box no ndsiwrapper. 
Do i need to use ndiswrapper even tho it can see a wireless connection.
Any help and advice welcome
Thanks

---

### Post by pfwd.tech on 2007-05-26
I have done some searching but im not sure if im going down the right path.
i have found that i have version 1000 of this chipset and according to the prism 54 project the chipset is 	GW3887.
on the thread : [http://ubuntuforums.org/showthread.php?p=2543573](http://ubuntuforums.org/showthread.php?p=2543573) Vixvix is using PRISMAXP.sys.
Can someonne tell me how to get this file?  and what i need to do with it. The files i get from the prism54 project are .arm and i don't know what to do  with them.

Also i have downloaded the exe from the belkin site but i cant find the correct .sys and .inf files.

Any help would be great!!

---

