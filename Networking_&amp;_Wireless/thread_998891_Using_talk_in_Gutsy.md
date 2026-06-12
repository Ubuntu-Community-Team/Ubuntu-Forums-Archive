---
title: "Using talk in Gutsy?"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by LebLinux on 2008-12-01
Hello, I've installed inetuils and I insatalled talk and talkd but whenever I type: talk <user> I get Error on read from talk daemon: Connection refused. Press any key...

Any ideas please thank you!

---

### Post by puppywhacker on 2008-12-01
Hi,

talk is a client which needs to connect to a daemon (server) on port 517. You can install talkd to make it work

```

sudo apt-get install talkd

```

---

### Post by LebLinux on 2008-12-02
Its not working still displaying the talk error I pasted above...

However here is what I have:

ii  inetutils-talkd                            2:1.5.dfsg.1-4  
ii  talk                                       0.17-13

in /etc/inetd.conf :

#<off># talk    stream  tcp     nowait  root    /usr/sbin/talkd talkd

only this line.

I have /etc/init.d/inetutils-inetd started..

What could be wrong??

---

### Post by puppywhacker on 2008-12-02
talkd did not start with inetutils-inetd. The configuration line starts with a # which means it is commented out.

remove the #<off># and restart the inet daemon

you can check whereif the talkd is running by grepping through the netstat printout or running an lsof (which is less likely to be installed)

netstat -na | grep LISTEN | grep 517
lsof -i:517

---

### Post by LebLinux on 2008-12-02
I removed the #<off># from in /etc/inetd.conf

leblinux@leblinux:~$ sudo /etc/init.d/inetutils-inetd restart
 * Restarting internet superserver inetd                                 [ OK ] 
leblinux@leblinux:~$ netstat -na | grep LISTEN | grep 517
leblinux@leblinux:~$ lsof -i:517

still nothing...

---

