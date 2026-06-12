---
title: "How to see the IP addresses of currently opened pages"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by Mr.nano on 2007-10-31
What I want to do is to see the IP addresses of the web-pages I am looking at. Could somebody tell how to do that?

---

### Post by jfordwashere on 2007-10-31
Try "netstat -an" at an open terminal.

---

### Post by jfordwashere on 2007-10-31
Oh yeah btw, that will show all open sockets on the system, not just the sockets of webpages.

---

### Post by Mr.nano on 2007-10-31
Ok but as I saw the output I recalled that I forgot to mention that I have proxy server and all I am getting is:

tcp        0      0 192.168.0.124:39259     192.168.0.2:8080        ESTABLISHED

where the 192.168.0.2 is the proxy and the 8080 is the port. So is there a way to see the real ip addresses of the pages I open?

ps: I tried to ssh to the proxy server and see what's going on from there but but it has a password which i don't know

---

### Post by jfordwashere on 2007-10-31
Hmm, sorry I don't know then. If you want to find the IP of a particular host, though you can always run nslookup on the hostname.

---

