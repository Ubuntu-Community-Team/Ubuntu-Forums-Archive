---
title: "trouble with dhclient"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by bcardarella on 2007-02-10
I have 6.10 server installed and gave the server a static IP address. Everything works fine but in my /var/log/syslog file I have the following repeated several times an hour:

Feb 10 06:52:25 rails-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 10 06:52:28 rails-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 10 06:52:36 rails-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Feb 10 06:52:54 rails-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 10 06:53:09 rails-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 10 06:53:16 rails-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 10 06:53:26 rails-server dhclient: No DHCPOFFERS received.
Feb 10 06:53:26 rails-server dhclient: No working leases in persistent database - sleeping.


Like I said the server is set on a static IP address. There is no mention of DHCP in /etc/network/interfaces

How do I shutdown dhclient and prevent it from starting if the serer reboots? Thanks.


(and I did read the other post about DHCPDISCOVER but that wasn't dealing with a static config)

---

### Post by gradedcheese on 2007-02-10
If there's no mention of 'dhcp' in /etc/network/interfaces then I don't see why dhclient would run... you can make sure it's killed:

sudo killall dhclient

(or dhclient3 if that doesn't work).  See if it ever comes back after that.

---

### Post by bcardarella on 2007-02-10
That seemed to work. I guess dhclient3 was running in memory. Thanks!

---

