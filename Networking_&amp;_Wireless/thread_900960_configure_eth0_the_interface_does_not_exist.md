---
title: "configure eth0: the interface does not exist"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by wuda_cn on 2008-08-25
after installing ubuntu 8.04, i try to connect internet, but i can not connect it. i can ping my router, but i can not ping [www.yahoo.com](www.yahoo.com). 

and i configure static ip on eth0, and in nettool, when i choose eth0 and click configure button, a "the interface does not exist" message is appeared.

BTW, i found that the configuration of eth0 is in /etc/network/inferfaces file.

could you help me to fix it.

thanks very much.

---

### Post by Iowan on 2008-08-27
Post **/etc/network/interfaces** file and results of **ifconfig.** (You might also check results of **lspci** to verify the network card is recognized.)

---

