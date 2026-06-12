---
title: "Suspend kills wlan – how to reactivate it reliably?"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by Tobias Franz on 2006-08-29
Why can my Amilo M1425 not reconnect to the internet after I take it out of the suspend mode? It used to work fine with Breezy Badger, now since the update to Dapper LTS I have this frustrating problem and have to restart it completely most of the time. It doesn't help to disconnect and connect again with ifdown eth1, ifup eth1. Only on rare occacions it finds a connection all by itself. This is the output of tail -f /var/log/syslog on this occasion:

Aug 29 11:59:14 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Aug 29 11:59:19 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Aug 29 11:59:21 localhost kernel: [17193690.624000] eth1: no IPv6 routers present
Aug 29 11:59:25 localhost kernel: [17193694.960000] TKIP: replay detected: STA=00:01:e3:4f:e4:ee previous TSC 000000000000 rec eived TSC 000000000000
Aug 29 11:59:31 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Aug 29 11:59:35 localhost kernel: [17193704.972000] TKIP: replay detected: STA=00:01:e3:4f:e4:ee previous TSC 000000000000 rec eived TSC 000000000000
Aug 29 11:59:45 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 29 11:59:45 localhost kernel: [17193714.984000] TKIP: replay detected: STA=00:01:e3:4f:e4:ee previous TSC 000000000000 rec eived TSC 000000000000
Aug 29 11:59:52 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Aug 29 11:59:55 localhost kernel: [17193724.996000] TKIP: replay detected: STA=00:01:e3:4f:e4:ee previous TSC 000000000000 rec eived TSC 000000000000
Aug 29 11:59:58 localhost kernel: [17193728.136000] ipw2200: Failed to send RSN_CAPABILITIES: Command timed out.
Aug 29 11:59:59 localhost kernel: [17193729.136000] ipw2200: Failed to send SSID: Command timed out.
Aug 29 12:00:03 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Aug 29 12:00:15 localhost dhclient: No DHCPOFFERS received.
Aug 29 12:00:15 localhost dhclient: No working leases in persistent database - sleeping.
Aug 29 12:00:15 localhost ntpdate[714]: can't find host ntp.ubuntu.com
Aug 29 12:00:15 localhost ntpdate[714]: no servers can be used, exiting
Aug 29 12:00:15 localhost postfix/master[4690]: reload configuration /etc/postfix
Aug 29 12:00:28 localhost kernel: [17193758.136000] ipw2200: Failed to send CARD_DISABLE: Command timed out.
Aug 29 12:00:30 localhost kernel: [17193759.744000] TKIP: replay detected: STA=00:01:e3:4f:e4:ee previous TSC 000000000000 rec eived TSC 000000000000
Aug 29 12:03:33 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Aug 29 12:03:33 localhost dhclient: DHCPOFFER from 192.168.2.1
Aug 29 12:03:33 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Aug 29 12:03:33 localhost dhclient: DHCPACK from 192.168.2.1
Aug 29 12:03:33 localhost dhclient: bound to 192.168.2.3 -- renewal in 66951 seconds.

What do I need to do to get a reliable reconnection after suspend?

---

### Post by ltmon on 2006-08-29
I have a similar problem with the intel pro wireless 3945 drivers.  It occasionally just gives up after returning from suspend.

I work around it with a script that unloads and reloads the drivers when I call it.  For you I think it would look similar to:

```

#!/bin/sh
/etc/init.d/networking stop
rmmod ipw2200
modprobe ipw2200
/etc/init.d/networking start

```

I can't say for sure if this will work, but try it anyway and see if it makes a difference.

L.

---

### Post by Tobias Franz on 2006-08-29
Thanks, this seems to work. Now I wonder if it would make sense to append this script to some other file that is responsible for reactivation after suspense, so it will be executed automatically every time. But I would not know where this file is.

---

