---
title: "/etc/amavis/amavisd.conf doesn't exist"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by gschoppe on 2007-09-13
exactly what i said...

I try th run amavis-new and I get the message:

```

gschoppe@Hippocampus:~$ sudo  /etc/init.d/amavis restart
Stopping amavisd: (not running).
Starting amavisd:   The value of variable $myhostname is "Hippocampus", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in amavisd.conf, or fix what uname(3) provides as a host's network name!
(failed).


```

so I gksudo gedit /etc/amavis/amavisd.conf

BAM! - new file.

why? ... alternatively, how do i fix this issue?

---

### Post by mootpoint on 2007-09-14
try editing /etc/amavis/conf.d/50-user. amavis switched to a multiple-file configuration setup a while back; maybe that error message never got the news.

mootpoint

---

### Post by gschoppe on 2007-09-15
thanks, that fixed the issue... i think.

---

