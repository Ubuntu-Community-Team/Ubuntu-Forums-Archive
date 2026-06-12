---
title: "Reinstalling cron"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by jsdegard on 2009-03-16
Hello 

I was advised to purge and reinstall cron because I accidentally deleted the /usr/bin/crontab file which was needed to run crontab commands i.e. view my cron jobs in webmin.  It won't let me do this, though.  I guess because of dependencies (because my original php had to be recompiled to include mssql functions).  How can I 'specify a solution', as it says?  Here is what happens when I try to uninstall cron:

jsdegard@lambda:~$ sudo apt-get remove --purge cron
[sudo] password for jsdegard:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
libapache2-mod-php5: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubun
tu5.2 is to be installed
logrotate: Depends: cron or
anacron but it is not going to be installed or
fcron but it is not going to be installed
php5-dev: Depends: php5-common (>= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is t
o be installed
php5-mysql: Depends: php5-common (= 5.2.4-2ubuntu5.4) but 5.2.4-2ubuntu5.2 is
to be installed
ubuntu-standard: Depends: cron
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s
olution).

Is there another way to force the removal, like a way to ignore the dependencies? The only other thing I can think of is to install ubuntu 8.04 on another partition and copy the file from there somehow (yuk).

Thanks

Jeremy

---

### Post by dje on 2009-03-16
first i would suggest you boot up a live cd and copy the file from there (no need to install, just copy straight from the live cd root /)

if that doesn't work you may wish to try this ([COLOR="Red"]I have not tested this, it may or may not hose your system, use at your own risk![/COLOR])
```
sudo apt-get install --reinstall cron
```

dje

---

### Post by jsdegard on 2009-03-22
Thanks guys for helping the new guy.  I took Ubuntu's suggestion to run 'apt-get -f install' which updated my dependencies for php where they needed to be, uninstalled cron, reinstalled cron, and reinstalled my compiled flavor of php with mssql.  Viola!  I have found this network to be very helpful.

Thanks again 

Jeremy

---

