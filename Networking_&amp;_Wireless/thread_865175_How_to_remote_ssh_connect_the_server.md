---
title: "How to remote ssh connect the server"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by satimis on 2008-07-20
Hi folks,


Server public IP - 220.232.xxx.xxx
Server internal IP (router IP) 192.168.0.52
Server hostname - satimis.com
domain - satimis.com
port 2222 already forward to 192.168.0.52


On Intranet
$ ssh -p2222 192.168.0.52

can ssh connect the server


What will be the correct command on Xterm to ssh connect the server on local machine via Internet ?


Tried follows without result;

$ ssh -p2222 satimis.com
$ ssh -p2222 220.232.xxx.xxx

just hanging without connected.  Please advise.  TIA


B.R.
satimis

---

### Post by PinkFloyd102489 on 2008-07-20
I dont quite understand what you're wanting, so I'll just go from here.


If you're wanting to access your server from outside your LAN, on a Linux machine, then entering "ssh -p2222 satimis.com" would be correct if you've already forwarded the port correctly.

Also check to make sure the username matches up and apply the correct switch if not. I think it's -l (as in lol) but I cant remember.

---

### Post by satimis on 2008-07-20
> **PinkFloyd102489 said:**
> I dont quite understand what you're wanting, so I'll just go from here.


If you're wanting to access your server from outside your LAN, on a Linux machine, then entering "ssh -p2222 satimis.com" would be correct if you've already forwarded the port correctly.

Also check to make sure the username matches up and apply the correct switch if not. I think it's -l (as in lol) but I cant remember.
Hi PinkFloyd102489,


Thanks for your advice.


This is a test. Recently I finish installing SugarCRM on this LAMP server. It can be connected on browser via Internet on a local PC in the same LAN


Connection:-
Server LAN IP 192.168.0.52
PC IP 192.168.0.10
on local PC browser run;
```
https://satimis.com/index.php
```


But on local PC Xterm the server can't be ssh connected via Internet.


If I can't test it in this way. I have only one public IP. What can I do? via a proxy server on Internet?


TIA


B.R.
satimis

---

