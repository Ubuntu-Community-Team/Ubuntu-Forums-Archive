---
title: "failed to restart apache2 in ubuntu 11.04"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by vineeth v s on 2011-08-28
hi,

 when i try to restart apache2 , shows error msg,bt can't find error in log.pls help

> 
vineeth@vineeth-Inspiron-N5010:~$ sudo /etc/init.d/apache2 restart 
 * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.                                                                         [fail]




---

### Post by wojox on 2011-08-28
What does this say:

```
netstat -A inet -lnp
```

---

### Post by vineeth v s on 2011-08-31
vineeth@vineeth-Inspiron-N5010:~$ netstat -A inet -lnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:59885           0.0.0.0:*                           -

---

### Post by divyabdasar on 2011-11-06
When i try to restart apache2 in my ubuntu 11.04 i get following error

i tired to enable virtual hosts for my projects, after enabling the hosts, when i try to restart apache2 i get this error. 

divya@divya-Inspiron-1545:~$ sudo service apache2 restart
[sudo] password for divya: 
 * Restarting web server apache2                                                                                                                                        Action 'start' failed.
The Apache error log may have more information.

divya@divya-Inspiron-1545:/etc$ netstat -A inet -lnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
udp        0      0 0.0.0.0:48171           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           - 

if any solutions please let me know...

---

