---
title: "error gettng while installing mysql 5"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by prasobh4u on 2010-12-16
Hi everyone, 
I am new with linux.

i was trying to install mysql 5 in redhat.. but i am getting an error like this :(

[COLOR=Red][root@localhost Mysql5]# rpm -iUvh MySQL-server-community-5.1.36-0.rhel5.i386.rpm

error: Failed dependencies:
        libmysqlclient.so.15 is needed by (installed) dovecot-1.0.7-7.el5.i386
        libmysqlclient.so.15(libmysqlclient_15) is needed by (installed) dovecot-1.0.7-7.el5.i386
[/COLOR]
can any one help me ?

---

### Post by Wobblybob on 2010-12-18
I think you would be better asking this on a Red hat forum as Ubuntu uses .deb package management. That said the error message seems to be telling you to add the dovecot-1.0.7-7.el5.i386 package before you try installing the mysql package.

---

