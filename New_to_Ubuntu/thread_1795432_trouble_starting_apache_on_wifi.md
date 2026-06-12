---
title: "trouble starting apache on wifi"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by arewenotmen1983 on 2011-07-02
Dear Forums,

I have a very nice neighbor who lets me use his wifi for my internet access.  I'm also trying to learn perl cgi scripting, and got apache2 to test my scripts.  I bound apache to 127.0.0.1:80 with listen, and I still can't start apache.  I get this:

httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

What do?  Help me Ubuntu Forums, you're my only hope.

---

### Post by mikenev on 2011-07-02
Just to verify - you are running the apache restart as root using sudo, right? You can't run on port 80 or write to the apache logs as your regular user and it looks like you're getting errors related to that.

---

