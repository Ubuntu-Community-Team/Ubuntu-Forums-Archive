---
title: "postfix-mysql can't connect to mysql"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by yourabi on 2006-09-05
Hello,

I've install postfix, postfix-mysql, mysql-server, mysql-common, and mysql-client all from apt (ubuntu server i386). I can indeed connect to mysql with a simple mysql -u root. However, after enabling the mysql maps in postfix, I see the following in /var/log/mail.log 

Sep  4 21:36:11 hercules postfix/cleanup[4486]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

[ I can see the socket ]
ls -l /var/run/mysqld/mysqld.sock
srwxrwxrwx 1 mysql mysql 0 2006-09-04 21:24 /var/run/mysqld/mysqld.sock

I don't think it's a permissions thing, but I'm out of ideas.

The versions of everything are vanilla from apt, so mysql-5.0.22, postfix-2.2.1...etc

Thanks for any pointers/ideas/solutions.


Cheers!

---

### Post by yourabi on 2006-09-05
Hate to repsond to my own post, but I've foudn the solution. 

In the mysql map files, the host line was set to localhost, (ping localhost returns 127.0.0.1), but changing it to 127.0.0.1 resolved the issue. I know for a fact that localhost works on FreeBSD/postfix, so it must be a postfix on linux thing... I'm just not sure what?

hosts = 127.0.0.1


I'm still interested if anyone has any insights as to why localhost wouldn't work?

---

### Post by Uluen on 2006-09-05
Well it's good you're posting a solution to your problem so others can find it later, thanks.

It sounds like a DNS issue, doesn't it? What does your */etc/resolv.conf* and *hosts* look like?

---

### Post by sputicus on 2006-10-24
The problem, is that that (most of) the postfix applications are running in a chroot environment. This means they see nothing other than what is under /var/spool/postfix as their running environment. In the chrooted environment there is no /var/run/mysqld/mysqld.sock, so the postfix utils fail.

You could perform hard link from the acutal /var/run/mysqld/mysqld.sock to the identical place in the chroot environment, but you would have to remake this link every time mysqld is restarted. It is simpler, and almost as efficient, to just have postfix use TCP to communicate with the local mysql server. Setting the hosts to 127.0.0.1 makes this happen.

I struggled with this for about 12 hours before discovering the ubuntu PostfixCompleteVirtualMailSystemHowto did not cover this problem. I plan to update the howto as soon as I can.

---

### Post by wladyx on 2008-02-25
You are a life saver!! Just migrated from FBSD to Ubuntu server and i was desperate :)

---

