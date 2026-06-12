---
title: "Server 8.04 - MySQL Library Version Problem"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by TheMasterOfNone on 2010-07-19
Hey Everyone,

I'm new to Ubuntu and Linux in general.  I wanted to get a LAMP server up and running, my host gigenet offered Ubuntu 8.04 as their only Ubuntu solution through their cloud servers.  I managed to get everything installed, added repositories (mainly dotdeb for php).  I get this error though PHP Myadmin:

*Your PHP MySQL library version mysqlnd 5.0.7-dev - 091210 - $Revision:  294543 $ differs from your MySQL server version 5.1.48.*

After much research I have three questions:
**1. ** Is this version difference important?  If it is what is the best solution to fix it (Change OS, update repositories, download mysqlnd, etc)

**2. ** If changing the OS is a good idea would Debian 5 or CentOS 5 be a better choice for a LAMP server?  

**3.  **I tried updating PHPMyAdmin to an update to date version (currently on 2.11.3) through apt-get.  The current repositories do not have the latest version.  I understand I can download the Tar file and unzip/dpkg it but I would rather not fiddle around as I'm not familiar with the OS.  
*What is the easiest way to update PHPMyAdmin?  *

Thanks in advance for your help.

---

### Post by WRDN on 2010-07-19
Answering each question in turn:

1. The version numbers are widely different, so there will have been many changes since then (especially as it went from 5.0.x to 5.1.x).
It looks like you might be mixing repositories, with mysql coming from the hardy repositories, and phpmyadmin from others (possibly lucid?).

You should first update your package list with "sudo apt-get update", then do "sudo apt-get upgrade" to upgrade any packages to their latest version.

Check /etc/apt/sources.list to ensure there are no references to any other Ubuntu release than Hardy, and then try installing phpmyadmin again:

```
sudo apt-get install phpmyadmin
```

You can take a look at phpmyadmin and its dependencies here: [http://packages.ubuntu.com/hardy/phpmyadmin](http://packages.ubuntu.com/hardy/phpmyadmin)

2. If you want to change OS, I can't comment on Cent OS as I haven't used it, but I can say that, Debian is used for a lot of servers, as it is very stable, so it would be a good choice.
Though I've never used it personally, I would expect Cent OS to be very stable also, as it is based on Red Hat Enterprise Linux.
As for non-Linux distributions, the most common server OS is a form of BSD (UNIX) e.g. FreeBSD, NetBSD etc.


3. You should only update the software through apt-get, as many pieces of software have version dependencies, that stop at a particular time. Someone else here might be able to tell you more though.

---

### Post by TheMasterOfNone on 2010-07-19
Thanks for your reply WRDN, much appreciated.

I have determined that short of upgrading I won't be able to get the correct versions installed on my server.  Lucid is the only versions that I have up to date and upgrading only crashes the server onstartup as I assume a cloud server has some unique running properties.

On your recommendation I've switched over to Debian as it should be far less hassle than dealing with an old version of Ubuntu.  Thanks!

---

