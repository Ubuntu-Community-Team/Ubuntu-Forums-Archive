---
title: "Syslog server setup"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by CharlieNixon on 2008-05-14
I want to setup my Ubuntu 8.04 box as a syslog server. First I need it to listen for "remote" syslogs. I edited **/etc/init.d/sysklogd** to accomplish this purpose. I changed

**SYSLOGD=""**
to
**SYSLOGD="-r -m0"**

Then I did a **netstat -tulp** but I don't see anything on 514. In fact, I don't see anything different from earlier at all. What gives?

By editing the file **/etc/syslog.conf** I was able to change the location of my local system's logs, but I want this system to listen for remote logs.

Any ideas?

---

### Post by Monicker on 2008-05-14
Did you reload/restart the syslog daemon?

---

### Post by CharlieNixon on 2008-05-14
yes, I did

**sudo /etc/init.d/sysklogd restart**

---

### Post by CharlieNixon on 2008-05-20
Does *anyone* have any suggestions? Everything I read online says this should be a snap.

---

