---
title: "Postfix and port 25"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by rcaruana on 2009-03-09
I am new to linux. I have installed ubuntu server 8.0.4. I installed postfix on that server. I am able to telnet from the server, but I can't send email through port 25. I'm sure it's a simple solution, but I'm ready to pull my hair out.

---

### Post by hyper_ch on 2009-03-09
what error do you get?

check /var/log/mail.log

---

### Post by rcaruana on 2009-03-09
Mar  9 17:07:34 marconi postfix/smtpd[13553]: connect from unknown[192.168.1.128]
Mar  9 17:07:34 marconi postfix/smtpd[13553]: fatal: bad net/mask pattern: "192.168.1.0/254"
Mar  9 17:07:35 marconi postfix/master[5643]: warning: process /usr/lib/postfix/smtpd pid 13553 exit status 1
Mar  9 17:07:35 marconi postfix/master[5643]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Mar  9 17:08:58 marconi postfix/smtpd[13879]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Mar  9 17:09:03 marconi postfix/smtpd[13879]: warning: 192.168.1.128: hostname rhonda-laptop.gmdc.local verification failed: Name or service not known
Mar  9 17:09:03 marconi postfix/smtpd[13879]: connect from unknown[192.168.1.128]
Mar  9 17:09:03 marconi postfix/smtpd[13879]: fatal: bad net/mask pattern: "192.168.1.0/254"
Mar  9 17:09:04 marconi postfix/master[5643]: warning: process /usr/lib/postfix/smtpd pid 13879 exit status 1
Mar  9 17:09:04 marconi postfix/master[5643]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

The 192.168.1.0/254 is my internal network

Thanks,

---

### Post by hyper_ch on 2009-03-09
how did you install it?

---

### Post by rcaruana on 2009-03-10
apt-get install postfix

---

### Post by brian_p on 2009-03-10
> **rcaruana said:**
> 

Mar  9 17:07:34 marconi postfix/smtpd[13553]: fatal: bad net/mask pattern: "192.168.1.0/254"

The 192.168.1.0/254 is my internal network

I think the information you have given postfix is incorrect. Are you sure 192.168.1.0/254 is right? Might it not be 192.168.1.0/24?
Or go with the postfix defaults if it offers any.

---

