---
title: "Duplicate offer and ack entries in DHCP log"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by barroncm on 2014-11-02
[COLOR=#000000]This happens for all clients. [/COLOR]
[COLOR=#000000]The dhcp server is authoritative and mac filtered.[/COLOR]
[COLOR=#000000]Any Ideas as to why this is occurring?
[/COLOR]Below is an example.

[COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPINFORM from 10.10.2.8 via eth0 [/COLOR]
[COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPINFORM from 10.10.2.8 via eth0 [/COLOR]
[COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPACK to 10.10.2.8 (00:15:00:1b:73:cd) via eth0 [/COLOR]
[COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPACK to 10.10.2.8 (00:15:00:1b:73:cd) via eth0[/COLOR]

---

### Post by Doug S on 2014-11-03
I saw your other same thread on this, and your bump. I looked into it for awhile, but I don't know... However, I am surprised by the order of the log entries as I would have expected this:```
[COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPINFORM from 10.10.2.8 via eth0 [/COLOR]
[COLOR=#000000][COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPACK to 10.10.2.8 (00:15:00:1b:73:cd) via eth0 [/COLOR]
Oct 31 17:57:50 server2 dhcpd: DHCPINFORM from 10.10.2.8 via eth0 [/COLOR]
[COLOR=#000000]Oct 31 17:57:50 server2 dhcpd: DHCPACK to 10.10.2.8 (00:15:00:1b:73:cd) via eth0[/COLOR]
```I.E I would have expected the log entires to be in the order of fetched and dealt with by the daemon. Here is a similar example from my server. Note how the log entries are in the daemon processed order and the actual packets, captured with tcpdump, are in a different order. (there is a one hour time offset between the two logs, something I have never bothered to fix):```
Oct 31 11:18:11 doug-64 dhcpd: DHCPREQUEST for 192.168.111.106 from 00:23:6c:8a:a3:bc via eth0
Oct 31 11:18:11 doug-64 dhcpd: DHCPACK on 192.168.111.106 to 00:23:6c:8a:a3:bc via eth0
Oct 31 11:18:11 doug-64 dhcpd: DHCPREQUEST for 192.168.111.106 from 00:23:6c:8a:a3:bc via eth0
Oct 31 11:18:11 doug-64 dhcpd: DHCPACK on 192.168.111.106 to 00:23:6c:8a:a3:bc via eth0
Oct 31 11:18:15 doug-64 dhcpd: DHCPDISCOVER from 00:23:6c:8a:a3:bc via eth0
Oct 31 11:18:15 doug-64 dhcpd: DHCPOFFER on 192.168.111.106 to 00:23:6c:8a:a3:bc via eth0
``````
2014-10-31 10:18:11.119956 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:23:6c:8a:a3:bc, length 300
2014-10-31 10:18:11.120013 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:23:6c:8a:a3:bc, length 300
2014-10-31 10:18:11.120142 IP 192.168.111.1.67 > 192.168.111.106.68: BOOTP/DHCP, Reply, length 300
2014-10-31 10:18:11.120213 IP 192.168.111.1.67 > 192.168.111.106.68: BOOTP/DHCP, Reply, length 300
2014-10-31 10:18:15.397896 IP 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:23:6c:8a:a3:bc, length 300
2014-10-31 10:18:15.398092 IP 192.168.111.1.67 > 192.168.111.106.68: BOOTP/DHCP, Reply, length 300
```For your case, I wonder if there are duplicate log entries, or some other odd thing. I would suggest to monitor things with tcpdump and correlate with the log file, and go from there.```
sudo tcpdump -n -tttt -i eth0 port 67 and port 68
```

---

