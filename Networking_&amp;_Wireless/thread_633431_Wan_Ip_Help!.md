---
title: "Wan Ip Help!"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by davidallan on 2007-12-06
Hi,

Hope someone can shed some light on this.

I've a Ubuntu server which is assigned 1 LAN static ip and 1 WAN static ip on eth0. My dg834 router is configured to port forward incoming services to my server via the LAN static ip.

My problem is I cant seem to use the WAN ip of the server. it just times out(from remote pc). if i enter the routers WAN ip it works. So how can i get it to resolve the servers WAN ip address??? the server is listening on all addresses and i've even tried turning the firewall of the router and still nothing.

please help....:confused:

---

### Post by Original Brownster on 2007-12-06
Hi,
From what I understand you are trying to use a remote pc to connect to your server by an Ip address you have assigned as a WAN address.
As you have already found you can use the IP address of your router because the isp has assigned it to you, the dns records for that block of addresses is owned by the isp and hence the dns servers 'know' how to get to it.
How have you got this WAN address because you cannot simply choose an address in this way, you can only do this for your lan, sorry if I have missed something but external ip addresses are bought and handled by registrars that handle pointing them to the required servers via dns, a bit more info and I might be able to help some more?

---

### Post by davidallan on 2007-12-07
thanks for the reply. i received a block of 8 ips. 5 usable. from my ISP. i'm since found my problem - NAT needed turning off and wan ips assigned to my machine. thanks anyways:)

---

