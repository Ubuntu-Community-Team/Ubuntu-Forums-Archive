---
title: "running apache"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by paul88 on 2010-07-14
I am trying to run apache and am getting the following message, what do I do?

```
paul@paul-laptop:~/httpd-2.2.8$ /home/paul/apache2/bin/apachectl start
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by Hanzerik on 2010-07-14
Port 80 requires higher privileges then a normal user has. Ports 1-1023 require root privileges to run services on.

If you are wanting to run Apache as a non-root user, then edit your apache config to have it run on say port 8080.

Or try starting it with sudo /home/paul/apache2/bin/apachectl start

Edit to Add: Did you compile apache yourself, or are you using something like XAMMP?

This is how I used to build Apache when I used to use apache as a web php interface for some game servers. I could just change the port and have multiple web servers running for different game servers.
```
./configure --prefix=$HOME/www --enable-so --with-port=8008
```

---

