---
title: "Winbind and logrotate error question"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by dpm on 2006-12-03
I've got winbind working on two computers, the hostnames of which are correctly resolved when I e.g. ping by host name.

However, I've got a small annoyance with winbind.

Every day I'm getting an e-mail from anacron on /var/mail telling me the following:

```
/etc/cron.daily/logrotate:
kill: 2: No such process

error: error running postrotate script for /var/log/samba/log.winbindd
run-parts: /etc/cron.daily/logrotate exited with return code 1 
```Here's the winbind logrotate configuration in /etc/logrotate.d:

```
/var/log/samba/log.winbindd {
    weekly
    missingok
    rotate 7
    postrotate
    [ -f /var/run/samba/winbindd.pid ] && kill -HUP `cat /var/run/samba/winbindd.pid`
    endscript
    compress
    notifempty
}
```I believe I'm getting the error when **kill -HUP `cat /var/run/samba/winbindd.pid`**is being executed, since there is no such a process ID. What makes me think this (and what really confuses me), is that when I do a 'ps -ef winbindd', I get no such process listed, although winbindd must be somehow running if hostname resolution is working.

Any comments will be greatly appreciated, I'm really lost right now.

Thanks.

---

### Post by dpm on 2006-12-10
oh well... 

shameless bump.

---

