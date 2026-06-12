---
title: "MySQL not running in a 10.4 LAMP server (desktop ed.)"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by andyzammy on 2010-07-06
Hi all,

I'm trying to get a LAMP server up and running, and i'm struggling to configure MySQL. I'm using webmin to do it, but i get the following error:
> MySQL is not running on your system - database list could not be retrieved.
Pressing the button or inputting the following command does nothing:
```
/etc/init.d/mysql start >/dev/null 2>&1 &
```

I'm following a guide written by a friend, but it was written for 8.04 if this info is any help.

Thanks for your time,
If you need me to give any more info just ask and i'll post it up.
Zammy

---

### Post by cariboo on 2010-07-06
Try running:

```
dpkg-reconfigure mysql-server-5.1
```

in a terminal, make sure to set a root password. Once mysql is setup, it should start automagically.

---

### Post by andyzammy on 2010-07-08
> **cariboo907 said:**
> Try running:

```
dpkg-reconfigure mysql-server-5.1
```

in a terminal, make sure to set a root password. Once mysql is setup, it should start automagically.

Thanks very much! worked. I did exactly the same thing at initial install though, so not sure why it messed up :S

---

