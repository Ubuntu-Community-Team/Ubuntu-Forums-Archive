---
title: "Adding MySQL to start on bootup"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by FlintyV on 2010-09-15
Hello,

I've a little Ubuntu server and was wondering how I add it to start when I boot up the server as I get errors on Wordpress as there DB isn't running.

NOTE: I only have SSH access, no GUI.

Cheers,
Scott

---

### Post by spjackson on 2010-09-15
Do you have the package mysql-server installed? Installing the package should configure it to start on boot.

Do you have these files?

/usr/sbin/mysqld
/etc/init.d/mysql
/etc/init/mysql.conf

Is there anything in /var/log/... that indicates that it failed to start on boot? Which version of Ubuntu Server is this?

---

### Post by FlintyV on 2010-09-15
Yea it's installed and there is a few errors but I think that's because it lost power a couple of times. 

A few things like "100913 16:54:35 [ERROR] /usr/sbin/mysqld: Table './temp/flux_posts' is marked as crashed and should be repaired
"

But when the server comes online I have to manually start MySQL with "sudo service mysql start" but Apache starts just fine on its own.

---

### Post by spjackson on 2010-09-16
> **FlintyV said:**
> Yea it's installed and there is a few errors but I think that's because it lost power a couple of times. 

A few things like "100913 16:54:35 [ERROR] /usr/sbin/mysqld: Table './temp/flux_posts' is marked as crashed and should be repaired
"

But when the server comes online I have to manually start MySQL with "sudo service mysql start" but Apache starts just fine on its own.

Does that error message you quoted above correspond to a boot time?

"sudo service mysql start" is effectively what is supposed to happen at boot time. It is a puzzle that it fails at boot time but succeeds subsequently.

You didn't indicate whether you have those files in /etc/init . If I were you I would be trying to find out whether it is trying to start at boot time and failing, or whether it isn't trying to start. I would also repair any tables for which errors are reported.

---

