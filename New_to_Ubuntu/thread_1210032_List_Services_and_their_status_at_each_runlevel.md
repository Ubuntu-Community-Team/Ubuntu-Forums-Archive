---
title: "List Services and their status at each runlevel"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Valsodar on 2009-07-10
Sorry for asking this simple question, but I just can't find it using google.

There is a command (CLI) that shows the run status of each service on your system. Does anyone remember what that command was?

---

### Post by ddnev45 on 2009-07-11
sysv-rc-conf comes to mind; I don't think it's installed by default.

---

### Post by earthpigg on 2009-07-11
i do not completely understand how all of this stuff comes together, but while reading about standard linux runlevels a while back while playing with arch, i came across this:

[http://www.linux.com/archive/feature/125977](http://www.linux.com/archive/feature/125977)
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

my noobish understanding is that the good old fashoned runlevel paradigm is being depreciated in ubuntu, and a few other distros as well.

---

### Post by earthpigg on 2009-07-11
wait, there it is:

ls -C /etc/rc*.d|more

hrmm....

*exploring*

---

### Post by Dougie187 on 2009-07-11
```
service --status-all
```

That tells you all the services, but not their runlevels.

---

### Post by MK++ on 2011-02-20
```
apt-get install chkconfig
chkconfig --list service_name
```

---

