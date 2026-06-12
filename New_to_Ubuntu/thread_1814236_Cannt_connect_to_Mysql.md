---
title: "Cannt connect to Mysql"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by inno_k on 2011-07-29
Why do i get th following error after restarting the mailserver?
The mail server works very well
Is it normal??

Either it first connects then gives:confused: tht error msg

Jul 29 13:51:38 mail dovecot: last message repeated 2 times
Jul 29 13:51:38 mail dovecot: pop3-login: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jul 29 13:51:38 mail dovecot: auth-worker(default): Killed with signal 15 (by pid=1 uid=0 code=kill)
Jul 29 13:51:38 mail dovecot: auth(default): Killed with signal 15 (by pid=1 uid=0 code=kill)
Jul 29 13:51:38 mail dovecot: dovecot: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jul 29 13:51:38 mail dovecot: Dovecot v1.2.15 starting up (core dumps disabled)
Jul 29 13:51:38 mail dovecot: auth-worker(default): mysql: Connected to 127.0.0.1 (mail)
Jul 29 13:52:46 mail dovecot: auth-worker(default): mysql: Connect failed to 127.0.0.1 (mail): Can't connect to MySQL server on '127.0.0.1' (111) - waiting for 1 seconds before retry
Jul 29 13:52:47 mail postfix/master[793]: daemon started -- version 2.8.2, configuration /etc/postfix


But if i restart Dovecot service it connects??

---

### Post by kimda on 2011-07-29
Have a look at this thread it may help you to get mysql working.  

[http://ubuntuforums.org/showthread.php?t=1732625](http://ubuntuforums.org/showthread.php?t=1732625)

---

