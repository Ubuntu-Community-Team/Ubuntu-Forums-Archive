---
title: "Can't connect to Internet from Ubuntu Server 18.04"
date: 2019-08-05
forum: Networking &amp; Wireless
---

### Post by Peter Alien on 2019-08-05
I'm testing Ubuntu Server 18.04 LTS in VMware and i have Windows 7 as Host.

I created a FTP Server in Ubuntu, and it works well. I can access it from Host using a Browser, typing: [ftp://192.168.160.10](ftp://192.168.160.10)

The problem is that i can't connect to the Internet from Ubuntu Server!!!


I leave the specs here:

Ubuntu Server Network Adapter (in VMware Workstation) => VMnet 8 (NAT)
IP Static: 192.168.160.10/24
Gateway: 192.168.160.2
DNS Servers: 8.8.8.8 and 8.8.4.4
(I'm using NetPlan to configure the network interface (ens33) in Ubuntu)



In Windows (using Command Prompt), i have:

Wifi Connection (LAN)
--------------------
IP Static: 192.168.1.68
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.254


VMnet8
-------
IP Static: 192.168.160.1
Subnet Mask: 255.255.255.0
Gateway: ---


Can anyone help me? Many thanks.

---

