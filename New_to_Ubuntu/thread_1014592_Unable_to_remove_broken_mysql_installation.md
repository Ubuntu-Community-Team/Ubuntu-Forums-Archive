---
title: "Unable to remove broken mysql installation"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mafiacooper on 2008-12-18
Hi all,

I'm rather new to Ubuntu, having been persuaded to use it only yesterday - I'm used to CentOS and the delights of Yum for managing software installs.

Last night I encountered some rather odd problems with remote connections to MySQL so I decided to reinstall it. However, I kept getting errors about a missing debian-system-maint in the mysql.user table, so I attempted a "manual uninstall" and, in the process I'm afraid that the /var/lib/mysql directory was lost (my bad).

I now cannot uninstall MySQL using the usual:
```

sudo apt-get autoremove --purge mysql-server mysql-server-5.0

```
and I receive the following output:
```

Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                          [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--purge):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                          [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                          [ OK ]
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
This is clearly because I have lost all of the tables by deleting the mysql directory :(

Can anyone walk me through the process of getting this fixed so that I am able to reinstall?

Thanks!

---

### Post by gettinoriginal on 2008-12-18
I believe MySQL is in synaptic package manager, you could just reinstall it from there.

---

### Post by HPVOHHR on 2009-02-11
I am having this exact same problem.  Deleted all the default users in MySQL and now I can't even purge/remove it.  The scripts to remove try to use the user that doesn't exist anymore!

This is a server install, not desktop.

Has there been any resolution to this?

Thanks.

---

### Post by HPVOHHR on 2009-02-11
Ok, I managed to remove it like this:

```
sudo pkill -9 mysql
sudo dpkg-reconfigure mysql-server-5.0
sudo apt-get --purge remove mysql-server-5.0
```

Then re-installed:

```
sudo apt-get install mysql-server-5.0
```


I have no idea why this worked... I'd tried just the purge/remove and it wouldn't work because of errors due to the user being deleted.

For some reason, killing the process, then reconfiguring, then purge/remove... worked.

Good luck!

---

