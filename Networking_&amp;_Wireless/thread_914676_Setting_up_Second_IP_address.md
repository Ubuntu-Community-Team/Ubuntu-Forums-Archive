---
title: "Setting up Second IP address"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by giedrius_lt on 2008-09-09
Hello all 
i am trying setting up second ip address by falowing 
sudo vi /etc/network/interfaces

auto eth0:1
iface eth0:1 inet static
address 192.168.1.60
netmask 255.255.255.0
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x

and then sudo /etc/init.d/networking restart
i get error 
Ignoring unknown interface eth0:1=eth0:1.

whats wrong ?

---

### Post by awe on 2009-10-08
I have exactly the same problem. Help greatly appreciated!

---

### Post by Iowan on 2009-10-08
How is eth0 set up - Network Manager? *Might* need to set up eth0 in the same file.

---

