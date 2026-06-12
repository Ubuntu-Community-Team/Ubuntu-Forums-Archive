---
title: "problem starting daemon using ssh"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by techno.naru on 2008-08-01
hello friends

i am trying to start the drqueue-slave daemon using ssh
but the problem is that the command
ssh [email]root@10.0.1.xxx[/email] /etc/init.d/drqueue-slave restart

the command executes without error but the daemon does not start

but if i manually go to the machine using ssh and then execute the command the daemon starts....

what shall i do...

---

### Post by opscure on 2008-08-01
ssh server 'program </dev/null >/dev/null 2>&1 &'

---

