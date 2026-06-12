---
title: "[SOLVED] Mulitple network connections at once"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by lawentzel on 2008-10-17
Okay, this is annoying the heck out of me.  Guy I work with is able to have two connections going on with both Ubuntu 8.04 and 8.10.  On his laptop he has 5 connections going.  Four wireless connections and one wired.

I can't get two to work.  (Wired and wireless.)

So... what needs to be set or what sort of animal will I have to sacrifice to the network gods to get this working.

For those who are asking why...  I want to be able to access two different networks at the same time.  Thanks.

---

### Post by lawentzel on 2008-10-17
Sorry, I can get one or the other to work.  But not both at the same time. In case someone was wondering or was going to ask.

---

### Post by iponeverything on 2008-10-17
lets see..

edit /etc/network/interfaces

the format is pretty strait forward. do a man interfaces or google around a bit.. It can be used for wireless or wired. Give it shot and post back if you run in problems.

---

### Post by lawentzel on 2008-10-17
Here is what it says:

auto lo
iface lo inet loopback

Which is identical to my friends computer.

---

### Post by lawentzel on 2008-10-17
So searching the Internet, Google, and "man interface" I came up with several things I tried.  The one I thought should work, given what I read, did not.  It wouldn't grab the wireless network.
```
auto lo eth0 ath0

iface lo inet loopback

iface eth0 inet dhcp

iface ath0 inet dhcp
```

I then restarted my network connection using the following command:
```
sudo /etc/init.d/networking restart
```

I got the following:
```
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:04:76:51:19:87
Sending on   LPF/eth0/00:04:76:51:19:87
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.20.136 from 192.168.20.9
DHCPREQUEST of 192.168.20.136 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.20.136 from 192.168.20.9
bound to 192.168.20.136 -- renewal in 117312 seconds.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:75:08:2b
Sending on   LPF/ath0/00:15:e9:75:08:2b
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Just to make sure it didn't work, I looked at "ip addr".  Only the wired connection had an IP address assigned to it.

Thanks

---

### Post by lawentzel on 2008-10-17
I've resolved this!

Under System, Administration, Network.  Unlocked the app. Left Wireless connection to "Roaming mode enabled" and changed Wired connection to "Address: dhcp"

This resolved the issue. While the wireless network icon only shows the wireless connection, going into terminal and typing "ip addr" I have two unique IP addresses now.

Thanks.

---

