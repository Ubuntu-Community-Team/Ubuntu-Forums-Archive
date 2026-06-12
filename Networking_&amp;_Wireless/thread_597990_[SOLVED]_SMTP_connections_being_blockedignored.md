---
title: "[SOLVED] SMTP connections being blocked/ignored"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by montgoss on 2007-10-30
My Ubuntu server is refusing SMTP connections.
```
$ telnet 192.168.2.16 25
Trying 192.168.2.16...
telnet: Unable to connect to remote host: Connection refused
```

On the server:
```
$ sudo netstat -na | grep ":25 "
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN 
```
```
$ iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

How do I unblock this port?

---

### Post by mpokrywka on 2007-10-31
Server is refusing conections because of this:
> **montgoss said:**
> 
```
$ sudo netstat -na | grep ":25 "
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN 
```

Listens only on loopback interface (127.0.0.1), and you are trying to connect on other interface...
You did not specify which SMTP server you are using, but try to find in manual (or using dpkg-reconfigure package, or /etc/default/some-config-file) how to specify which interfaces/addresses it should listen

---

### Post by montgoss on 2007-10-31
I figured it out.

I'm using sendmail.  I had to edit /etc/mail/sendmail.mc.  I changed the line that said ```
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, Addr=127.0.0.1')dnl
``` to ```
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission')dnl
```

Then ran: ```
su
m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
/etc/init.d/sendmail restart
```

Now it'll allow connections on port 25.  ```
$ sudo netstat -na | grep ":25 "
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN   
```

It still doesn't actually accept the email and route it  But that's a separate issue...

---

