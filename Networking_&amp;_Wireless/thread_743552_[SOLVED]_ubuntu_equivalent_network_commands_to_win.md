---
title: "[SOLVED] ubuntu equivalent network commands to windows cmd"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-04-02
Hi,
What are the equivalent Ubuntu terminal commands for:

ipconfig                 ... Show information

ipconfig /all           ... Show detailed 

ipconfig /renew    ... renew all adapters

---

### Post by koenn on 2008-04-02
ipconfig --> ifconfig
try ifconfig --help or man ifconfig for switches and parameters


for ipconfig /renew , you have a choice : 
dhclient
/etc/init.d/networking restart
ifdown && ifup
and probably also ifconfig [interface] down && ifconfig [interface] up

---

### Post by Iowan on 2008-04-02
**ifconfig** is Ubuntu's version of **ifconfig** .
**man ifconfig** should provide a wealth of information.

---

