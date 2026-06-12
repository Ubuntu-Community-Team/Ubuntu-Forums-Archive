---
title: "How can I get a list of connections to a given port?"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Growbag on 2008-05-28
I run a server that offers connections over port 27960, is there a way of getting a count of connections to this port, and also a list of connected IPs?

I think maybe that the initial communication port is 27960, but then the actual connections are made on another port, I'm not too sure.

The server is the game "Enemy Territory" if that helps.

Thanks.

---

### Post by Monicker on 2008-05-28
From a terminal session:
```
netstat -anultp |grep 27960
```

If its a udp port, that probably won't help much, since udp is connectionless.  In that case you should use wireshark or tcpdump to see the connections as they occur.

---

