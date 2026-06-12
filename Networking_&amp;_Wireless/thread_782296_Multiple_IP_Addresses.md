---
title: "Multiple IP Addresses"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by sakid on 2008-05-04
Hi all,

I've been searching for a few days but can't the info im looking for, so here i am.

I'm wondering if there is a way I can assign multiple IP addresses to my network interface - like an alias i guess. I know it can be done easily in Fedora, can it be done in Ubuntu?


Thanks

---

### Post by superprash2003 on 2008-05-04
go to System->administration->network and then go to the HOSTS tab

---

### Post by sakid on 2008-05-04
I had a look but I dont think thats what I need unless I'm missing something?

Ill clarify what I want to do.
I currently get a static ip from my dhcp server (192.168.10.20)
I want to also be to have an ip of 192.168.1.x at the same time to configure new hardware etc.

---

### Post by sakid on 2008-05-05
I've found how to do it if anyone else is interested..


```
sudo ifconfig eth0:0 192.168.1.1 up
```Where you would substitute eth0 for your network interface and 192.168.1.1 for the IP you want alais.

---

### Post by Paris Heng on 2008-05-05
> **sakid said:**
> I've found how to do it if anyone else is interested..


```
sudo ifconfig eth0:0 192.168.1.1 up
```Where you would substitute eth0 for your network interface and 192.168.1.1 for the IP you want alais.

Just edit all the IP address in /etc/network/interfaces, then restart the network.

Use belwo to check IP addr,

> ip addr show

---

