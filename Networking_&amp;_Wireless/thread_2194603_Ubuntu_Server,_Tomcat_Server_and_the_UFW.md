---
title: "Ubuntu Server, Tomcat Server and the UFW"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by kmccmk9 on 2013-12-19
Hello, so I've been trying to get this website up and running under tomcat7. I've installed everything and basic html pages work. The war file is uploaded and again everything is fine. I add some firewall protection and suddenly I can't access the site anymore. I've tried everything. IPv4,IPv6, tomcat7 configuration...etc I can't figure out what's going wrong. It always ends with a 500 error timeout page. This is my ufw port map:

> 
To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
25                         ALLOW       Anywhere
80                         ALLOW       Anywhere
8080                       ALLOW       Anywhere
443                        ALLOW       Anywhere
3306                       ALLOW       Anywhere
9667                       ALLOW       Anywhere
22                         ALLOW       Anywhere (v6)
25                         ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6)
8080                       ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)
3306                       ALLOW       Anywhere (v6)
9667                       ALLOW       Anywhere (v6)


Please let me know  what information you need, additionally. Logs show no errors of any kind either.

---

### Post by bashiergui on 2013-12-20
What are the rules for outgoing? Allow all out?
Look at the ufw logs to see what ports are getting blocked when you try to view the website.

---

### Post by kmccmk9 on 2013-12-20
Unfortunately I have been unable to find any kind of log for ufw even with ufw logging on high. The only thing that has worked so far has been opening all ports after 10,000

---

### Post by bashiergui on 2013-12-20
They're not in var/log/ufw?

---

### Post by kmccmk9 on 2013-12-27
Unfortunately there is nothing there.

---

