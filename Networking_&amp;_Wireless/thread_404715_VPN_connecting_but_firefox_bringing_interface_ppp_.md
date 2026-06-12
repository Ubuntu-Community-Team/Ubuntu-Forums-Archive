---
title: "VPN connecting but firefox bringing interface ppp down"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by rolando on 2007-04-08
Hi

I am using Edgy Eft 6.10

I have been using nm-applet to connect to my university VPN for sometime now, and it works first time every time.

But I recently changed ISPs and now I am having this problem.

I connect to the VPN, the interface ppp comes up, as normal, I can ping google etc and other sites, but as soon as I connect to a website with firefox, BANG! the interface comes down. I check with ifconfig and lo and behold ppp has gone.

Here is my routing table before I connect and after, if anyone can make sense of it I would be very grateful.

Before

[FONT="Courier New"]Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
default         voyager.home    0.0.0.0         UG        0 0          0 wlan0[/FONT]

After

[FONT="Courier New"]Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
my-vpn.domain. 192.168.1.1     255.255.255.255 UGH       0 0          0 wlan0
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0
default         *               0.0.0.0         U         0 0          0 ppp0[/FONT]


Thanks 

Rolando

---

