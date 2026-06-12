---
title: "arptables and multicast"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by povlhp on 2014-02-18
First a disclaimer, I am using OpenWRT as my distribution, but this is a general Linux question, thus I went to my favourite Linux forum:

[FONT=Verdana]Overview:
I have one STB that does Multicast IPTV. The rest of my devices can use udpxy and unicast.
My OpenWRT on TP-Link 3600 runs igmpproxy to allow the multicast to work. Fine.[/FONT]
[FONT=Verdana]I use a MOCA bridge between the STB and OpenWRT, and it seems to limit multicast to 10 Mbps, which is too slow for HDTV (it does 95 Mbps simultaneously both ways with iPerf UDP).[/FONT]
[FONT=Verdana]So I decided that I would try to use arptables to change the MAC address of the multicast packet leaving OpenWRT/Linux, to make it a unicast L2 packet.[/FONT]
[FONT=Verdana]I tried all the ones below without success. Also tried -i / -o with both eth0 and eth0.1 (LAN) and eth0.3 (Multicast input VLAN)[/FONT]
[FONT=Verdana]Why can't I change the destination MAC on multicast ? Is it not possible ? I hope that would fool the bridge to see it as unicast, and prevent the packets from going all over my network.[/FONT]
[FONT=Verdana]```
arptables -I INPUT -h-length 6 -d 233.0.0.0/8 -j mangle --mangle-mac-d 18:zz:yy:xx:5a:27
arptables -I OUTPUT -h-length 6 -d 233.0.0.0/8 -j mangle --mangle-mac-d 18:zz:yy:xx:5a:27
arptables -I FORWARD -h-length 6 -d 233.0.0.0/8 -j mangle --mangle-mac-d 18:zz:yy:xx:5a:27
[/FONT]
```
[FONT=Verdana]Funny that the Marmitek MOCA limits multicast to 10Mbps, as it is sold as being able to deliver HD IPTV. Trying to raise their support, and find out how to modify its PQoS. Tried to set QoS to EF and thus TOS to 0x88 with no luck. But clearly a bug in the firmware (hopefully upgradeable).[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by povlhp on 2014-02-18
I found out, that I probably need to use ebtables instead, catching the packets when they hit the interface.


So I did this (in addition to the arptables commands)


```
ebtables -t nat -A PREROUTING  -p ipv4 --ip-source ! 192.168.0.0/24 --ip-destination 233.0.0.0/8 -j dnat --to-destination 18:aa:bb:cc:dd:ee
```


still no luck rewriting the destination MAC address.


BTW: This page is great at showing the flow through ebtables and iptables :  [http://ebtables.sourceforge.net/br_fw_ia/br_fw_ia.html](http://ebtables.sourceforge.net/br_fw_ia/br_fw_ia.html)


ebtales seems to be empty for all tables when starting up.

---

