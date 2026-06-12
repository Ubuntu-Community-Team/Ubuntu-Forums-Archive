---
title: "increase ssh timeout"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by fearevilleet on 2007-01-18
hello,

My ssh sessions timeout after a few minutes. I can I increase the timeout limit for ssh?

---

### Post by scrooge_74 on 2007-01-18
Yes you can make changes to the config file in /etc in the ssh server

---

### Post by Aberrix on 2007-01-19
nm

---

### Post by cuong48d on 2008-02-15
very simple! you edit file /etc/ssh/sshd_config and set: LoginGraceTime [YourValue]
you can set whatever value you want example 3600 for 1 hour.

---

