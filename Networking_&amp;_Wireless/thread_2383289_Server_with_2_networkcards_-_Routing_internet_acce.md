---
title: "Server with 2 networkcards - Routing internet access for subnet"
date: 2018-01-23
forum: Networking &amp; Wireless
---

### Post by gabrixl on 2018-01-23
Hi

First of I'm sorry if my english isn't the best.

Situation:

I have two virtual devices.

1 - Server for DHCP, DNS and Routing
- Networkcard 1: ens160, 192.168.102.10 > Private network
- Networkcard 2: ens192, 192.168.1.129 > Internet

2 - Test Client for private network
- Networkcard 1: ens160, 192.168.102.12 > Private network

My goal:
I want the private network to be connected with the internet from the server.

How do I need to setup the DNS and the DHCP? :confused:

Thank you in advance. :D

---

### Post by TheFu on 2018-01-23
Welcome to the forums.
What you want is a Linux router.  There are a few how-to GUIs about that.  Ars and TLDP have some of the best information.
[https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)
good luck.

---

### Post by SeijiSensei on 2018-01-23
Or you could start here:  [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29)

---

