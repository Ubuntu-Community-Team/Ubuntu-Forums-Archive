---
title: "dhcp to Static IP how to?"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by fisho on 2008-06-16
Hi all how do i go about making my laptop wireless connection have the a static IP address and make it point to my win2003 box for DNS  i can reserve ip in router ok.

I don't want to use DNS supplied by my router settings because when i tyr to access a webpage on win 2003 i get prompted for router user and password when [www.XXX.XX](www.XXX.XX) the address is ok if i use [http://XXX.XX](http://XXX.XX)   for it tho..

want to access my exchange server aswell
what files do i need to edit and how on ubuntu 7.10

---

### Post by superprash2003 on 2008-06-16
for static ip you need to manually edit under system->administratoin->network .. for permanent DNS [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by tuproxy on 2008-06-16
Can't you edit
```
sudo nano /etc/network/interfaces
```

change the "dhcp" to "static"
and add:
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

Wouldn't this be the easiest way?

---

### Post by fisho on 2008-06-19
thanks man worked it out

---

