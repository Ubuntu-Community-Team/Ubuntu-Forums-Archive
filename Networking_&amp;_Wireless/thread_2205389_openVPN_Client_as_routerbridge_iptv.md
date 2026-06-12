---
title: "openVPN Client as router/bridge iptv"
date: 2014-02-13
forum: Networking &amp; Wireless
---

### Post by Andreas_Hiebsch on 2014-02-13
Hi Ya'll,

I've been working on theis senario for weeks now but I cannot solve my problem. 

I'm living in the US and want to watch german IPTV using my old german IPTV settop box.
To do so I set up a Debian 7 as openVPN tap server behind my parents router (Speedport v921) on port 1194.

germany:
 - Router v921 has 192.168.2.1 
 - vopenVPN Server 192.168.2.100
    - bridge between eth0 and tap0 (dhcp for clients 192.168.2.30 to 35)
    - gateway 192.168.2.1 
 
US:
- Router 192.168.1.1
- openVPN Client 192.168.1.100 (eth0 -> router)
  - bridge between eth1 and tap0 192.168.2.30 (eth1 -> LINUX PC FOR DEBUGGINGIP CHECK ETC later TVBOX)
  - gateway 192.168.2.1

Linux Box Behind eth1:
- IP from german DHCP 192.168.2.110
- gateway and dns 192.168.2.1 

Some of the setup work already but not all of it. 
The Linux box behind eth1 gets all DHCP info from the german router 192.168.2.1 incl. gateway and DNS.
I can ping every device from the openVPN, 192.168.2.1 as well as 192.168.2.110. I can also ping from ovpn server to ovpn client (i can pin all in germany and all in the us).
if I lynx a location service it shows my german ISP IP which is good :)

The only problem is the client behind eth1. I can ping 192.168.2.30 (tap0 ip) but i cannot ping 192.168.2.1 nor anythin else in germany.
Do I have to set some IP tables or anything else. BTW, I have no clue about iptables.



Thank you guys

Andreas

---

### Post by Andreas_Hiebsch on 2014-02-25
Got it to work. 
I missed to metion that I'm running the US Linux box 192.168.1.100 on a ESXi 5.1 server. 
I had to change the default [promiscuous mode]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1002934") on the network card/switch of the ESXi to allow all.
NowI can watch German IPTV in the US!

Andreas

---

