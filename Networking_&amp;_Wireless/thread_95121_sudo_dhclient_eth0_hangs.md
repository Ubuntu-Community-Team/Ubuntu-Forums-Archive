---
title: "sudo dhclient eth0 hangs"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by juanit086 on 2005-11-25
yep it hangs randomly, sometimes it runs perfect and gets ip faster than light but sometimes it hangs and i cant get ip while booting.

any solution??

im abroad using cable modem though ethernet.

---

### Post by Lambert on 2005-11-25
Try running this command randomly at times. Curious if there is another router within range

sudo iwlist <logical_name> scan

logical_name = the name given to your interface wlan0 eth0 ath0 etc...

---

### Post by juanit086 on 2005-11-26
r0cha@ROCHAMAINubuntu:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
r0cha@ROCHAMAINubuntu:~$ sudo iwlist eth0 scan
Password:
eth0      Interface doesn't support scanning.

r0cha@ROCHAMAINubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:01:02:7f:ac:9f
Sending on   LPF/eth0/00:01:02:7f:ac:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19

r0cha@ROCHAMAINubuntu:~$ sudo dhclient eth0
sudo: timestamp too far in the future: Nov 26 11:57:34 2005
Password:
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:01:02:7f:ac:9f
Sending on   LPF/eth0/00:01:02:7f:ac:9f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.203.80.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.203.80.1
bound to 82.158.13.38 -- renewal in 1654 seconds.
r0cha@ROCHAMAINubuntu:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.102.9.147) 56(84) bytes of data.
64 bytes from 66.102.9.147: icmp_seq=1 ttl=243 time=42.0 ms
64 bytes from 66.102.9.147: icmp_seq=2 ttl=243 time=41.7 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2001ms
rtt min/avg/max/mdev = 41.772/41.918/42.064/0.146 ms
r0cha@ROCHAMAINubuntu:~$

it runs randomly :(

---

### Post by juanit086 on 2005-11-26
i have tested suse 9.1 and it works perfectly with my cable modem and windows too, but ubuntu...

---

### Post by juanit086 on 2005-11-26
ive already tested using acpi=off at grub, but sudo dhclient eth0 keeps running randomly

---

