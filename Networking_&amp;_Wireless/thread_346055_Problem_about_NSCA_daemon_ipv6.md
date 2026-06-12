---
title: "Problem about NSCA daemon /ipv6"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-01-25
Hey Forum. 

Have a little question: 
I have for some time now beeing using Nagios as supervision as the distributed system - but have an error I haven't seen before now: 
I have this in my syslog:
Jan 25 12:06:26 localhost nsca[4349]: Network server bind failure (98: Address already in use) 
Jan 25 12:06:26 localhost nsca[4350]: connect from ::ffff:192.168.1.1 (::ffff:192.168.1.1)
Jan 25 12:06:26 localhost nsca[4351]: Network server bind failure (98: Address already in use) 
Jan 25 12:06:26 localhost nsca[4352]: connect from ::ffff:192.168.1.1 (::ffff:192.168.1.1)
Jan 25 12:06:26 localhost nsca[4353]: Network server bind failure (98: Address already in use) 
Jan 25 12:06:27 localhost nsca[4354]: connect from ::ffff:192.168.1.1 (::ffff:192.168.1.1)
Jan 25 12:06:27 localhost nsca[4355]: Network server bind failure (98: Address already in use) 
Jan 25 12:06:27 localhost nsca[4356]: connect from ::ffff:192.168.1.1 (::ffff:192.168.1.1)
Jan 25 12:06:27 localhost nsca[4357]: Network server bind failure (98: Address already in use) 
Jan 25 12:06:28 localhost inetd[4027]: nsca/tcp server failing (looping), service terminated

Then the Daemon is stopped - and it does this little trick each time after restart
 netstat -tan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2500            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:199             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp6       0      0 :::5667                 :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 :::25                   :::*                    LISTEN     
tcp6       0     0 ::ffff:192.168.1.30:22 ::ffff:192.168.1.135:2558 ESTABLISHED


And after 1-2minuts:
 netstat -tan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2500            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:199             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 :::25                   :::*                    LISTEN     
tcp6       1    0 ::ffff:192.168.1.30:5667 ::ffff:192.168.1.1:34349 CLOSE_WAIT 
tcp6       0     0 ::ffff:192.168.1.30:22 ::ffff:192.168.1.135:2558 ESTABLISHED

But where to define what to be using - ipv4 / ipv6 ??? What should I do here - never been messing around with these problems before 


Thanks

---

