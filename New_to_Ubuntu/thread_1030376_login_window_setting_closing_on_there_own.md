---
title: "login window setting closing on there own"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by baxter1980 on 2009-01-04
when I go to my login window settings the application opens and closes after it loads. I want to fix this problem so I can change my GDMtheme

---

### Post by cmnorton on 2009-01-08
There may be some tell-tail information in your logs in /var/log. Start with syslog and messages. You do not need to post logs here. Just see if there are any errors in these logs right after this happens:

sudo tail /var/log/messages
sudo tail /var/log/syslog

Are you being prompted for an administrative password and are you entering it if prompted?

---

