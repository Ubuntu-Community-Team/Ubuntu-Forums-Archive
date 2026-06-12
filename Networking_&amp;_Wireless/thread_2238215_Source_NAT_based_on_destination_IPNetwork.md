---
title: "Source NAT based on destination IP/Network"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by mark157 on 2014-08-06
Hi,

I have setup a strongswan VPN on AWS VPC to a Cisco ASA. The far end has requested I setup a source NAT to a specified IP however I need to ensure I only NAT if the traffic is destined to hosts on a particular VPN as I have several tunnels setup. For example;

AWS (local)
Local Host:   10.0.0.10
Public IP (AWS):  50.80.100.80   (Note, this the the AWS VPC public IP)
Private Subnet: 10.0.0.0/24

CISCO (remote)
Remote Public IP: 100.100.10.10
Remote Local Host: 100.100.10.10
Private Subnet: 172.16.10.10/32

I need to NAT all traffic from 10.0.0.0/24 to 192.168.1.10 for all traffic destined to 172.16.10.10/32. I am thinking it would look something like the following?

# iptables -t nat -A PREROUTING -s 10.0.0.0/24 -d 172.16.10.10/32 -j SNAT --to-source 192.168.1.10

Thanks in advance!
Mark

---

