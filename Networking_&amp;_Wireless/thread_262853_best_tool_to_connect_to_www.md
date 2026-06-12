---
title: "best tool to connect to www"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by carteris21 on 2006-09-22
Hi,
   may someone recommend a Telnet tutorial, or other tool to connect to server in 80 port (www)(not a web browser) and it's tutorial.

---

### Post by p.i.m.p on 2006-09-22
:confused: if ure running a webserver, then wouldnt opening that port open up a webpage? if u mean something to connect to it from the console, try elinks, a console based web browser

---

### Post by kidders on 2006-09-22
Hi there,

I can't imagine why you'd want to chat with a web server over telnet ... maybe you're just curious, or trying to debug something?

Anyhow, any telnet client will do the trick. Send it something like this:

```

GET / HTTP/1.0
Host: www.whatever.com
<blank line here>

```

The server should respond in some fashion. To do anything more ... well ... interesting, you'd need to know a little about how the HTTP protocol works.

Any help?

---

### Post by carteris21 on 2006-09-23
OK, now i'm learning HTTP protocol.

---

