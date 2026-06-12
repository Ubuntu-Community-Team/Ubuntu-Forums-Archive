---
title: "Networking problem"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by banie on 2007-04-16
Hi all,

I using ubuntu 6.10. The problem is when I store DNS ip in networking setting, it change by itself to router ip. I already save. The network manager has conf file. But I dont know where is the file. My router Aztech 600ER.

Thanks.

---

### Post by Thingymebob on 2007-04-18
Try editing /etc/dhcp3/dhclient.conf
Add a line that reads

prepend domain-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;

Where xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx are the DNS IPs from your ISP

---

