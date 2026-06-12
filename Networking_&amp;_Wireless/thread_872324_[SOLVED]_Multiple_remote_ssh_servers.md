---
title: "[SOLVED] Multiple remote ssh servers"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by cravenc on 2008-07-27
Hello,

I'm setting up two Ubuntu servers for my church, a web and mail server.  I'd like to use SSH on the default port 22.  Is there a way to run two computers with ssh and access both remotely?  

I currently have port 22 forwarded to the web server.  

If I have to I can set one computer's ssh server to use a different port.

---

### Post by Rhubarb on 2008-07-27
If you can ssh to one computer (the web server), then you can ssh from the web server to the other email server.

To access your web server:
```
ssh username@webserverIPaddress
```

To access your email server:
```
ssh username@webserver_IP_address
ssh username@email_server_Internal_IP_address
```

So you can create an ssh tunnel within an ssh tunnel to reach your email server.

If you don't like this way, you can tell your router to translate a different port / tell ssh to use a different port, so you'd connect this way:
```
ssh username@email_server_IP_address:port_number
```

---

