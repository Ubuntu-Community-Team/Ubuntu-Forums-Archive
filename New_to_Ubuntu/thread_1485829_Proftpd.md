---
title: "Proftpd"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by macmike on 2010-05-17
I installed Proftpd. How do I start the program so I can configure it? Also I am having trouble getting Virtual Hosting to go without giving me warnings. Also can I install some sort of GUI file to work with Ubuntu 10.04 Server installation? Need a lot of help!

Mike Hughes

---

### Post by hannaman on 2010-05-17
Proftpd can be setup on install to either run from inetd or standalone.  If you chose standalone on install, you can start and stop proftp by typing one of the following:
```
sudo /etc/init.d/proftpd start
sudo /etc/init.d/proftpd stop
```
If you chose inetd, you shouldn't have to do anything to start it.

The configuration files are located in /etc/proftpd.

To test if ftp is working, type the following on the server where ftp is installed:
```
ftp 0
```
If you can log in, then the ftp server is working.  If you cannot log in from another machine, you might have to configure port forwarding on your router to forward ports 20 and 21 to your ftp server.

---

