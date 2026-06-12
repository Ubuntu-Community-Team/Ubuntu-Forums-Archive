---
title: "Problems with mysql"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by thorbs on 2010-07-31
I have earlier installed mysql. It is the mysql-server 5.1 5.1.4.1 - 3ubuntu12.1. I am being told that it is in a very bad state. 

instead i am told I should have installed. mysql-server 5.1 5.1.4.1 - 3ubuntu12.3 - i386deb 


Ubuntu is trying to perform this action by itself but is not able to. I have tried all the different ways I can find described, including starting up in recovery mode.


Can anybody help me how to do this?

---

### Post by cariboo on 2010-07-31
The package you are looking for is in the lucid repositories, if you are having a problem installing the deb, it can be downloaded from [here]("http://packages.ubuntu.com/lucid/mysql-server-5.1").

---

### Post by phaed on 2010-08-02
I'm having a similar problem.

apt just hangs when trying to upgrade MySQL:

> The following packages will be upgraded:
  mysql-server-5.1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7,008kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 220414 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12.3 (using .../mysql-server-5.1_5.1.41-3ubuntu12.6_i386.deb) ...

And that's where it hangs.  I have to kill it manually.

If I try to remove the package, it says:

> The following packages will be REMOVED:
  mysql-server-5.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 15.0MB disk space will be freed.
Do you want to continue [Y/n]? 
dpkg: error processing mysql-server-5.1 (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)


Of course, when I try to reinstall it, it just hangs again.

I also get:

> $ sudo dpkg --configure -a
dpkg: error processing mysql-server-5.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 mysql-server-5.1

---

### Post by shanedj on 2010-08-05
I too am having this issue. I left the upgrade running overnight and its still "preparing to replace mysql-server-5.1 etc"

---

### Post by phaed on 2010-08-05
Yep, that's what happened to me.  It started with unattended-upgrades at 6 am and was still hanging at 2 pm.

---

### Post by thorbs on 2010-08-06
Hi I found the solution in the end of this thread

[http://ubuntuforums.org/showthread.php?t=1488763&highlight=mysql+reinstall&page=3](http://ubuntuforums.org/showthread.php?t=1488763&highlight=mysql+reinstall&page=3)


If you for some reason like me is not able to identify the PID there is help here:

[http://ubuntuforums.org/showthread.php?t=1545816](http://ubuntuforums.org/showthread.php?t=1545816)

---

### Post by phaed on 2010-08-06
Thanks, although I already backed up my data and reinstalled Ubuntu.  It's unfotunate, but I need MySQL for WebDAV, and I need WebDAV to backup and sync my Zotero files, and it didn't look like a solution was forthcoming. :-)

However, if it happens again, I'll keep that in my mind.  For now, I have turned off unattended-upgrades.

---

### Post by phaed on 2010-08-09
Now the same thing happened again but with libldap-2.4-2.  It just hangs.  Frustrating.  I'm switching to Debian server :-)

---

### Post by phaed on 2010-08-10
Ok, so I downloaded the libldap deb package and installed it manually and that worked.  It's possible that these errors are resulting from deb files that get corrupted during transfer.  Might want to download manually if it happens again.

---

