---
title: "problems with apache2 and joomla"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by Jarramundi on 2008-10-16
Hi, just beating my head around trying to get a copy of joomla up and running on my localhost, using apache2 mysql php etc. 
I've been through a million tutorials, but I think my problem stems from a previous install of xampp, which gave me nightmares (looping permissions debarcle) and I removed it. however the localhost still shows:
```
 http://localhost/xampp 
``` please tell me how I remove this.

Also... (it gets more painful)  when I try and start/restart apache2 using:
```
  sudo /etc/init.d/apache2 start/restart 
```
I get the following error:
```
 
[Fri Oct 17 00:31:02 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd (no pid file) not running
[Fri Oct 17 00:31:12 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```

It's doing my head in guys. I've been trying to nut it out for days.
Any progress will be hugely appreciated.

---

### Post by superprash2003 on 2008-10-16
i suggest your reinstall apache.. some of your apache files are affected as well.

---

### Post by Jarramundi on 2008-10-16
Yep... That won't solve the first problem though. How do I reset my localhost? Please I'm quite new to webbing in linux and it's a steep learning curve.

---

