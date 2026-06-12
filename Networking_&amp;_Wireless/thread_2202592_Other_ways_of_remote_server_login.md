---
title: "Other ways of remote server login"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by subhojit on 2014-01-29
There is a remote server (VPN), the server acts as database server. Ther is also another server (same VPN) which is the webserver. In webserver it has Apache (prefork), PHP and MySql client installed. Database server has Mysql client and MySql server installed. The webserver was not able to connect to database server: ```
mysql -u root -h xxx.xx.xxx.xx -P 3306 -p
```
It was giving connection timed out error.

Also tried ```
mysql -u root -h xxx.xx.xxx.xx -P 22 -p
```
In this case it was giving connection refused error.

For both the errors I googled  and I got various suggestion from stackexchange, Ubuntu forums and blogs. I tried those suggestions which were opening ports, checking firewall configuration, MySql config changes to listen to ports. But none of them worked.

I am a beginner in networking, I was trying the suggestions and might have did something wrong in port configuration. Now I cannot even do ssh login in database server from my machine, it is saying connection timed out. I can login to webserver, as I did not changed its port configuration.

I want to uninstall openssh and start everything from fresh in database server.

So is there any way I can login to database server other than ssh?

I am stuck ](*,) and do not have any idea. Please help :) thanks in advance

---

### Post by TheFu on 2014-01-30
What other remote access tools did you setup?  As you know now, screwing with port 22 is just a bad idea especially if ssh (22 is the default port for that service) is the primary access method.
Is this an ISP box? If so, they usually have some method of "console access." Usually through their web-admin pages.

Otherwise, get your car keys and start driving.

---

