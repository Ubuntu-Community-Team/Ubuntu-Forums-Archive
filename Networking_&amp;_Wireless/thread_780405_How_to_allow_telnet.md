---
title: "How to allow telnet"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by moonhk on 2008-05-03
Hi All

How to allow telnet for my ubuntu ? I want windows can telnet my ubuntu.


moonhk@hex:~$ telnet 192.168.0.110
Trying 192.168.0.110...
telnet: Unable to connect to remote host: Connection refused
moonhk@hex:~$


moonhk@hex:~$ uname -a
Linux hex 2.6.15-51-server #1 SMP Tue Feb 12 17:12:18 UTC 2008 i686 GNU/Linux
moonhk@hex:~$

moonhk

---

### Post by jetsam on 2008-05-06
I think all you need to do is install the telnetd package, **but**...

Telnet is a very insecure protocol and almost no one uses it for its original purpose anymore.  Do not install it if you aren't behind a secure firewall and on a trusted network.  

A better, more secure choice is to install openssh-server and use putty from windows to access the linux box.  More details here:
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by moonhk on 2008-05-20
Thank. OK now.

---

