---
title: "Ubuntu refuses connection on a network"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by rubionis on 2007-08-29
Hi,

I'm relatively new to Ubuntu and I have installed it as a virtual machine. I have established a network of virtual machines: Fedora, PC-BSD and Ubuntu.
I can connect between Fedora and PC-BSD (ssh), but never been able to add Ubuntu in the network.
Anytime I try to connect to, it refuses connections (refused on port 22, ssh). BTW I can ping Ubuntu, and it can ping the other machines too, so it's not a network issue.
I've tried for days and days, and many things. I configured the /etc/hosts, hosts.allow, hosts.deny,.. installed Firestarter and it's temporarily disabled, but no results!!!:confused:

As a matter of fact the first time (long ago) I was able to connect to Ubuntu, but that was IT...!! At the time the reason was the IP of the other machine was being added automatically in the hosts.deny file. I removed that IP from the file, but the problem persisted.Since then I've never been able to connect to Ubuntu.
I'm totally lost at this point...!

Any help is appreciated
 
Thanks

---

### Post by noob12 on 2007-08-29
Can you post the output of these

```

ps -ef | grep sshd

netstat -tnl

```

---

### Post by rubionis on 2007-08-29
Thanks for the quick reply.

*ps -ef | grep sshd*
mirix    24497  9276  0 13:13 pts/0    00:00:00 grep sshd

*netstat -tnl*
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:975             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3922          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2747          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN

If this info is needed, I'm using Ubuntu 6.06.
uname -a
Linux ubuntu 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

---

### Post by noob12 on 2007-08-30
It appears from both of these that you are not actually running the ssh service.  That's why you can't connect via ssh.  It is not installed by default.

Install it.
```

sudo aptitude install openssh-server

```

I believe it is started automatically when you do install it, but this will make sure (just this time)
```

sudo /etc/init.d/ssh restart

```

It will be started automatically on boot.  I expect this will address your issue.  

If your problem still persists after this, please again collect the output of the same two commands I asked for in posting #2 on this thread and post it again; we expect different output at that point, and it will provide useful info for diagnosis.

---

### Post by rubionis on 2007-08-30
:popcorn: PROBLEM SOLVED :popcorn:

ps -ef |grep sshd

root      4793     1    0  09:00  ?             00:00:00 /usr/sbin/sshd
mirix     5604  4589  0  09:11  pts/0       00:00:00 grep sshd

I'm able to fully connect to Ubuntu. I'm still surprised that ssh wasn't installed by default. Never suspected that.

Thanks again noob12. Very helpful and right on point. =D>

---

