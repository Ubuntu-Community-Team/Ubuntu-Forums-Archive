---
title: "about wireless connection"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by tanyeun on 2008-03-10
I can use ifup/down eth0 to open and close wired connection
does anyone know the command to close and open the wireless connection?
thx

David

---

### Post by wieman01 on 2008-03-10
Probably:
> sudo ifup eth1
> sudo ifdown eth1
To find out about the correct interfaces, do:
> sudo lshw -C network
> sudo iwlist scan
You can restart all network interfaces by issuing:
> sudo /etc/init.d/networking restart

---

### Post by tanyeun on 2008-05-20
thx wieman01 ^_^

---

