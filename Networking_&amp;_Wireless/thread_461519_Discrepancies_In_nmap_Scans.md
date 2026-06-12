---
title: "Discrepancies In nmap Scans"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by scottfinman on 2007-06-01
The following pertains to a server running Ubuntu Feisty.

In particular, when I run an nmap port scan on the server *from* the server, I get the following (which is what I expect to see):

> 
>root@coeus:/var/www/apache2-default# nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-01 19:38 EDT
Interesting ports on scottfinman.com (127.0.0.1):
Not shown: 1690 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
443/tcp  open  https
587/tcp  open  submission
3306/tcp open  mysql


However, when I run the same scan on the server from my home machine, I get the following (which is not what I expect to see):

> 
>scott@sfdesktop-ubuntu:~$ nmap scottfinman.com

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-01 19:38 EDT
Interesting ports on 64.79.219.245:
Not shown: 1687 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
443/tcp  open     https
623/tcp  filtered unknown
664/tcp  filtered unknown
3306/tcp open     mysql
6667/tcp filtered irc
6668/tcp filtered irc
7000/tcp filtered afs3-fileserver


I was hoping to better understand what's happening with the so-called 'filtered' ports. As well, ports 25 and 587 are not showing up in the latter scan. I came across some tentative discussion that the filtered ports might be something coming up due to my ISP, rather than anything on the server side? 

There is a similar relevant inquiry posted at:
[http://osdir.com/ml/linux.admin/2003-03/msg00159.html](http://osdir.com/ml/linux.admin/2003-03/msg00159.html)
...no clear explanation in response, however.

Any insight would be much appreciated!

---

### Post by wob08 on 2008-04-03
I have encountered the same problem. The vmware server is responsible for it: if you shut it down, the nmap scans does not show those two ports.

Regards,
András

---

