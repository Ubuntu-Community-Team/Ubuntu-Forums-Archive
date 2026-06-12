---
title: "Nullmailer"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by mörgæs on 2010-10-18
A small question regarding Nullmailer. 


I am trying to send mail from a PHP script through Nullmailer, but it is not working. The machine is running a classic LAMP setup on Ubuntu 10.04.


**PHP:**
A simple script using the mail() function. While invoking, return code 1 indicates that everything is all right here.


**Nullmailer: **
The directory /etc/nullmailer/ contains two files: Adminaddr which is empty and remotes which contains only the line
postur.simnet.is smtp


When running, this is what I get in **syslog**:
Oct 18 19:54:09 sandkassi nullmailer[1054]: Trigger pulled.
Oct 18 19:54:09 sandkassi nullmailer[1054]: Rescanning queue.
Oct 18 19:54:09 sandkassi nullmailer[1054]: Starting delivery: protocol: smtp host: postur.simnet.is file: 1287431649.1999
Oct 18 19:54:09 sandkassi nullmailer[2000]: smtp: Succeeded: 250 2.0.0 Ok: queued as 3C1F02F434
Oct 18 19:54:09 sandkassi nullmailer[1054]: Sent file.
Oct 18 19:54:09 sandkassi nullmailer[1054]: Delivery complete, 0 message(s) remain.

It also seems to be fine, but when looking in my mailbox nothing is received. 


Does anyone have an idea as to what is wrong?

---

### Post by mörgæs on 2010-10-19
It just came to my mind: Could the problem be related to /etc/hosts? For now it only has two lines:

127.0.0.1    localhost
127.0.1.1    sandkassi

---

