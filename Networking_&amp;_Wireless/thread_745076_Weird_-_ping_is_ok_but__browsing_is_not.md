---
title: "Weird - ping is ok but  browsing is not"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by gxyz1234 on 2008-04-04
Hi,
After installing Ubuntu 7.10 and configuring the wireless (static IP), I have
ping working by either using IP or DNS. However, when trying firefox (http) I can only connect to only two sites - Mozilla.org & fedoraproject.org ! . Any other site (google/ yahoo/ etc..)  gives "Waiting for ____"  and finally fail !!!. Also wget fails as well. I guess something is blocking the http protocol. Thus, I have tried to check the iptables but it is empty. 

I have another windows box with the same static configuration (ip,msak,gw, dns) with no problems.

The route command gives: 
Kernel IP routing table
Destination     Gateway         Genmask    Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0         0        0 eth1
link-local           *                255.255.0.0      U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100      0        0 eth1


Please help..... Thanks!

---

### Post by superprash2003 on 2008-04-04
have you configured the DNS in your pc or your router?

---

### Post by rickyjones on 2008-04-04
Do you have a proxy server on your network in any fashion that we might be overlooking? That is the only area that I can think of right now.

-Richard

---

### Post by gxyz1234 on 2008-04-04
I have configured the DNS in both machines ( Windows + Ubuntu).  However - since the ping is working with DNS it seems that it is http-related??

I do not use proxy   (system->preference->network proxy:  direct connection  to internet) . However, how can I follow the path of an http packet initiated from the browser??

---

### Post by superprash2003 on 2008-04-04
please post the output of cat /etc/resolv.conf

---

### Post by gxyz1234 on 2008-04-05
Hi All,
Installation of ubuntu on Vmware using NAT solved the problem. 
Thanks!

---

