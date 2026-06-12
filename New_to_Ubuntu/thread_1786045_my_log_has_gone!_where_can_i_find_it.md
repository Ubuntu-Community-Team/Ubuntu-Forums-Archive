---
title: "my log has gone! where can i find it?"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by werty2010 on 2011-06-19
i booted up my laptop today and for some reason i checked the log file viewer and everything was blank!?

could someone tell me why this is happening and where can i check the previous logs?

---

### Post by Rubi1200 on 2011-06-19
There is a good chance the logs were probably rotated, meaning cleaned up.

Look in /var/log and you should see a bunch of files with the following format:

e.g.>  auth.log.2.gzNew entries will be created as events are logged.

Hope this answers the question.

You can check the settings for rotation of most logs by issuing this command:

```
 cat /etc/logrotate.d/rsyslog
```

---

