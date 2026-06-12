---
title: "Transmission and UFW"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Marcelo Ramone on 2008-05-26
Hello.

In the Transmission preferences, I can see the port 51413 is closed.

From terminal I try to open the port with: 

> sudo ufw allow from 192.168.1.105 to any port 51413Now the program is still showing that port closed...

> marcelo@linux:~$ netstat -a | grep 51413
tcp        0      0 *:51413                 *:*                     LISTEN  
marcelo@linux:~$

---

### Post by Marcelo Ramone on 2008-05-26
apparently is a program error...

> Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-05-26 08:32 UYT
Interesting ports on localhost (127.0.0.1):
Not shown: 65535 closed ports
PORT      STATE SERVICE
51413/tcp open  unknown
Nmap done: 1 IP address (1 host up) scanned in 4.565 seconds


---

### Post by hmich176 on 2008-06-03
Any ideas on how to fix it?

---

### Post by stoffe on 2009-04-01
Old post, but it seems to be working in Jaunty, transmission sees the port as open.

---

### Post by crysys on 2009-05-08
Huh, not for me.  My port was open and working in Intrepid but since a clean install of Jaunty I could not get this port to register as open.

But Marcelos' ufw rule has opened it.  Now here is where it gets wierd.

> :~$ sudo ufw status
Status: inactive


ufw isn't even running but adding the rule managed to open the port just the same.  I don't pretend to understand the firewall but that just plain shouldn't work.  Or rather it should have worked all the time.

Update:  Now it reports a closed port once again.  This thing is screwy.

---

