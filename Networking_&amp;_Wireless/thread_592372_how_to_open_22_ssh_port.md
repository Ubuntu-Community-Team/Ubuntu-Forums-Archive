---
title: "how to open 22 ssh port"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by Mr.nano on 2007-10-26
ok here is the deal:
I tried to ssh to my computer at home but when i typed:
```

nmap localhost -p 22
```

i get this:

```
PORT   STATE  SERVICE
22/tcp closed ssh
```

As I said I want to connect to my home computer which has ssh server installed and listening on 22 port. Could I just open on this pc temporary 22 port to establish the connection and close it afterwards?

I read somewhere that I should install ssh server on this computer too, but i dont want to, I just want to use it as a client.

So how can i do that thing?

---

### Post by jfordwashere on 2007-10-26
You don't need to open port 22 if you are only ssh'ing out of the box.

---

