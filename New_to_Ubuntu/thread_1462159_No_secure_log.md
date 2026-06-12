---
title: "No secure log?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by HarrisonNapper on 2010-04-25
So I have a widget that does "tail -f /var/log/messages" and I was plotting to have another one with /var/log/secure.

Much to my surprise, /var/log/secure is not there. I don't know if there's another file for this or if there's no file for it, just wanted to see what you all know.

Thanks in advance for any insight. :)

Edit: for those of you looking for this, check man syslog for more info. When I checked in /etc/rsyslog.d I saw the 50-default.conf file and that had all of the info that would normally have been in syslog.conf, /var/log/auth.log or /var/log/user.log

Cheers.

---

### Post by QLee on 2010-04-25
[QUOTE=HarrisonNapper]So I have a widget that does "tail -f /var/log/messages" and I was plotting to have another one with /var/log/secure.

Much to my surprise, /var/log/secure is not there. I don't know if there's another file for this or if there's no file for it, just wanted to see what you all know.

Thanks in advance for any insight. :)[/QUOTE]

Perhaps you are more familiar with Red Hat derived distros where there is a "secure" log.

Judging by the phrasing of your edit, you don't need help deciding which logs you have to parse to obtain the data you desire from your custom launcher.

---

