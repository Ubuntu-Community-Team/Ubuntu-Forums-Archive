---
title: "Server crash daily, what logs to check"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by dcollier on 2009-07-16
Hello, I have a ubuntu 2.6.24-23-virtual install on virtual server 2005.  The server will lock up while working on any task at any moment.  What logs should I look for and what whit in the logs should i be looking for?  any help would be helpful!

---

### Post by Elep.Repu on 2009-07-16
/var/crash

---

### Post by dcollier on 2009-07-18
ok /var/crash?  no such dir or file

---

### Post by cariboo on 2009-07-18
All the log files are located in /var, I would suggest you check, daemon.log, syslog, messages and kernel.log

---

