---
title: "login script"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by ant2ne on 2008-12-07
Where do I put a script that will be executed at log in, regardless of the user. I want it to execute even on users who may not even exist on the system yet.

---

### Post by lovelyvik293 on 2008-12-07
Put anyware user can not access and add it in the cron entry.

---

### Post by ant2ne on 2008-12-08
is there an at login cron?

---

### Post by Mattventura on 2008-12-08
You can put it in /etc/profile and it should execute at any successful login.

---

