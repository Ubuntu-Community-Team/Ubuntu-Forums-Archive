---
title: "Can not browsing the Internet !"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by Mr. Me on 2006-09-14
Hi, 
Please i need some help 
i`m connicting to the internet via sattlite 
(Network) 
the brousing was fine last night but now i can not browsing the enternet from ubuntu. 

i can using the internet from windows its mean there is no problem with the conniction!

i re-inatalled ubuntu again and same problem no change 
when i checked the network feom linux i sow it active and i sow the IP address from my ISP. 

connicting to the internet without browsing !
also i didnt use proxy at all. 
any help for this problem? 
Regards,

---

### Post by mithras86 on 2006-09-14
I don't quite follow you. But there is a bug in Dapper Drake which means that you don't get an internet connection. 
Go to your network-manager and disable your interface. Then enable it, and you should get a new ip address and have a connection.
Through the console you can solve it with ```
sudo ifdown eth0
sudo ifup eth0
```where eth0 is yuor network interface.

---

