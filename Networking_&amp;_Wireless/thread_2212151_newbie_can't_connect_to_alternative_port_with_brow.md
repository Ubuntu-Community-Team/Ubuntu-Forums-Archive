---
title: "newbie can't connect to alternative port with browser"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by Christopher_Henry on 2014-03-19
Hi all,

I am running the meteor nodejs framework. Starting my application with the command

meteor --port 25000

make my application available at [http://localhost:25000](http://localhost:25000)

However, I cannot connect to this port with my browser from another machine on the network, or another machine on the internet. 

My network administrator claims that my ip address is on a wide open subnet, meaning that all ports should be available to connections originating outside our network (we use this subnet for testing). 

Running netstat -anltp gives the following: 

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:25000           0.0.0.0:*               LISTEN      9415/node
tcp        0      0 127.0.0.1:25001         0.0.0.0:*               LISTEN      9437/mongod
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      929/mysqld
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      700/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      846/cupsd
tcp        0      0 0.0.0.0:20281           0.0.0.0:*               LISTEN      9458/node
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      8624/0
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN      8970/2
tcp        0    272 142.132.145.50:22       206.45.37.210:64732     ESTABLISHED 8525/sshd: christop
tcp        0      0 142.132.145.50:22       206.45.37.210:49419     ESTABLISHED 8848/sshd: 3909-001
tcp        0      0 142.132.145.50:22       206.45.233.108:51723    ESTABLISHED 8738/sshd: 3909-001
tcp        0      0 142.132.145.50:40682    107.21.116.12:443       TIME_WAIT   -
tcp6       0      0 :::8009                 :::*                    LISTEN      911/jsvc.exec
tcp6       0      0 :::80                   :::*                    LISTEN      911/jsvc.exec
tcp6       0      0 :::22                   :::*                    LISTEN      700/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      846/cupsd
tcp6       0      0 ::1:6010                :::*                    LISTEN      8624/0
tcp6       0      0 ::1:6011                :::*                    LISTEN      8970/2

```



In addition, I have tried  

sudo iptables -A INPUT -p tcp --dport 25000 -j ACCEPT 

with no luck. 

One piece of additional information. There is currently an apache-tomcat server running on this system, which is able to server pages to outside machines. 

Is there any other steps I need to do to open this port in order to be able to connect to this port with my browser? Or, is it time to ask my network administrator to double check that my machine is indeed open to the internet. 

Thank you

---

