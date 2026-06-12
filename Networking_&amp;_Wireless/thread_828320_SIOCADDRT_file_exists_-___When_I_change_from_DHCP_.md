---
title: "SIOCADDRT: file exists -   When I change from DHCP to static"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2008-06-13
I changed my Static setting to DHCP and then back to static and I get an error SIOCADDRT - this file already exists (or something like that).  I change it back to DHCP and it works well, but I still can't get it to change back to the static address that I had it set on previously.  

Now when I change the static address to another address, I get no errors when I restart the network after changing the static IP addy.  What's going on?

---

### Post by Leo Simon on 2011-10-04
I'm having a similar problem.    When I first log on to my static Ip, it sometimes doesn't work, when I try again I get the SIOCADDRT: file exists message.   The web suggests a fix::

netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
128.32.175.0    *               255.255.255.0   U         0 0          0 eth4
10.10.196.0     *               255.255.252.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         10.10.196.1     0.0.0.0         UG        0 0          0 wlan0
default         g3-40.inr-240-m 0.0.0.0         UG        0 0          0 eth4


ip route delete 128.32.175.0 dev eth4

But it doesn't work and I get the response.
RTNETLINK answers: No such process

Any advice would be most appreciated

---

### Post by jonobr on 2011-10-04
Recommend you post the exact error message along with the results of ifconfig and /etc/network/interfaces


also having a look at dmesg may show you something.

---

