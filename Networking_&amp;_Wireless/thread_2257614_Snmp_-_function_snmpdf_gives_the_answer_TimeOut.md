---
title: "Snmp - function snmpdf gives the answer TimeOut"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by support6 on 2014-12-21
I h[COLOR=#333333][FONT=UbuntuRegular]ave a big problem.[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]In Ubuntu 14.04 I installed: 
1) apt-get install snmpd 
2) apt-get install snmp 
3) apt-get install snmp snmp-mibs-downloader[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I want run snmpdf: ,, snmpdf -v 2c -c public 192.168.72.129 " then I waited 5 second and I got answer ,, snmpdf: Timeout "[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In /etc/snmp/snmp.conf I comment out line ,,#mibs".
 In /etc/snmd/snmpd.conf i Comment out line ,,# rocommunity public default -V systemonly" and i wroterocommunity public 172.16.0.0/20.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I was looking for solutions but I can't find the answer anywhere.
 Please, help me.[/FONT][/COLOR]

---

