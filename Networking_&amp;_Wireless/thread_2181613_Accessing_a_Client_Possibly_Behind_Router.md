---
title: "Accessing a Client Possibly Behind Router"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by Dan Again on 2013-10-18
The short and sweet version of the question: how do server processes access client processes that may be behind a router?

The long version: Not an Ubuntu question, really...more of a general networking question, however, I haven't had much luck getting this question answered on StackOverflow or the StackExchange network engineering site. I'm trying to create toy UDP server/client programs for an undergraduate research project I am working on. I've got my server up and running on my Raspberry Pi, but I'm having trouble getting messages back to the client. Specifically...
[LIST=1]
[*]start server
[*]client sends message to server on accept socket
[*]server receives message, creates connection thread on new socket and sends ack back to client
[*]client never gets ack from server
[/LIST]
The client never receives the ack because it is sent to the client's public IP address, AKA the router. The router has no idea what to do with the message, so it just drops it. I feel like this probably isn't a novel problem and there has to be some sort of well-defined solution to it, I just don't know enough about networking to even know where to start. I'd like the solution to be a general one...that is, I'd like to figure out how to establish communication between a server and client regardless of whether or not the client is behind a router.

---

### Post by houstonbofh on 2013-10-18
What you need can be found here

[http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding)

and here

[http://portforward.com/english/routers/port_forwarding/](http://portforward.com/english/routers/port_forwarding/)

You need a path from the public IP of the router to the device behind it.

Now the problem is because the server is creating an entirely new connection, not just answering the request.  If you just answer the query, NAT takes care of it for you.  An example of this problem in the real world is here...

[http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html](http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html)

---

