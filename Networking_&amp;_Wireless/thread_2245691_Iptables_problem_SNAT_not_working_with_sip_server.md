---
title: "Iptables problem SNAT not working with sip server"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by alex266 on 2014-09-25
Dear,

Since yesterday i have a problem with my sip server/ iptables on my fw.

De SIP server inside my internal network is sending packets to our voip provider, so far so good. the firewall is sending those packets to the correct interface (eth0) (FORWARD) but after that its send the packet with its internal ip address to the internet.

My SNAT:
-A POSTROUTING -s 192.168.0.0/16 -o eth0 -j SNAT --to-source xxx.xxx.xxx.xxx



tcp dump on the fw:
15:37:11.200622 IP 192.168.15.11.5060 > xxx.xxx.xxx.xxx.5060: SIP, length: 507
15:37:13.200619 IP 192.168.15.11.5060 > xxx.xxx.xxx.xxx.5060: SIP, length: 507
15:37:17.200304 IP 192.168.15.11.5060 > xxx.xxx.xxx.xxx.5060: SIP, length: 507

as you can see this is not what it is supposed to do.

Does anyone know what i am doing wrong?

---

