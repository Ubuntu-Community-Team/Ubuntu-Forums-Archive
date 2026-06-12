---
title: "Woun't stop connecting on eth0"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by Kimmern55 on 2006-11-07
Hey! I'm connected to a wireless network on eth1..but in my sys.log I see that my computer tries to connect to eth0 all the time..maybe every other minute..how can I make it stop? I'm already connected to eth1, so don't know why it does that!..eth0 is wired network, witch i almost don't use..but can't remove it either..no network cable is connected to my laptop either..so..any suggestions? I use Kubuntu edgy..

For the record..i've tried ifconfig eth0 down and ifconfig eth0 stop..

This is the "loop" I have in my syslog..over and over again:

Nov  7 11:02:42 kimmern-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov  7 11:02:51 kimmern-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov  7 11:02:58 kimmern-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov  7 11:03:11 kimmern-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov  7 11:03:30 kimmern-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Nov  7 11:03:34 kimmern-laptop dhclient: No DHCPOFFERS received.
Nov  7 11:03:34 kimmern-laptop dhclient: No working leases in persistent database - sleeping.

---

