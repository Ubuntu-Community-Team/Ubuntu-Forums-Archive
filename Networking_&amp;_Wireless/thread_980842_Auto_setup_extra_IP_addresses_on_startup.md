---
title: "Auto setup extra IP addresses on startup"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by jds340 on 2008-11-13
I'm using 8.04 and I've edited my /etc/networks/interfaces file to add these lines

>>> start of quote
auto eth1:0 eth1:1
iface eth1:0 inet static
address 192.168.1.30
netmask 255.255.255.0 
#
iface eth1:1 inet static
address 192.168.1.31
netmask 255.255.255.0 
>>>> end of quote

But when I reboot I don't get the extra addresses. What am I doing wrong, and more importantly where is the Ubuntu documentation on this? So I don't have to ask again.

Thanks

John Small

---

### Post by Iowan on 2008-11-13
Apparently NetManager has some issues - particularly with static addresses.  There are several suggested options - [this one]("http://ubuntuforums.org/showthread.php?t=974382") has worked for some folks.

---

