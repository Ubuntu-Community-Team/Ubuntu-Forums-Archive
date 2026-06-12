---
title: "Fail2ban failregex question"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by mistypotato on 2010-12-29
Hi,

**In this line....**

12.345.67.89 - - [29/Dec/2010:05:08:43 -0500] "POST /login.php?do=login HTTP/1.1" 200 8918 "http://www.mydomain.com/login.php?do=login" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"

**I'm trying to set up a fail2ban filter rule to catch this section.....**

POST /login.php?do=login


but nothing I try is working
Here is what I currently have

failregex = [[]client <HOST>[]] .*("POST /login\.php\?do=login").*

Can anyone see why this isn't working?

thx

---

