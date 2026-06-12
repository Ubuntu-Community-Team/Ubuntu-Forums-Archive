---
title: "Server rejecting connections from remote machines"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by Rob_H on 2007-01-08
Hi,

I'm trying to run JBoss as a non-root user in order to debug a Java application. The server starts up fine and binds to the correct port (8345), and I can make connections to it from a browser running on the same machine. But as soon as I try to connect from a different machine on the same network, the connection is refused. The **netstat** command produces the following output, which confirms that the server is listening on port 8345:

```

sudo netstat -lp | grep 8345
tcp6       0      0 localhost:8345          *:*                     LISTEN     18215/java
```

If I sniff the traffic between the two boxes, I see a TCP SYN packet coming to port 8345 from the client. Then the server sends back a RST/ACK and nothing else.

The same exact JBoss configuration works fine on a Fedora box, which leads me to believe there's something different about how Ubuntu is configured for networking out of the box. For starters, does the "tcp6" mean that it'll only accept connections over IPv6? Does the fact that the user is non-root affect anything? There is no firewall between the client and server, and iptables are empty. I'm running out of ideas.

Any help greatly appreciated! Thanks!

---

### Post by Rob_H on 2007-01-08
Some more info: Even running a browser on the same box, it looks like I can only connect to the server process if I specify "localhost" as the host name. If I use the machine's network IP address, the connection is refused. So it looks like either JBoss is binding to the wrong interface or there is some kind of privilege problem. Any way to check?

---

### Post by Rob_H on 2007-01-09
SOLVED - JBoss was binding to the loopback interface. Apparently, it does a lookup by host name to get the local IP address and then tries to bind to that interface. Unfortunately, it looks like Ubuntu has a default entry in **/etc/hosts** that maps the host name to the loopback address. Removing that entry fixed the problem.

---

