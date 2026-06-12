---
title: "How to setup a basic port tunnel on squid?"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by metalelf0 on 2007-05-12
Hi everybody!

I've a computer connected to a squid proxy server, and I'd love to be able to use some im protocols on this client. I need to tunnel the ports 5190 and 5222, but I don't know how to do that on the server. The IM application on the client is pidgin 2.0 so it has full support for http tunnels.
I tried adding this lines at the end of my server squid.conf:

```
acl aim port 5190
no_cache allow aim
http_access allow aim
acl gtalk port 5222
no_cache allow gtalk
http_access allow gtalk
```

But none of the port tunnels work. What could be wrong? How could I set this correctly?

Thank you very much!

Elf0

---

