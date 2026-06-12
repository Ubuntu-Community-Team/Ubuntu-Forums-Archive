---
title: "Installed Tinyproxy, but unable to locate it?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by jono2009 on 2009-03-02
I have tried to find an answer from a similar question from the forum, but no results. I'm using Ubuntu 8.10

I've installed Tinyproxy by the terminal, as show in the below copy, but I'm unable to locate it.
I've looked all though applications lists, systems/preferences and administrations lists,(synatic package manager shows it as installed, but no leads to where).

 

####-####-desktop:~$ sudo apt-get install tinyproxy
[sudo] password for ####: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tinyproxy
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 65.8kB of archives.
After this operation, 238kB of additional disk space will be used.
Get:1 [http://mirror.internode.on.net](http://mirror.internode.on.net) intrepid/universe tinyproxy 1.6.3-3 [65.8kB]
Fetched 65.8kB in 7s (8621B/s)                                                 
Selecting previously deselected package tinyproxy.
(Reading database ... 360373 files and directories currently installed.)
Unpacking tinyproxy (from .../tinyproxy_1.6.3-3_i386.deb) ...
Processing triggers for man-db ...
Setting up tinyproxy (1.6.3-3) ...
update-rc.d: warning: /etc/init.d/tinyproxy missing LSB style header
Starting tinyproxy: tinyproxy.

Thankyou for any help you can give me,(been a 56 year old noob, I need all the help I can get). :P:P:P

---

### Post by Sysero on 2009-03-03
Hey.

Open a terminal and type:

```
whereis tinyproxy
```

It should tell you where it's hiding.

---

### Post by jono2009 on 2009-03-03
> **Sysero said:**
> Hey.

Open a terminal and type:

```
whereis tinyproxy
```

It should tell you where it's hiding.


Yep, you have done it. Thanks for your help problem Solved.
:popcorn:

---

