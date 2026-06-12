---
title: "Ubuntu 16.04 LTS as Router Port Forwarding Not Working"
date: 2017-03-24
forum: Networking &amp; Wireless
---

### Post by huntersfo on 2017-03-24
Hello, 


I have recently installed a Ubuntu Server 16.04 LTS and would setup this server as router between internet and intranet. 


Interface settings: 
1. Intranet: interface eno1, address 192.168.5.3 (static IP)
2. Internet: interface eno4, address 10.9.8.3 (static IP, behind an ISP router)


Requirement: 
The intranet Linux host 192.168.5.1, needs to be accessible from internet via public port 40099.
forward internet port 10.9.8.3:40099, to the intranet port: 192.168.5.1:22.


I did extensive search on Google and Youtube for the Ubuntu Router setup, but no luck for several days.


Here are the settings: 
cat /proc/sys/net/ipv4/ip_forward
1


To keep the troubleshooting simple, I set all INPUT and FORWARD default to ACCEPT.
iptables-save
*nat
: REROUTING ACCEPT [3723:437711]
: INPUT ACCEPT [2847:316535]
: OUTPUT ACCEPT [5511:415020]
: POSTROUTING ACCEPT [200:14243]
-A PREROUTING -i eno4 -p tcp -m tcp --dport 40099 -j DNAT --to-destination 192.168.5.1:22
-A POSTROUTING -o eno4 -j MASQUERADE
COMMIT
# 
*mangle
: PREROUTING ACCEPT [892492:1452087772]
: INPUT ACCEPT [22013:5691695]
: FORWARD ACCEPT [870476:1446395801]
: OUTPUT ACCEPT [14229:3022179]
: POSTROUTING ACCEPT [884705:1449417980]
COMMIT
# 
*filter
: INPUT ACCEPT [0:0]
: FORWARD ACCEPT [0:0]
: OUTPUT ACCEPT [14229:3022179]
-A INPUT -j ACCEPT
-A FORWARD -j ACCEPT
COMMIT




Here are the worked parts:
The intranet hosts (192.168.5.1) could access the internet by set the router address of this router (192.168.5.3).
From the router(192.168.5.3) I can remotely login to the intranet host 192.168.5.1 via SSH.
It works when I set the port forwarding to the router itself (map 10.9.8.3:40099 to 192.168.5.3:22).


Based on the above configuration, I still cannot access from internet (10.9.8.3:40099) to get the SSH login prompt of intranet host 192.168.5.1. 


fixed.

---

