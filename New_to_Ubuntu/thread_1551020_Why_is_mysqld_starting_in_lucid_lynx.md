---
title: "Why is mysqld starting in lucid lynx?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by submute on 2010-08-11
In 10.04 server, mysqld is starting on boot. But, there is no symlink in /etc/rc2.d/ (I'm on runlevel 2) pointing to the startup script in /etc/init.d.

Any ideas why it's being started? I'd like it to stop!

---

### Post by sandyd on 2010-08-11
> **submute said:**
> In 10.04 server, mysqld is starting on boot. But, there is no symlink in /etc/rc2.d/ (I'm on runlevel 2) pointing to the startup script in /etc/init.d.

Any ideas why it's being started? I'd like it to stop!
upstart is starting it.

---

### Post by submute on 2010-08-11
> **carlee said:**
> upstart is starting it.

Is there some more proper way to turn off the automatic start rather than just removing /etc/init/mysql.conf ?

---

### Post by sandyd on 2010-08-11
> **submute said:**
> Is there some more proper way to turn off the automatic start rather than just removing /etc/init/mysql.conf ?work in progress...
[https://bugs.launchpad.net/upstart/+bug/94065](https://bugs.launchpad.net/upstart/+bug/94065)

---

