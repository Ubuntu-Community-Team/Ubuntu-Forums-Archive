---
title: "ssh installation problem"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by archie_me on 2010-07-24
Hi,i recently downloaded and installed ubuntu 10.04 LTS on my desktop pc.After that,i went to the network manager and established a wired connection after providing the necessary info like ip address,dns server etc..The wired connection is active.
My internet is not working at all.
According to my ISP,the ssh is diabled on my ubuntu system.So to rectify it,i wrote the following command at the terminal:
 
1) $:**sudo -i**
 
o/p:password:
 
2)#:**apt-get update**
 
 
err:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com") conncn timed out
err:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/") conncn timed out
err:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/") conncn timed out
err:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/") conncn timed out
err:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/") conncn timed out
err:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/") conncn timed outerr:Unable to connect to [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/") conncn timed out
 
3)**apt-get install ssh**
 
gives the same above error.
 
 
 
 
Could u please provide a solution for the same??I need it quite urgently for a project.

---

### Post by bodhi.zazen on 2010-07-24
The title of your thread is misleading, IMO, as it looks as if the problem is not with ssh but rather with your network connection.

Can you ping google ?

```
 ping -c 4 google.com
```How about ubuntu ?

```
ping -c 4 [www.in.archive.ubuntu.com]("http://www.in.archive.ubuntu.com/")
```

Are you running a firewall ?

Do you need to use a proxy server ?

---

