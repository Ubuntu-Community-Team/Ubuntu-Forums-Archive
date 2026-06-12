---
title: "router access and ethernet problem"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by anything2 on 2008-07-09
Hi 
i am trying to access my router but cannot

I have a NETGEAR wgr614 v8 router connected to my ethernet slot
I have wifi enabled and working 
the netgear router is for my home network 
no internet on it and right now its not connected to anything else just my ethernet port

I have the following problems
I just want to access the router page
It shows an ip of 169.254.x.x

I tried static ips  as 192.168.1.x
and also 192.168.0.x and 192.168.2.x 
but nothing helped

I read everything could find but nothing seems to work

i can ping it

I also found out that theres a problem with the dhcp server
I tried to fix it using instructions on a website i found but it didnt work either

tried to edit /etc/network/interfaces
which basically amounts to the same thing

can someone help me out to access my router
thanks

---

### Post by rlzyoner on 2008-07-09
Generally a 169 address means that your machine is not being assigned an Ip address from the router.

Strange that this would be the case if you can ping the router.

Are you sure that you are not pinging the router via your wireless connection.
If so, its probably an issue with the ethernet cable, try another one

---

