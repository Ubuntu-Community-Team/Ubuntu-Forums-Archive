---
title: "Establish TCP/UDP Connection with Server via Terminal?"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by eulallia1 on 2008-10-19
Which command(s) may do this?

Thanks

---

### Post by puppywhacker on 2008-10-19
I often use telnet to check TCP connections

For instance by "localhost 80" and then giving "GET / HTTP/1.0" you can check if a webserver responds. UDP is more difficult so I usually make a little program (C/Java/Perl/Python) to send UDP packets.


client:/$ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
GET / HTTP/1.0

HTTP/1.1 200 OK

---

### Post by eulallia1 on 2008-10-21
> **puppywhacker said:**
> I often use telnet to check TCP connections

For instance by "localhost 80" and then giving "GET / HTTP/1.0" you can check if a webserver responds. UDP is more difficult so I usually make a little program (C/Java/Perl/Python) to send UDP packets.


client:/$ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
GET / HTTP/1.0

HTTP/1.1 200 OK

Thanks for your help, but the command supported both, and
when I use the command on Google, Google closes the connection, where on the command I used before it returned a 400 because of my ill formed request.

---

### Post by cariboo on 2008-10-22
Are you trying to access your server via a terminal, try ssh. You have to have openssh-server installed on the server then it is just a matter of opening a terminal and typing:

```
ssh user@server
```

Jim

---

