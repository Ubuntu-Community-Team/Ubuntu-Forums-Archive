---
title: "Curious mail problem"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by dmj99 on 2008-04-05
After a bit of fiddling, I managed to get Alpine, fetchmail, procmail and postfix working so I can read and send email.  Everything seems to be working well (amazingly enough).  However, I notice I get this curious email every twenty minutes:


```
Date: Sat,  5 Apr 2008 15:40:01 -0700 (PDT)
From: Cron Daemon <root@earthlink.net>
To: root@earthlink.net
Subject: Cron <smmsp@ubuntu> test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp

/usr/share/sendmail/sendmail: 1226: /usr/sbin/sendmail-msp: not found
```

Does anyone know what this is?

Thanks for your interest,

DeeJay

---

### Post by superprash2003 on 2008-04-06
this looks like a cron task which you have setup..go to terminal and type crontab -e to find out

---

### Post by dmj99 on 2008-04-06
When I try crontab -e I get the following one line:

```
# m h  dom mon dow   command
```

Not sure that it tells me much, but thanks for your input.  

DeeJay

---

### Post by dmj99 on 2008-04-07
Problem solved:  edited the file  /etc/cron.d/sendmail and commented out the entry scheduled for 20 minutes.

---

