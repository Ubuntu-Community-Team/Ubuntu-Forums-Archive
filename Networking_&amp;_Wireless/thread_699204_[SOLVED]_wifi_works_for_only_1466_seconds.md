---
title: "[SOLVED] wifi works for only 1466 seconds"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Bad_Byte on 2008-02-17
[B]SOLVED: Used a wrt54gl router as a client-bridge mode (wrt54gl does the wifi as any other wifi client and linux get internet thou ethernet cable).
[/B]
I got a problem with kubuntu 7.10/64bit.
The wifi connection will only work for 1466 seconds, and then I have to reboot to get 1466 more seconds or use another wifi device (to get another 1466 seconds).

The 1466 (~24.5minutes) comes from dhclient, which sounds strange as the router is setup with a 60minute dhcp lease time.

```

:~# dhclient -d wlan0
There is already a pid file /var/run/dhclient.pid with pid 6215
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:15:af:2b:06:ef
Sending on   LPF/wlan0/00:15:af:2b:06:ef
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.32 -- renewal in 1466 seconds.

```

Edit: Fixed the dhcp issue but now ping & traceroute says "no buffer" after 5~15 minutes.

```

~ traceroute 194.24.252.207
traceroute to 194.24.252.207 (194.24.252.207), 30 hops max, 40 byte packets
send: No buffer space available

~ ping -c 3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

~ ping -c 3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 21042ms

```

---

