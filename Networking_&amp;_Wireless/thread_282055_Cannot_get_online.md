---
title: "Cannot get online"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by mooscape on 2006-10-22
I have a HP compaq nx9110 running ubuntu dapper like a rocket.   I have since bought an IBM R40 that is running well except that I cannot get onto the internet from home (works well from the office and from hotel).  Both machines are running the same version of dapper, but only the HP can get online. From the Ubuntu Forum I read about trying:

 sudo /etc/init.d/networking restart

I get the following result :

mel@mel-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
SIOCADDRT: Network is unreachable
Failed to bring up eth0.
                                                                                                                      [ ok ]
mel@mel-laptop:~$

Can anyone help me?

---

### Post by closer9 on 2006-10-25
EDIT:
Sorry, moved to a different thread. The more I looked into it, doesnt seem like the same problem as the OP.

Free bump I guess :-P

---

### Post by mooscape on 2006-10-28
Note .... have moved thread to [http://www.ubuntuforums.org/showthread.php?t=284190](http://www.ubuntuforums.org/showthread.php?t=284190)

---

