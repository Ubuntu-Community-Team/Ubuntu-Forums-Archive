---
title: "Server Stuff"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by cody1233 on 2013-09-11
Hello again everybody!

I am trying to set up a web/samba/ssh server on a wired connection at my school.  I have installed all of the software and the configuration files are the default (except for the samba config file...I edited it to allow guest access and to set up the directories it shares).  I am trying to access it on a laptop that is wireless and is on a different subnet.  I tried the local and public IP addresses on all of the servers and none of them worked.  The IP address for the laptop is 10.80.209.232 and the (local) address for the server is 10.201.20.236.

Any suggestions??  Maybe is another subnet unreachable??

---

### Post by TheFu on 2013-09-12
This is a routing question. Might not be anything you can do about this.  Can you ping between them?  Traceroute?  Check in both directions.  Samba will probably be blocked - I hope it is. 

You might have to talk to the network admins to resolve this.

---

### Post by cody1233 on 2013-09-12
There's no ping or portscan.  That's what I was afraid of...Thanks though!!!

---

