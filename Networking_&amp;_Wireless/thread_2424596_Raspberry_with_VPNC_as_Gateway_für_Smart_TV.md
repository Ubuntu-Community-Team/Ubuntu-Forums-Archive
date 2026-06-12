---
title: "Raspberry with VPNC as Gateway für Smart TV"
date: 2019-08-11
forum: Networking &amp; Wireless
---

### Post by tonjver on 2019-08-11
Hi,

[COLOR=#242729][FONT=Arial]in my vacation house in Sweden I have fast Internet through fiber (local network 192.168.10.x) and want to connect my Samsung Smart TV via VPN to my FritzBox and thereby to my home network incl. NAS and my home internet connection to overcome geoblocking. VPN on FritzBOx 7490 is set up and I can connect. In set up a Raspberry Pi 3b+ with Ubuntu 18.04 (Bionic Beaver) and a fixed IP address 192.168.10.201. I used vpnc for network viewer and can connect to my FritzBox (192.168.178.1), access my NAS and the Internet through the FritzBox. I tried to set my Samsung TV with a fixed local IP and 192.168.10.201 as Gateway, subnet mask 255.255.255.0. Now there is my problem: which DNS Server do I need to set up in my TV (local from fiber network or home from FritzBox) I tried both DNSs but always got the error message on my TV that it´s not connected tot he Internet. Do I need to activate IP routing on my RaspBerry? If yes, how?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Many thanks,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]JV[/FONT][/COLOR]

---

