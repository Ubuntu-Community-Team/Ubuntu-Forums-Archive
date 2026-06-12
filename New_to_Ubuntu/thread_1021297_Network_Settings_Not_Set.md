---
title: "Network Settings Not Set"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by navidz on 2008-12-25
Hello everyone,
I use Ubuntu 8.10 and Created new "Wired connection 1".
When restart computer.  I must select connection manually to "Wired connection 1".
Please Help me for automatically select this connection.

Thanks, Navid :KS

[COLOR="Red"]Sorry for poor English[/COLOR]

---

### Post by zvacet on 2008-12-26
When you connect to the net try run this command in terminal

```
sudo /etc/init.d/networking restart
```

---

