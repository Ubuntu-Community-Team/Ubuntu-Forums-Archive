---
title: "DSL Connection problem with Ubuntu 15.04"
date: 2015-08-04
forum: Networking &amp; Wireless
---

### Post by pthfdr on 2015-08-04
When connecting using DSL a connection failure occurred:
Connection activation failed
(1)Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/13' failed in libnm-glib.
Config:
Connection name:&#65288;Entered)
General:
Automatically connect to this network when it is available:FALSE
All users may connect to this network:TRUE
Automatically connect to VPN when using this connection:FALSE
DSL:
Username:(Entered)
Service:(Entered)
Password:(Entered)
Ethernet:
Device MAC address:08:62:66:06:5D:EB(eth0)
Cloned MAC address:(None)
MTU:automatic
PPP Settings:
Allowed methods:EAP,PAP,CHAP,MSCHAPv2,MSCHAP
Use point-to-point encryption (MPPE):FALSE
Allow BSD data compression: TRUE
Allow Deflate data compressio:TRUE
Use TCP header compression: TRUE
Send PPP echo packets: TRUE
IPv4 Settings:
Method: Automatic (PPPOE) addresses only
DNS servers: 208.67.222.222,208.67.220.220

---

### Post by stroestefan on 2015-08-11
Please check if you have pppoe installed (sudo apt-get install pppoe). I took me sweet time searching the net for an answer to this message before I saw (tail -f /var/log/syslog) it wasn't installed ...

---

