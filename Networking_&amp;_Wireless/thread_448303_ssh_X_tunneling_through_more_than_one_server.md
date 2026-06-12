---
title: "ssh X tunneling through more than one server"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by bierholen on 2007-05-19
Hi there,

I would like to remotely run an X application on my Ubuntu machine at home. The application is on a Unix server at work. I can easily access the Unix system by

ssh -X unix1.work

I can also run X applications from unix1 on my computer. My problem is that the application I want to use is on a different machine: unix2. I can log on to this machine with rlogin:

[bierholen@unix1 ~]$ rlogin unix2
[...]
unix2%

Running X applications from unix2 on my computer doesn't work:

unix2% xclock
Error: Can't open display:

That makes sense to me. My question now is if it is possible at all to run applications from unix2 on my computer. I can't connect directly to unix2. I always have to go via unix1. I played around quite a bit but I couldn't make it work.

Thanks for any help!

---

