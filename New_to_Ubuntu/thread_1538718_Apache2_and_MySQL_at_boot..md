---
title: "Apache2 and MySQL at boot."
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Athunye on 2010-07-25
What is the correct way to stop apache2 and mysql from being loaded at boot time?

update-rc.d stuff doesn't work anymore. I googled for it, but nothing seems to work as expected, like commenting the line **start on** in /etc/init/mysql.conf.

The wiki should be updated, but it isn't. In my humble opinion, when the developers change the default way to do simple things like this - add or stop services from boot - they should update the wiki. 

And before anyone asks me to read the upstart (and other) man pages, please, be aware of the fact that not everyone is linux guru or developer. I'm one of these who are not (yet).

In my (humble) opinion, Ubuntu is one of the best GNU/Linux distributions available today.
One thing I'd like to have in Ubuntu, however, is a **daemons array** like in archlinux, (in /etc/rc.conf) when you just add the name of the service you want there, and it'll be initialized at boot time.
```

# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng dbus fam hal @iptables @net-profiles crond !gdm)

```I already talked too much. I'm waiting for some help. Thanks in advance.

---

### Post by Athunye on 2010-07-26
I found out that apache2 can still be removed from boot with update-rc.d -f apache2 remove (the traditional way), whereas with mysql
I had to set **start on (!0123456)** in /etc/init/mysql.conf.

What a mess!!! :(

---

