---
title: "managing events and logs"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by sergiofm on 2013-10-03
Hi,

I wanted a centralized management of logs. I want to store all my logs (apache, mysql, windows server logs, etc) and query them via web server. Any ideas?

Tanks,
Sérgio Marques

---

### Post by TheFu on 2013-10-03
Cacti.

---

### Post by sergiofm on 2013-10-03
Hi,

I want to install it on Ubuntu and i want to read all tipe of logs (linux logs, windows logs). Cacti can read windows security logs?

Thanks,
Sérgio Marques

---

### Post by houstonbofh on 2013-10-03
Set up a syslog server to centralize the logs.  As for sharing them, you could just link /var/www/logs to /var/log after installing apache to the syslog server.

---

### Post by sergiofm on 2013-10-03
Sorry, I am newbie in this things. Do you knoe any toturial?

Thanks,
Sérgio Marques

---

### Post by sergiofm on 2013-11-15
Anyone???? Pleaseeeeeeee

Thanks,
Sérgio Marques

---

### Post by houstonbofh on 2013-11-15
Here is a good start on syslog...
[http://askubuntu.com/questions/148375/rsyslog-filter-for-logging-router-events-syslog-server](http://askubuntu.com/questions/148375/rsyslog-filter-for-logging-router-events-syslog-server)

Here is some information on symbolic links...
[http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link](http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link)

As for setting up Apache, there are lots of them

---

### Post by sergiofm on 2013-11-20
thank you very much

---

