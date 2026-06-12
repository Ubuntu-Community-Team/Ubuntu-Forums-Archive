---
title: "Wireless Suddenly Stopped Working"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by cranley on 2008-04-18
Hey all - I'm typing this from my Vista based work laptop (wireless connection) - everything's good here.  I was out of town for 9 days, I came home, fired up my Ubuntu box and although it connects to the network, there's no internet (same ol' story, I know).  Output:

> cranley@cranley-desktop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 12495
Killed old client porcess, removed PID file
Internet Systems Consortium DHCP Client v3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:12:17:59:ee:e0
Sending on LPF/eth1/00:12:17:69:ee:e0
Sending on Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCADDRT: No such process
bound to 192.168.1.103 -- renewal in 42674

> cranley@cranley-desktop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.
eth1 IEEE 802.11b/g ESSID:"Myskwin" Nickname:"Broadcom 4318" Mode:Managed Frequence=2.437G GHz Access Point: 00:16:B6:2C:DA:4E Bit Rate=24 Mb/s Tx-Power=19dBm RTS thr:off Fragment thr:off EncryptionKey[withholding this i am because i'm paranoid] Security mode: open Link Quality=50/11 Signal level=-60 dBm Noise level=-72 dBm Rx invalid nwid:0 Rx invalid crypt:92 Rx invalid frag:0 Tx excessive retries: 0 Invalid misc:0 Missed beacon:0

vmnet1 no wireless extensions.
vmnet8 no wireless extensions

This is on Gutsy.  Was working fine last time I shut it down - all of a sudden it's puke city.  I can ping my router, but I can't hit the admin interface in Firefox.  I tried following the advice of others and set the IPv6 disabled flag in about:config to true, but still no dice.

Anybody have any ideas?  I'm stumped stumped and not totally knowledgeable about the finer workings of linux.

Thanks in advance.

---

### Post by cranley on 2008-04-18
> cranley@cranley-desktop:~$ route
Kernel IP routing table
Destination           Gateway  Genmask            Flags   Metric   Ref   Use    Iface
192.168.1.0         *              255.255.255.0  U          0          0       0        vmnet8
192.168.1.0         *              255.255.255.0  U          0          0       0        eth1
192.168.219.0     *              255.255.255.0  U          0          0       0        vmnet1


Honestly, I don't know enough for the above to make much sense - however, is it possible vmnet8 and eth1 are conflicting?  Why is eth1's Use denoted as false?

---

