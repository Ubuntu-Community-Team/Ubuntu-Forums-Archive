---
title: "Can't SSH to server,  Connection reset by peer. Help!"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by freetree on 2008-07-17
One ubuntu 8.04 workstation and 8.04 serer. Have problem when ssh to server from workstation. SSH can login once every 4-10 times. But most times, just got 'Connection reset by peer' right after input the password. 

From the server side, auth.log showed connection is established. 

From workstation, can use wine to start ssh windows problem to login without problem. 

Seemed have no problem before certain upgrades in ubuntu. 

So the problem is most probably on the ssh client side. Any suggestions?

---

### Post by xingguard on 2008-07-30
I've been getting the same problems. I've filed a bug report

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/253471](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/253471)

---

