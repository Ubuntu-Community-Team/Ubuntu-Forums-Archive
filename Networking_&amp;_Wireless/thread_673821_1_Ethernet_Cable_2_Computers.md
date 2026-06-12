---
title: "1 Ethernet Cable 2 Computers"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by bgissal on 2008-01-21
I have searched extensively how to do this, but I seem not to have the problems others are having. 

SITUATION:

-I have a crossover cable to link the two Ubuntu boxes both running 7.10.
-I have assigned both computers a static ip with different subnets. For one, I have 192.168.8.1 and for the other I have 192.168.8.2.

After I start up the SSH (by using $sudo /etc/init.d/ssh start), on which I have it installed on both and type the command: 

$scp filename username@192.168.8.1:~

on the donating computer (i.e., the computer sending the file), The command line prints:

ssh: connect to host 192.168.8.1 port 22: No route to host

Where can you suggest I look to solve this??

---

### Post by banewman on 2008-01-21
Is the ssh server installed on one comp?

---

