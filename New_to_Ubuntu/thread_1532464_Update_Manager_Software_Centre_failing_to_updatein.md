---
title: "Update Manager/ Software Centre failing to update/install"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by crabclaw on 2010-07-16
I just did a clean install of Lucid Lynx and every time I try to update or install something new I get the following error message: 

Package operation failed

```
installArchives() failed: Selecting previously deselected package python-compizconfig.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 147411 files and directories currently installed.)

Unpacking python-compizconfig (from .../python-compizconfig_0.8.2-0ubuntu1_i386.deb) ...

Selecting previously deselected package compizconfig-settings-manager.

Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb) ...

Processing triggers for desktop-file-utils ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache...

Processing triggers for hicolor-icon-theme ...

Processing triggers for python-support ...

Setting up postfix (2.7.0-1) ...



Postfix configuration was not changed.  If you need to make changes, edit

/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration

values, see postconf(1).



After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.



Running newaliases

newaliases: fatal: myorigin parameter setting must not contain multiple values: jonathan s.

dpkg: error processing postfix (--configure):

 subprocess installed post-installation script returned error exit status 75

Setting up python-compizconfig (0.8.2-0ubuntu1) ...

Setting up compizconfig-settings-manager (0.8.2-0ubuntu1) ...



Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Processing triggers for python-central ...

Errors were encountered while processing:

 postfix

Setting up postfix (2.7.0-1) ...



Postfix configuration was not changed.  If you need to make changes, edit

/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration

values, see postconf(1).



After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.



Running newaliases

newaliases: fatal: myorigin parameter setting must not contain multiple values: jonathan s.

dpkg: error processing postfix (--configure):

 subprocess installed post-installation script returned error exit status 75

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place


```

Any ideas?

---

### Post by cariboo on 2010-07-16
The error code tells you what the problem is:

> newaliases: fatal: myorigin parameter setting must not contain multiple values: jonathan s.

the space between **jonathan** and **s** is the problem, either add an underscore, or remove the space.

---

### Post by crabclaw on 2010-07-17
thanks, I couldn't figure out how to do that, even though I've been using ubuntu since dapper drake, so I just did another clean install. It only took me 10-odd minutes. Lucid Lynx is astounding.

---

