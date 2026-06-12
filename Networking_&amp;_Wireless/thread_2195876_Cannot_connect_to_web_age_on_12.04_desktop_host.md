---
title: "Cannot connect to web age on 12.04 desktop host"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by bpgplus on 2013-12-26
I am trying to run a web page on a 12.04LTS desktop machine (specifically Calibre's Content Server).

The issue:
I can only connect to the 12.04LTS machine if I have made a connection from the 12.04LTS machine to the browser machine first.

Detail:
PC1 - 12.04LTS
PC2 - Win7 in this example
Local net 10.1.1.0/24 DHCP to both machines with exact same GW
PC1 browse HTTP://<PC1 IP>:8088 ---> ALWAYS SUCCESS
PC2 attempts to browse HTTP://<PC1 IP>:8088 ---> FAIL
PC1 continutous ping PC2, while PC2 attempts to browse HTTP://<PC1 IP>:8088 ---> SUCCESS
Stop ping from PC1 to PC2, then 5 minutes later PC2 attempts to browse HTTP://<PC1 IP>:8088 ---> FAIL AGAIN.

Repeatability : Always. PC1 must establish a connection to PC2 before PC2 can browse the web page.

IPTABLES rules - none beyond what was set by Ubuntu 12.04LTS install. UFW off. Did try to set an iptables rule of iptables -I INPUT -i eth1 -p tcp --dport 8088 -j ACCEPT ((eth1 is THE CORRECT interface for the wireless card)) with no positive result.

It can't be the web page as it is always available on PC1. As long as PC1 starts and continues the communication between PC1 and PC2, PC2 can browse.

Anyone know what am I missing that my Google-fu is not shedding light on in terms of 12.04LTS accepting new inbound connections?

---

### Post by Iowan on 2013-12-26
Can PC2 **ping ** PC1?

---

### Post by bpgplus on 2013-12-26
PC2 (w7) can only ping PC1 AFTER PC1 starts pinging PC2.

This has all the markings of a firewall on the Ubuntubox preventing new inbound connections, while allowing inbound-from-PC2 traffic from already-initiated-by-PC1 conversations

---

### Post by bpgplus on 2013-12-28
Update - it is not just Calibre. I've now installed nginx as another test with similar results

---

### Post by bpgplus on 2013-12-30
BUMP - No one has any ideas on this?

---

