---
title: "Problems accessing only one https server"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by jure1873 on 2008-08-13
I've got a very strange connectivity problem: When I try to open a connection to a apache server the connection is estabilished but then stalls until a timeout. Same problem with ssh. It seems like it works for the first few seconds and then it stops working or it stops working after big packets start to come/get sent. Small html pages load fine, complex ones do not.

I'm behind nat and the other server that I'm trying to access is also behind nat (with port forwarding for apache and ssh). 

The funny thing is that I can access all the pages on that server from a windows installation inside vmware on my pc. How is this possible? 

I thought it's a mtu problem, but if I do ifconfig eth0 mtu 500 it still doesn't work.

---

