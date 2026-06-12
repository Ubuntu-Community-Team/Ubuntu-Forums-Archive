---
title: "Strange Dchp Problem-Ip connectinity"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by arxontas on 2008-05-30
Guys and Girls :)

I have a strange problem !!!

The topoplogy of the network is :

DHCP server --->cisco router(Enabled for relaying dhcp)-->pc

I don't have access to cisco router to see exactly its configuration...

The problem is that all pcs (2 in total) get ip from the dhcp server but i can ping only to one.

Below you can see the log messages

root@dhcp1 ~]# tail -f /var/log/messages
May 30 10:07:24 dhcp1 dhcpd: DHCPREQUEST for 10.41.0.254 (192.168.131.5) from 00:02:02:19:80:97 via 10.41.0.1
May 30 10:07:24 dhcp1 dhcpd: DHCPACK on 10.41.0.254 to 00:02:02:19:80:97 via 10.41.0.1
May 30 10:07:40 dhcp1 dhcpd: DHCPREQUEST for 10.41.0.252 from 00:02:02:19:80:7a via bond0.2
May 30 10:07:40 dhcp1 dhcpd: DHCPACK on 10.41.0.252 to 00:02:02:19:80:7a via bond0.2
May 30 10:08:00 dhcp1 dhcpd: DHCPDISCOVER from 00:02:02:19:80:97 via 10.41.0.1
May 30 10:08:00 dhcp1 dhcpd: DHCPOFFER on 10.41.0.254 to 00:02:02:19:80:97 via 10.41.0.1
May 30 10:08:00 dhcp1 dhcpd: DHCPREQUEST for 10.41.0.254 (192.168.131.5) from 00:02:02:19:80:97 via 10.41.0.1
May 30 10:08:00 dhcp1 dhcpd: DHCPACK on 10.41.0.254 to 00:02:02:19:80:97 via 10.41.0.1
May 30 10:08:10 dhcp1 dhcpd: DHCPREQUEST for 10.41.0.252 from 00:02:02:19:80:7a via bond0.2
May 30 10:08:10 dhcp1 dhcpd: DHCPACK on 10.41.0.252 to 00:02:02:19:80:7a via bond0.2


i can ping to 10.41.0.252 but not in 10.41.0.254
THe difference that i noticed is that in case of 10.41.0.254

the DHCPREQUEST for 10.41.0.254 (192.168.131.5) from 00:02:02:19:80:97 [B]via 10.41.0.1
[/B]

and for 10.41.0.252 is 

DHCPREQUEST for 10.41.0.252 from 00:02:02:19:80:7a [B]via bond0.2
[/B]


Any help is welcome!!!!

---

### Post by arxontas on 2008-06-01
Guys any ideas ?

Maybe the problem is too strange:( !!

---

### Post by arxontas on 2008-06-04
Solved
Thanks For No Help!!!!!!!

---

### Post by Iowan on 2008-06-04
Your turn to be the help - what did you find that fixed it?

---

