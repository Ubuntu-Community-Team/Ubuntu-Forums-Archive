---
title: "how to open isql page?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by venkatesh_b87 on 2009-02-25
hi everybody, i have installed oracle in my ubuntu system. i have tried to connect to isql several times but could not connect to. someone please help me with the proper address which will lead me to isql page. please note that i have installed oracle with all default options, i mean that the port number will be the default provided by oracle.
thanks...

---

### Post by cmnorton on 2009-02-25
Not knowing the first thing about Oracle, I'll take a stab at it only because Informix has a product called isql. 

1) Is the oracle daemon running?

2) Is their a config file somewhere that defines how you connect to the Oracle server?

In Informix, it's $INFORMIXDIR/etc/hosts, and you provide the port and server names there, and then make sure /etc/services has that port defined.

Have a look for where Oracle's configuration is, and look there. Also, look in your logs under /var/log. There should be an Oracle daemon log there. That can tell you something.

---

### Post by venkatesh_b87 on 2009-02-25
no i am trying to connect isql from oracle and not informix.
am sorry i do not know to check whether daemon is running or not in ubuntu system.
i could not find any config file that defines what you have told me.

---

### Post by cmnorton on 2009-02-25
I understand you are using Oracle and not Informix. I am trying to find some common pieces to your problem.

It sounds like you need some Oracle documentation to find out the name of your daemon.

Then, you need to go to a command line (x-term), and enter

ps -ef | grep oracle-daemon-name.

Also, you're going to need some documentation for Oracle. Your config files could be under /etc.

Enter sudo find /etc -type f -name "*oracle*"

---

### Post by venkatesh_b87 on 2009-02-25
venkatesh@venkatesh-laptop:~$ ps -ef | grep oracle-daemon-name
1000      6173  6029  0 07:35 pts/0    00:00:00 grep oracle-daemon-name
venkatesh@venkatesh-laptop:~$ sudo find /etc -type f -name "*oracle*"
[sudo] password for venkatesh: 
/etc/init.d/oracle-xe
/etc/xdg/menus/oraclexe.menu
/etc/default/oracle-xe
venkatesh@venkatesh-laptop:~$

---

### Post by cmnorton on 2009-02-26
You supply oracle-daemon-name. This was to substitute for the name of your oracle daemon that you obtained from oracle or on-line documentation.

---

