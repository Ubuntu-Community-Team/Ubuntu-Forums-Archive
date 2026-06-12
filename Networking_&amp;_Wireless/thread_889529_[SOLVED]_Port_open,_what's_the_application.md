---
title: "[SOLVED] Port open, what's the application?"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by borobudur on 2008-08-14
Hi, if I do a port scan I see one port open which I don't know what it is (port 7547). How can I find out what that is?

---

### Post by brian_p on 2008-08-14
> **borobudur said:**
> Hi, if I do a port scan I see one port open which I don't know what it is (port 7547). How can I find out what that is?

```
sudo lsof -i :7547
```

---

### Post by borobudur on 2008-08-14
Thanks but if I do that ***lsof*** gives no output. Nothing!?

---

### Post by tribaal on 2008-08-14
You can also use
```
sudo netstat -tunap
```
This should list all open ports, and state what application is listening on it (last column).
You can run it without sudo, but than you might miss processes ran with root privileges.

Hope this helps!

- Trib'

---

### Post by borobudur on 2008-08-14
Thanks Tribaal! Now as I run this command it seems that this port is not open anymore :-|

What could that have been?

---

### Post by brian_p on 2008-08-14
> **borobudur said:**
> Thanks but if I do that ***lsof*** gives no output. Nothing!?

My conclusion would be that there is no service on that port. What does the netstat command give?

---

### Post by borobudur on 2008-08-14
```
user@machine:~$ sudo netstat -tunap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      8026/dovecot    
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      8026/dovecot    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4538/mysqld     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      8026/dovecot    
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      8026/dovecot    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      10447/apache2   
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      4868/exim4      
tcp        0      0 0.0.0.0:636             0.0.0.0:*               LISTEN      12060/slapd     
tcp6       0      0 :::22                   :::*                    LISTEN      4440/sshd       
tcp6       0      0 :::636                  :::*                    LISTEN      12060/slapd     
tcp6       0      0 85.5.x.x:x              192.168.1.x:47232       ESTABLISHED 13158/sshd: user
udp        0      0 0.0.0.0:68              0.0.0.0:*                           5915/dhclient   
```

---

### Post by brian_p on 2008-08-14
> **borobudur said:**
> 

What could that have been?

Something you had running at the time but have since stopped.

As a matter of interest the netstat output shows no printing system on the machine. That's by design I expect.

---

### Post by borobudur on 2008-08-15
It's just a server for the web. It has no intranet purpose. 
Thanks!

---

