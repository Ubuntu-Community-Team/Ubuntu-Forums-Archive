---
title: "Ubuntu not allow port 25 to communicate"
date: 2019-12-27
forum: Networking &amp; Wireless
---

### Post by kdmiller45 on 2019-12-27
I have installed Ubuntu 18.04 with no firewall installed, but when I use an outside port scanning site, it say port 25 is blocked and I can not telnet into it, I can ping the site.

I also have a business internet account and they do not block that port

---

### Post by TheFu on 2019-12-27
Did you start a listener on port 25/tcp?  Nothing is listening.

Also, it is best to prove the statements with commands and output rather than make a statement without any proof. Often, this would show the mistake.

---

### Post by SeijiSensei on 2019-12-27
Desktop Ubuntu doesn't come with an mail transfer agent like Postfix or sendmail installed by default. Did you install one yourself? Or did you install the server version? Did you configure the MTA to listen on an interface other than localhost? That's the default in most distributions for security reasons.

---

### Post by kdmiller45 on 2019-12-27
Appreciate the patience guys,  I did have sendmail installed, I uninstalled it and purged the settings
the attached is the result of netstat -an | grep 25 now assigned to 0.0.0.0:25 that should get to a public IP

---

