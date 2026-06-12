---
title: "Running a program on startup: get &quot;TcpSocket.cpp:248: connect error [101]&quot;"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by jnoreiko on 2007-12-15
I need my system to start darkice, a streaming program when it's switched on -- without a user having to log in.

This guide suggests doing this by adding the command to /etc/rc.local

So I've done that.
But when I power up and log in, darkice isn't running.

The darkice log says:

```
DarkIce: TcpSocket.cpp:248: connect error [101]
```

What does this mean and what can I do about it?

---

### Post by jnoreiko on 2008-01-30
Just in case anyone else wants the answer: looks like it's a bug in darkice: [http://darkice.tyrell.hu/trac/ticket/19](http://darkice.tyrell.hu/trac/ticket/19)

---

