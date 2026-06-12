---
title: "Apache2 Startup Script Missing?"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by f@rfromhome on 2010-01-16
Whats up everybody?  

I'm very new to linux in general and had a question.  I'm trying to install wordpress on my server (Ubuntu Server 9.10) and I'm having some issues.  I installed Apache, Php, phpmyadmin and all of the stuff that it said it needed.  I messed up the install and attempted to uninstall those programs too.  When I reinstall apache, the apache2 start up script is not listed in init.d 

I've tried:

sudo dpkg -P --force-depends package
sudo aptitude install package

with no luck.  I found that on another forum but it didn't do anything.  

Any suggestions on how to get Apache working again?  

Thanks,

-Matt

---

### Post by cariboo on 2010-01-17
You can repair the problem a couple of ways, you can extract the .deb located in /var/cache/apt/archves using file roller. or completely remove apache using:

```
sudo apt-get purge apache2
```

The above command complete removes apache2 and all of it's configuration files. using the -remove option only removes the program. Make sure apache2 is stopped before removing it. or you won't be able to uninstall it.

---

### Post by f@rfromhome on 2010-01-17
Thanks for the reply.  How can I stop the apache service if the apache2 file is not in the init.d dir?  

Here is my output when I tried to purge and then reinstall.  

root@*******:/etc/init.d# apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 40 not upgraded.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 52322 files and directories currently installed.)
Removing apache2 ...

root@*******:/etc/init.d# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
Need to get 0B/1,424B of archives.
After this operation, 36.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 52319 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.12-1ubuntu2.1_all.deb) ...
Setting up apache2 (2.2.12-1ubuntu2.1) ...

When I ls in init.d, I still don't see any apache2 file...

I'm sorry I'm such a newb at ubuntu and I appreciate all of the help.

Thanks,

-Matt

---

